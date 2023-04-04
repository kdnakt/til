
### -Iオプションで置換する

- -Iオプションで渡した文字列を置換してコマンドが実行される

```
$ ls
aaa
bbb
ccc

$ ls | xargs -Idirname echo dirname/foo.txt`
aaa/foo.txt
bbb/foo.txt
ccc/foo.txt
``` 
