
### スキーマ関連コマンド

- スキーマ一覧を表示する
  - ¥dn
  - ¥dn+ （アクセス権も表示する）

- 現在のスキーマを表示する
  - select current_schema();

- スキーマを変更する
  - SET search_path = my_schema;

### テーブル関連コマンド

- テーブル一覧を表示する
  - ¥dt
  - ¥dt+ （サイズも表示する）

- カラム情報を出力する
  - ¥d テーブル名称

### ビュー関連コマンド

- ビュー一覧を表示する
  - ¥dv
  - ¥dv+ （サイズも表示する）

### マテリアライズドビュー関連

- CREATE MATERIALIZED VIEW table_name AS query
  - queryのところに `SELECT column_name FROM other_table_name` みたいに書く
  - v12だと自動更新はない
    - REFRESH MATERIALIZED VIEWコマンドで更新
    - CONCURRENTLYをつけるとSELECTをロックしない、ただしデータがない初回はエラーになる
  - https://www.postgresql.jp/document/12/html/sql-creatematerializedview.html
