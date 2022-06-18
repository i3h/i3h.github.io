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

解析思路：

1. `boxed_num` 类型是 `Box`
2. `add_one` 传入参数类型是 `&mut Box`
3. 在函数 `add_one` 内部，`*num` 类型是 `Box`。
4. `*num.as_mut()` 是 `Box` 内部变量 `0` 的 mutable ref `&mut 0`。

#### AsMut 的实现

```
#[stable(since = "1.5.0", feature = "smart_ptr_as_ref")]
impl<T: ?Sized, A: Allocator> AsMut<T> for Box<T, A> {
    fn as_mut(&mut self) -> &mut T {
        &mut **self
    }
}
```

解析思路：

1. 函数 `as_mut` 传入参数是 `&mut Box`
2. `*self` 类型是 `Box`
3. `**self` 类型是 `Box` 内部数据 `T`

#### **参考资料**

1. <https://doc.rust-lang.org/std/convert/trait.AsMut.html>
2. <https://doc.rust-lang.org/src/alloc/boxed.rs.html#1931-1936>
