
### 文字列配列カラムとPgArrayのバグ

- `varchar(100)[]` とか `text[]` みたいなカラムをJVMの `Array<String>` 型に変換できる
  - hibernateの[StringArrrayType](https://github.com/vladmihalcea/hibernate-types/blob/master/hibernate-types-4/src/main/java/com/vladmihalcea/hibernate/type/array/StringArrayType.java)を利用
- 文字列に全角スペースが含まれていると `Array<String>` に変換した際に全角スペースが消えてしまう問題があった
  - 他の空白文字が含まれていない場合
  - かつ、org.postgresql:postgresqlの42.2.15以前を利用している場合
- [このコミット](https://github.com/pgjdbc/pgjdbc/commit/e8923c71597f844f07ef1b123d704d0a3b332a38)で修正されている

```diff
-        } else if (!insideString && Character.isWhitespace(chars[i])) {
+        } else if (!insideString && Parser.isArrayWhiteSpace(chars[i])) {
          // white space
          continue;
```

```
  public static boolean isArrayWhiteSpace(char c) {
    return c == ' ' || c == '\t' || c == '\n' || c == '\r' || c == '\f' || c == 0x0B;
  }
```
