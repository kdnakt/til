
### Sender Policy Framework (SPF)の制限

- [RFC4408](https://datatracker.ietf.org/doc/html/rfc4408#section-10.1)
- DNSルックアップを伴うmechanisms and modifiersの使用は1回のSPFチェックにつき10回まで
  - mechanisms:  include / A / MX / PTR / exists 
  - modifiers: redirect
