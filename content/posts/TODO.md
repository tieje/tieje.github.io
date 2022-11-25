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


```rust
// my solution
pub fn to_csv_text(array: &[Vec<i8>]) -> String {
    let mut csv_text = String::new();

    for arr in array {
        for ele in arr {
            csv_text.push_str(&ele.to_string());
            csv_text.push(',')
        }
        // remove excess ','
        csv_text.pop();
        csv_text.push('\n')
    }
    // remove last excess character which will be "\n"
    csv_text.pop();
    csv_text
}

// best solution
fn to_csv_text(array: &[Vec<i8>]) -> String {
    array
    .iter()
    .map(|row| 
        row.iter()
           .map(|x| x.to_string())
           .collect::<Vec<_>>()
           .join(",")
    )
    .collect::<Vec<_>>()
    .join("\n")
}
```

11/25/2022

- [review closures](https://doc.rust-lang.org/book/ch13-01-closures.html?highlight=anonymous%20function#closures-anonymous-functions-that-capture-their-environment)
- [learn about writing tests in Rust](https://doc.rust-lang.org/book/ch11-01-writing-tests.html)
- [codewar kata of the day](https://www.codewars.com/kata/56efc695740d30f963000557/train/rust)


- update resume
- update portfolio-blog-fresh and linkedIn with new resume
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

## My Process

### Things To Always Do

- Read at least 10 pages of a book that I'm currently reading.

### Phase I
Get comfortable with Rust.

Every day until I feel comfortable writing Rust:
1. Take notes on documentation that you set for yourself to read.
2. Work on one coding problem with a solution written in Rust.
3. Set up links to documentation for you to read next time either related to the solution of the problem or features or packages of the language.

### Phase II
Write a basic application in Rust complete with testing.

TODO
- Figure out what to build

### Phase III
Write an advanced application in Rust complete with testing.
I have chosen to work with micro-controllers and IoT to create my own smart home application.
Things I'd like to control or keep in constant measurement in a stream:
- turn on and off lights with a double clap of hands
- monitor air quality
- monitor temperature

#### Tech
- Tauri
- Rust for micro-controllers and backend development
