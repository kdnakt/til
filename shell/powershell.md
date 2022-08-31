
### Powershellでエイリアスを使う

- http://www.vwnet.jp/windows/PowerShell/2020100601/PsAlias.htm
- まずスクリプトの実行を許可する
  - if((Get-ExecutionPolicy -Scope LocalMachine) -ne "RemoteSigned"){Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force}
- $PROFILEのファイルを作成してエイリアスを登録する
  - Set-Alias wget Invoke-WebRequest

### サブコマンドを含めたエイリアスを使う

- https://docs.microsoft.com/ja-jp/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-7.2
- functionを定義してエイリアスにするとよい

```
function GitStatus { git status }
set-alias s GitStatus
```
