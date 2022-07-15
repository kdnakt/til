
### 返り値のないメソッドのモック

```kotlin
val mockedFile = mockk<File>()

every { mockedFile.write(any()) } returns Unit
```

- https://notwoods.github.io/mockk-guidebook/docs/mockito-migrate/void/

