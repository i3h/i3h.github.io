---
layout: post
title: "Rust AsMut"
date: 2022-06-18 17:30
---

#### 定义

`AsMut` 是一个 mut-to-mut ref trait，它可以帮助获取 struct inner type 的 ref。

```
pub trait AsMut<T> 
where
    T: ?Sized, 
{
    fn as_mut(&mut self) -> &mut T;
}
```

#### 例子

```
fn add_one<T: AsMut<u64>>(num: &mut T) {
    *num.as_mut() += 1;
}

let mut boxed_num = Box::new(0);
add_one(&mut boxed_num);
assert_eq!(*boxed_num, 1);
```

#### **参考资料**

1. <https://doc.rust-lang.org/std/convert/trait.AsMut.html>
2. <https://doc.rust-lang.org/src/alloc/boxed.rs.html#1931-1936>
