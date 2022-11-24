+++
title = "TODO"
date = 2022-11-20
draft = false
[taxonomies]
tags=["first-post", "TODO"]
[extra]
toc=true
+++

# Chronology

11/17/2022

It builds but I need to deploy.

11/19/2022

[github actions docs](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- got down deployment

11/20/2022

I want something dark and concise.
Hermit will do.

- choose a theme
  - Considerations
    - soapstone
    - hermit
    - after-dark
    - clean blog
    - d3c3nt
    - sam
    - simple-dev-blog
    - apollo
- create about page

11/20/2022

11/21/2022

- pick a book to read about making clean code and programming architecture
  - I chose The Pragmatic Programmer because it's the most recommended programming book
- choose a rust crate library to study to get better at writing good rust code
  - I'll probably just choose tauri because it's related to what I'm doing
- work on coding problems from [codewars](https://www.codewars.com/)

11/22/2022

I've been thinking about creating a tauri app that can be used for displaying graphs for multiple sensors.
I'd like to start with an air quality sensor just because I think it might be the simplest.
Tauri is not Rust, however, working with the air quality sensor will allow me to get into low-level programming with Rust.
I'll need a micro-controller though.
Plus, I can read the Tauri github to figure out how it works, as well as improve my own Rust coding problems by example.

[Codewar solution](https://www.codewars.com/kata/577a98a6ae28071780000989/solutions)
```rust
fn minimum(arr: &[i32]) -> i32 {
    *arr.iter().min().unwrap()
}

fn maximum(arr: &[i32]) -> i32 {
    *arr.iter().max().unwrap()
}
```
Learn about the following:
- [iterators](https://doc.rust-lang.org/book/ch13-02-iterators.html?highlight=iter()#methods-that-produce-other-iterators)
- [unwrap](https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html?highlight=unwrap()#shortcuts-for-panic-on-error-unwrap-and-expect)
- [codewar kata of the day](https://www.codewars.com/kata/5899dc03bc95b1bf1b0000ad/solutions/rust)

11/23/2022

Studying the standard library is a bit too esoteric for me. I'll stick with studying codewar problems and tauri.

- [traits](https://doc.rust-lang.org/book/ch10-02-traits.html?highlight=trait#traits-as-parameters)
- [codewar kata of the day](https://www.codewars.com/kata/58ca658cc0d6401f2700045f/train/rust)

```rust
// my solution
fn find_multiples(n: u32, limit: u32) -> Vec<u32> {
    let mut some = 0;
    let mut v:Vec<u32> = Vec::new();

    while some <= limit && some + n <= limit {
        some += n;
        v.push(some);
    }
    v
}
// best solution
fn find_multiples(n: u32, limit: u32) -> Vec<u32> {
    (n..=limit)
        .step_by((n) as usize)
        .collect()
}
```

11/24/2022

- [range inclusive operator](https://www.cloudhadoop.com/rust-range-operator-examples/)
- [step_by](https://doc.rust-lang.org/std/iter/struct.StepBy.html)
- [collect](https://doc.rust-lang.org/std/iter/trait.Iterator.html#method.collect)
- [Generic Data Types](https://doc.rust-lang.org/book/ch10-01-syntax.html)
- [codewar kata of the day](https://www.codewars.com/kata/5a34af40e1ce0eb1f5000036/train/rust)


- update portfolio site with rust and most recent portfolio blog
- figure out what you want to work on
- get active in the rust community and see which libraries need contributors
- create a post about figuring out what you want to do with rust
- fix disqus

## Bookmarks

- [The Pragmatic Programmer](file:///Users/tieje/Desktop/the-pragmatic-programmer.pdf)

pdf page left off here:

57

Impatient Duplication

## Useful links

- [zola docs](https://www.getzola.org/documentation/getting-started/overview/)

## Reading List

- [The List](https://www.best-books.dev/list/best-programming-books)

## Finished Books From Reading List

None so far