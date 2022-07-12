
### IDS04-J. ZipInputStream からファイルを安全に展開する

- zip アーカイブ内の各エントリについて、展開を行う前にファイル名を検証
  - ファイル名が不正なものであった場合には展開処理全体を中止
  - ファイル名が不正なものだけ展開をスキップする、あるいは安全な場所に展開するでも可
- zip アーカイブ内の各エントリについて、展開後のサイズを確認
  - サイズが大き過ぎる場合には例外をスロー
  - zip アーカイブに含まれるファイルサイズは信頼できないため、ZipEntry.getSize() メソッドは使っていない
- zip アーカイブに含まれるエントリ数もチェック
  - その数が1024を超える場合には例外をスロー
- https://www.jpcert.or.jp/java-rules/ids04-j.html

```java
static final int BUFFER = 512;
static final long TOOBIG = 0x6400000; // ファイルサイズの上限, 100MB
static final int TOOMANY = 1024;      // エントリ数の上限
// ...

private String validateFilename(String filename, String intendedDir)
      throws java.io.IOException {
  File f = new File(filename);
  String canonicalPath = f.getCanonicalPath(); 

  File iD = new File(intendedDir);
  String canonicalID = iD.getCanonicalPath();
  
  if (canonicalPath.startsWith(canonicalID)) {
    return canonicalPath;
  } else {
    throw new IllegalStateException("File is outside extraction target directory.");
  }
}

public final void unzip(String filename) throws java.io.IOException {
  FileInputStream fis = new FileInputStream(filename);
  ZipInputStream zis = new ZipInputStream(new BufferedInputStream(fis));
  ZipEntry entry;
  int entries = 0;
  long total = 0;
  try {
    while ((entry = zis.getNextEntry()) != null) {
      System.out.println("Extracting: " + entry);
      int count;
      byte data[] = new byte[BUFFER];
      // ファイル名が不正でないこととファイルサイズが大き過ぎないことを
      // 確認してファイルをディスクに書き出す
      String name = validateFilename(entry.getName(), ".");
      if (entry.isDirectory()) {
        System.out.println("Creating directory " + name);
        new File(name).mkdir();
        continue;
      }
      FileOutputStream fos = new FileOutputStream(name);
      BufferedOutputStream dest = new BufferedOutputStream(fos, BUFFER);
      while (total + BUFFER <= TOOBIG && (count = zis.read(data, 0, BUFFER)) != -1) {
        dest.write(data, 0, count);
        total += count;
      }
      dest.flush();
      dest.close();
      zis.closeEntry();
      entries++;
      if (entries > TOOMANY) {
        throw new IllegalStateException("Too many files to unzip.");
      }
      if (total + BUFFER > TOOBIG) {
        throw new IllegalStateException("File being unzipped is too big.");
      }
    }
  } finally {
    zis.close();
  }
}
```
