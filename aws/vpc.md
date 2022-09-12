
### Private DNS

- https://qiita.com/sasakiki/items/ad6498c921128ee4faee
- VPCを作成する
- 上記VPCを指定してRoute53プライベートホストゾーンを作る
  - Aレコードで解決したいドメイン名とIPを登録する
- DHCPオプションセット新規作成
  - ドメイン名：解決したいドメイン名＋ap-northeast-1.compute.internal（半角スペースで区切る）
  - ドメインネームサーバー：AmazonProvidedDNS
- 上記VPCのDHCPオプションセットを上で作成したものに変更
- Lambda関数にこのVPCを設定することでLambda関数内での名前解決結果を固定できる
