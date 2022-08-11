
### Powershellでエイリアスを使う

- http://www.vwnet.jp/windows/PowerShell/2020100601/PsAlias.htm
- まずスクリプトの実行を許可する
  - if((Get-ExecutionPolicy -Scope LocalMachine) -ne "RemoteSigned"){Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force}
- $PROFILEのファイルを作成してエイリアスを登録する
  - Set-Alias wget Invoke-WebRequest
