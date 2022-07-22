
### 例外を投げるプロパティ

- java.io.File#isFileはKotlin上ではメソッドでなくプロパティに見える
  - [参考](https://codechacha.com/ja/kotlin-file-exists/)
- Java上ではisFile()というメソッド
  - SecurityExceptionを投げる
- https://docs.oracle.com/javase/jp/8/docs/api/java/io/File.html#isFile--
- File#canWrite()などはKotlin上でもメソッド。違いは？
