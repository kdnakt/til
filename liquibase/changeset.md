
### ビューの作成時にスキーマを指定する

- https://docs.liquibase.com/change-types/create-view.html
- schemaNameでスキーマ名を指定しない場合、SQLの中で指定する
  - 実行時の引数などでdefaultSchemaNameを指定しておく
    - https://www.liquibase.com/blog/liquibase-environment-variables-control-deployments
  - SQLはこんな感じ
    - INSERT INTO ${database.defaultSchemaName}.my_table (my_column) VALUES ...
  - 指定しない場合「リレーションが見つからない」エラーとなる（PostgreSQLの場合
 
 
