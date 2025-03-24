# Common Traits

Let's briefly explore some standard library traits to understand their practical
use.

- Clone
- Copy
- Display
- Debug
- Default
- Eq and PartialEq
- Ord and PartialOrd
- Iterator
- IntoIterator
- From/Into

These traits enable a rich set of tools that work seamlessly across many types.
Let’s look at a few examples to illustrate their usefulness.

## Debug

Sometimes, especially when troubleshooting, we want to quickly inspect the
contents of a variable, such as the `origin` instance of `Point` below.

```rust,does_not_compile
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let origin = Point { x: 0, y: 0 };
    println!("{:?}", origin); // not work
}
```

The `Debug` trait enables this by allowing types to be
printed using the `{:?}` formatter in macros like `println!`.


