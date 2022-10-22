
### M1 Macでのspotbugsビルドエラー回避

- こちらの[issue](https://github.com/spotbugs/spotbugs/issues/2065)に記載の通り、以下のビルドコマンドで回避可能
- `./gradlew clean build -x :eclipsePlugin:compileJava -x :eclipsePlugin-junit:compileTestJava -x :eclipsePlugin-test:compileJava -x :eclipsePlugin-test:checkstyleMain`
  - -xはタスクを除外するオプション（[参考](https://docs.gradle.org/current/userguide/command_line_interface.html#sec:command_line_executing_tasks)）
