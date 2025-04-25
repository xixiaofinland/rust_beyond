# Single Project to Workspace

As you build projects in Rust, it's natural to start simple: a binary
(src/main.rs) or a library (src/lib.rs) sitting neatly in a single Cargo
project. But as your ideas grow, your project can benefit from a little more
structure.

In this chapter, we'll walk through the journey of evolving a simple Rust project
into a workspace. We'll see why you might want to do it, what changes are
involved, and what benefits you gain along the way. If you're curious about the
"next step" in organizing your Rust code, this is for you!

## The Starting Point: One Project, One Crate

Let's imagine you begin with a simple library and binary combined in one project:

```
my-project/
|- Cargo.toml
|- src/
   |- lib.rs
   |- main.rs
```

The `Cargo.toml` declares both a library and a binary:

```
[package]
name = "my-project"
version = "0.1.0"
edition = "2021"

[dependencies]

[lib]
path = "src/lib.rs"

[[bin]]
name = "my-project"
path = "src/main.rs"

```

You don't even need the `[lib]` and `[[bin]]` sections if you don't overwrite
the default settings in the sample above as the name is identical to the project
name.

This works beautifully for small programs. You can define reusable code in
`lib.rs,` and build your CLI, server, or app in `main.rs,` calling into the library.

But what if you want to:
- Add another binary (e.g., a CLI tool and a server)?
- Create internal libraries that aren't part of the public API?

You surely can still put all logic into the lib crate but how about separating
concerns more cleanly across crates? That's where workspaces shine!

## Moving to a Workspace

A Cargo workspace is a way to manage multiple related crates together. Think of
it like a "super-project" that coordinates building, testing, and managing
dependencies across multiple packages.

Let's transform our project step-by-step.

### Create a Cargo.toml for the workspace

Move the existing `Cargo.toml` into a new my-project/ sub-folder. Then, create a top-level `Cargo.toml`:

```
[workspace]
members = [
    "crates/my-project-lib",
    "crates/my-project-cli",
]

```

The members list tells Cargo which packages belong to the workspace.

### Split the code into crates

We'll create two crates inside a new crates/ directory as implied in the above
workspace `Cargo.toml`.


```
my-project/
|- Cargo.toml (workspace)
|- crates/
   |- my-project-lib/
      |- Cargo.toml
      |- src/
         |- lib.rs
   |- my-project-cli/
      |- Cargo.toml
      |- src/
         |- main.rs
```

`my-project-lib` will hold the reusable library code, while `my-project-cli` will be
a binary crate depending on my-project-lib.

### Update the crate dependencies

In `crates/my-project-cli/Cargo.toml`:

```
[package]
name = "my-project-cli"
version = "0.1.0"
edition = "2024"

[dependencies]
my-project-lib = { path = "../my-project-lib" }
```

Now your CLI crate can call into the library just like before. Spend some time
to put the code and tests into the corresponding crate. It's a good brain
excercise, with the help of `cargo build --workspace`, to define the clear crate
bundary which might not be the case before.

## Why Bother?

At first, moving to a workspace might feel like extra overhead. But it brings
powerful benefits, even for relatively small projects:

- Clear Separation of Concerns: Each crate focuses on a specific task. Your codebase becomes easier to understand and maintain.
- Faster Builds: Cargo can rebuild only the crates that changed, rather than the entire project.
- Multiple Binaries: You can easily add more binaries (tools, servers, utilities) alongside your main app.
- Internal Libraries: Share code across multiple binaries without publishing it externally.
- Testing in Isolation: You can run cargo test per-crate to get faster, more focused feedback.
- Ready for Growth: When you eventually want to split parts into separate published crates (on crates.io) or keep internal libraries private, you're already halfway there.

In short, workspaces help your project scale without becoming messy.

## A Natural Evolution

You don't have to start with a workspace when writing your first Rust project.
But when your project grows just a little—adding a second binary, needing some
internal shared code—workspaces offer a clean and powerful way to stay
organized.

The best part? Moving to a workspace is an incremental change. You can migrate a
project in stages, and Rust's tooling (Cargo) makes it smooth.

If you're curious, give it a try on your next project! You'll gain both clarity
and flexibility. In this small CLI project of mine:
[jirun](https://github.com/xixiaofinland/jirun/tree/a0af5d6f76301ff278fac61a4f84e3c497730303),
I have transferred it into workspace style to prepare for growing :)!

