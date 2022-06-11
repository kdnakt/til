
### QPACK

- リクエストのuser-agentヘッダや、レスポンスの特定のヘッダなど、あまり変わらないものを圧縮するための仕組みforHTTP/3
  - ハフマン符号と静的テーブル、動的テーブルを使う
  - 元になったのはSPDYのDeflate圧縮やHTTP/2のHPACK
- 解説
  - https://asnokaze.hatenablog.com/entry/2019/04/08/020017
  - https://github.com/flano-yuki/http3-note/blob/master/http3-note_3.pdf
- RFC 9204
  - https://datatracker.ietf.org/doc/html/rfc9204
