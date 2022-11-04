
### JEP 425: Virtual Threads (Preview)

- Java 19でプレビュー
  - 利用する場合`--enable-preview`オプションをつけてJVMを起動する必要あり
- https://openjdk.org/jeps/425
- https://quarkus.io/guides/virtual-threads

```java
// OSスレッド1万件だとクラッシュするOSもあるが仮想スレッドなら少ないOSスレッドで処理可能
try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
    IntStream.range(0, 10_000).forEach(i -> {
        executor.submit(() -> {
            Thread.sleep(Duration.ofSeconds(1));
            return i;
        });
    });
}  // executor.close() is called implicitly, and waits
```
