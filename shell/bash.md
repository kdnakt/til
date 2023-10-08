
### seq

- https://linuxhint.com/bash_range/

```
for i in $(seq 10)
do
  echo $i
done
```

### 配列をハードコードする

```
week=(Sun Mon Tues Wed Thur Fri Sat)
echo ${week[0]}
// Sun
```

### フォルダ内のファイルを作成日時でリネームする

- 以下は.movファイルの例

```
$ ls | xargs -I {} bash -c 'mv "$1" $(GetFileInfo -d "$1" | sed "s#^\(..\)/\(..\)/\(....\) \(..\):\(..\):\(..\)#\3\1\2-\4\5\6#").mov' - {}
```

- 参考
  - https://stackoverflow.com/questions/39479151/how-to-use-xargs-to-replace-2-arguments
  - https://stackoverflow.com/questions/34123076/osx-how-to-get-the-creation-modification-time-of-a-file-from-the-command-lin
