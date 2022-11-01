
### 半角のアットマーク（@）を使う

- MarkdownからHTMLへの変換時に@が入っていると以下のようになる

```
// foo.md
@マーク

// foo.html
<span class="citation" data-cites="マーク">@マーク</span>
```

- `\` でアットマークをエスケープすると不要なspanタグがなくなる
  - たぶん[このへん](https://pandoc-doc-ja.readthedocs.io/ja/latest/users-guide.html#citation-syntax)の引用がらみの機能
