## Traits

Types in Rust are powerful and versatile. Traits define shared behavior that
multiple types can implement.

### Default implementations

Traits in Rust are similar to interfaces in other languages but can also provide
default implementations for methods.

Typically, an interface defines method signatures without any implementation. In
Rust, however, you can supply default method implementations directly within a
trait.

>Hover over the code below and click " <i class="fa fa-play"></i> " to execute
and see the result.

```rust
trait Greet {
    fn greet(&self) { // Default implementation
        println!("Hello from the default greeting!");
    }
}

struct Person;

impl Greet for Person {} // Uses the default implementation

fn main() {
    let person = Person;
    person.greet(); // Outputs: Hello from the default greeting!
}
```
We can, of course, override this default behavior like so:

```rust
# trait Greet {
#     fn greet(&self) {
#         println!("Hello from the default greeting!");
#     }
# }
#
# struct Person;
// --snip--

impl Greet for Person {
    fn greet(&self) { // Overwrite the default implementation
        println!("Hello from Person greeting!");
    }
}

fn main() {
    let person = Person;
    person.greet();  // Outputs: Hello from Person greeting!
}
```

### Traits as Function Parameters and Return Types

Once the Greet trait is defined, it can be used as a type for function
parameters and return values:

```rust
fn main() {
    let person = Person;
    do_greet(person);

    let returned = return_greet();
    returned.greet();
}

fn do_greet(greetable: impl Greet) { // Accepts any type implementing Greet
    greetable.greet();
}

fn return_greet() -> impl Greet { // Returns some type implementing Greet
    Person
}

// --snip--
# struct Person;
#
# impl Greet for Person {}
#
# trait Greet {
#     fn greet(&self) {
#         println!("Hello, greeting!");
#     }
# }

```

When reading more and more Rust code, we see that experienced Rust developers
frequently use standard library traits. Rust provides common traits as both
guidelines and best practices. This not only helps us learn Rust but also
provide great references when programming in other languages.

In the following section, let's have a look at the out-of-box common traits!
