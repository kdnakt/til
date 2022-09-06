
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

### UUID生成

- https://torutk.hatenablog.jp/entry/20160519/p1

```
PS D:\> [Guid]::NewGuid()

Guid
----
95997df5-edae-430e-9f65-f0784e1e62c6

PS D:\>
```

### プロファイルをリロードする

- `& $PROFILE`
- https://devblogs.microsoft.com/scripting/powertip-reload-your-powershell-profile/
