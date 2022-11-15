
### Major Versionup

- AllowMajorVersionUpgradeはメジャーバージョンアップする時だけtrueになってれば良さそう
- https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-properties-rds-database-instance.html#cfn-rds-dbinstance-allowmajorversionupgrade
- https://dev.classmethod.jp/articles/upgrade-amazon-rds-using-aws-cloudformation/

### RDS Proxyピンニング：RDS PostgreSQL編

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-proxy-managing.html#rds-proxy-pinning
- 変数をSETするとピンニングが発生する
- プロキシターゲットグループ
  - セッション固定フィルタ：PostgreSQLではサポートなし
  - 初期化クエリ：PostgreSQLではサポートなし
- 拡張クエリプロトコルをJDBCデフォルト設定で利用するとピンニングが発生
- テンポラリテーブルやシーケンスを作成するとピンニングが発生

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-proxy-setup.html#rds-proxy-connecting-postgresql
- 以下のパラメータを追加するとピン止め回避できる
  - assumeMinServerVersion 
  - ApplicationName 
  - preferQueryMode 
