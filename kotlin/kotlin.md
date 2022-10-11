
### 例外を投げるプロパティ

- java.io.File#isFileはKotlin上ではメソッドでなくプロパティに見える
  - [参考](https://codechacha.com/ja/kotlin-file-exists/)
- Java上ではisFile()というメソッド
  - SecurityExceptionを投げる
- https://docs.oracle.com/javase/jp/8/docs/api/java/io/File.html#isFile--
- File#canWrite()などはKotlin上でもメソッド。違いは？

### try-with-resource in Kotlin

- 拡張関数use()を使うと同じ効果
- https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/use.html
