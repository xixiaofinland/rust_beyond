# Introduction

Hi there, I'm [Xi Xiao](http://xixiao.info). This is my journey learning
[Rust][r].

I created this book for three reasons.

First, I want to become a better writer. Books, like [Flowers for Algernon][ffa]
and [The Phoenix Project][tpp] amazed me. They explain complex ideas through
simple words that still hit hard. They prove we don't need fancy language to
convey thoughts.

This skill seems magical to me! We often hear that things must be complex to be
powerful. But these books are both simple AND powerful. I'm writing this book to
practice this rare combination.

Second, I love Rust. The language gives you modern features like type inference
and safe concurrency that make coding pleasant. But it also offers the low-level
control needed for system programming. Powerful yet approachable - just like the
writing style I admire.

Third, Rust isn't like other languages I've learned. It's complex enough to be
worth breaking down into bite-sized pieces. By sharing my journey, I hope to
make it more accessible for you too.

## How to read

I've organized related concpets together, but it shouldn't puzzle you much if
you jump around and focus on whatever interests you most.

I love reading with a dark color theme. You can change themes by clicking the
paint brush icon (<i class="fa fa-paint-brush"></i>) in the top-left menu bar.

Need to find something specific? Press the search icon (<i class="fa
fa-search"></i>) or hit the `S` key on the keyboard to open an input box. As you
type, matching content appears instantly.

## Code blocks

Code blocks may contain icons for interacting purpose:

| Icon | Description |
|------|-------------|
 <i class="fa fa-copy"></i> | Copy the code|
| <i class="fa fa-play"></i> | Execute and display the output |
| <i class="fa fa-eye"></i> | Toggle visibility of hidden lines |
| <i class="fa fa-history"></i> | For editable code blocks, this undos changes you have made |

<br/>
<br/>
Here are examples.

1. A block that you can copy the code, or execute and see the output:

```rust
fn main() {
    println!("Hello, I'm the non-editable code block!");
}
```

2. A code block that you can also edit and undo:

```rust, editable
fn main() {
    println!("Click on me and edit!");
}
```
3. A code block with a hidden line:

```rust
fn main() {
    println!("I have a hidden line, find it out!");
    # // a hidden comment line here
}
```
<br/>

<span id="ferris"></span>

In the sample code, Ferris will also help you distinguish code with different
context:

| Ferris                                                                                                           | Meaning                                          |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| <img src="img/ferris/does_not_compile.svg" class="ferris-explain" alt="Ferris with a question mark"/>            | This code does not compile!                      |
| <img src="img/ferris/panics.svg" class="ferris-explain" alt="Ferris throwing up their hands"/>                   | This code panics!                                |
| <img src="img/ferris/not_desired_behavior.svg" class="ferris-explain" alt="Ferris with one claw up, shrugging"/> | This code does not produce the desired behavior. |

## Source Code

The source files from which this book is generated can be found on
[GitHub][book].

[book]: https://github.com/xixiaofinland/rust_beyond

That said, let's get on with it!

[r]: https://www.rust-lang.org/
[ffa]: https://www.amazon.com/Flowers-Algernon-Daniel-Keyes/dp/015603008X
[tpp]: https://www.amazon.com/Phoenix-Project-DevOps-Helping-Business/dp/0988262592
