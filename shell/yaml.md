
### コロンをyamlでエスケープする

- 以下のStackoverFlowを参考に解決した
  - https://stackoverflow.com/questions/14873227/escaping-colons-in-yaml

```
# NG
- sed -i -e 's/foo:/bar:/g' baz.txt

# OK
- |-
  sed -i -e 's/foo:/bar:/g' baz.txt
```

- 参考：https://qiita.com/jerrywdlee/items/d5d31c10617ec7342d56
