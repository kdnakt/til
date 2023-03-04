
### console.time()で経過時間を記録する

- https://github.com/n8tz/CVE-2022-24999/blob/master/express-qs-string-bomb/poc.js

```
// タイマーを登録
console.time('timerA')
// 何も出力されない

doSomething()

// タイマーの途中経過を出力する
console.timeLog('timerA')
// 出力例）
// timerA: 463.177734375 ms

doSomething()

// タイマーを終了する
console.timeEnd('timerA')
// 出力例）
// timerA: 20463.177734375 ms
```
