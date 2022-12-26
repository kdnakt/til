
### &Rc<RefCell<T>> -> Rc<RefCell<T>>

- [LeetCode](https://leetcode.com/problems/merge-two-binary-trees/)とかで出てくるやつ

```
val node: Option<&Rc<RefCell<TreeNode>>>

val node2: Option<Rc<RefCell<TreeNode>>> = node.map(|n| Rc::clone(n));
```

- 参考:[RustでRc<RefCell<T>>する](https://qiita.com/komasayuki/items/c63887103f5039f8279f)
