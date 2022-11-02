
### jsonインポートはバリデーションが効かない

- json形式でレルムにユーザーをインポートできる
- ただし、required_actionsに設定する文字列はバリデーションが効かない
　　- 未登録のアクションでもインポートできてしまう
　　- 未登録のアクションの場合、ユーザーの詳細画面ではアクションが表示されない
  - ただしDBには登録されているのでAPIレスポンスには含まれている
　　-　該当ユーザーがログインすると、ログにエラーメッセージが出力される
  -　[RealmAdapter.java](https://github.com/keycloak/keycloak/blob/af3b573d196af882dfb25cdccb98361746e85481/model/jpa/src/main/java/org/keycloak/models/jpa/RealmAdapter.java#L1890)　
 
