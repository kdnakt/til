
### strcmp

- 配列を渡すとNULLを返す
  - リクエストを改竄して、 `password=admin` となっている辺りを `password[]=%22%22` とすると空の配列になる
- NULLと0の比較はtrueになる
- https://www.doyler.net/security-not-included/bypassing-php-strcmp-abctf2016

