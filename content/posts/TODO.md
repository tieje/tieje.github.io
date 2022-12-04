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

I may have reached diminishing returns for codewars.
The real complexity is behind the implementation with struct, impl, traits, and lifetimes.
I'll need to start creating simple programs.

- [review closures](https://doc.rust-lang.org/book/ch13-01-closures.html?highlight=anonymous%20function#closures-anonymous-functions-that-capture-their-environment)
- [codewar kata of the day](https://www.codewars.com/kata/56efc695740d30f963000557/train/rust)

```rust
// my solution
pub fn to_alternating_case(s: &str) -> String {
    s
        .chars()
        .map(|x: char| -> String {
            if x.is_uppercase() && x.is_alphanumeric() {
                x.to_lowercase().to_string()
            } else {
                x.to_uppercase().to_string()
            }
        })
        .collect::<String>()
}
// The solution I was trying to do OR what I think is the best solution
fn to_alternating_case(s: &str) -> String {
    s.chars()
        .map(|letter| match letter.is_uppercase() {
            true => letter.to_lowercase().to_string(),
            false => letter.to_uppercase().to_string(),
        })
        .collect()
}
```

11/26/2022

Instead of creating random little applications, I think it would best for me to just start planning and building what I want to build.
I'll be creating my own smart home system starting with very simple projects like displaying temperature on a tauri app in real time.
Because this is a synchronous application with little to no variability in workload, it doesn't make sense to learn and use RabbitMQ.
I'll need to create a separate file for the scope of the application.
I'll need a database but nowadays, there are so many options.
Supabase and Surreal db are at the top of my list right now.
I'd rather go with Surreal db just because it's written Rust.
This is becoming a pain because allocating physical resource is a drag. I need to buy a temperature hat for a raspberry pi.
Then I need to wipe the RPI clean for this new project.
Then I would probably want to use ansible to set up a raspberry pi and then build commands so that I'll never need to do that again... and then inevitably forget so then I'll need to do it again anyways...
It's not super hard. I just need a power source. I'll skip the fancy wiring because I just don't have enough room right now.

The big question is... when do I get to write Rust...
I can use Rust to run my projects on the RPI.
But Tauri is a straight up web way to build multiplatform desktop apps.
It seems like I'll be using one RPI. This RPI is a database and will handle the backend logic.

After doing some research, it looks like there are a few things that I need to do:

1. I need to build up a lot more foundational knowledge.
2. If I really want to write in Rust, I should start with writing Rust for web development.
   1. I should not just rely on using Tauri for development.
3. I should not give up on my plan for a personal smart home system. Though I should probably make it a bit scalable so I don't necessarily need to do the work again.

Performing additional research, it looks like I'll be using Tauri.
Tauri just looks like the most promising right now.

- [x] [review generic types chapter](https://doc.rust-lang.org/book/ch10-00-generics.html)
- [x] [review traits](https://doc.rust-lang.org/book/ch10-02-traits.html)


11/27/2022

Completed my reading, but I spent today breaking ground and planning out the application.

- [x] create a "working commit" command for .zshrc file

11/28/2022

- [x] [review lifetimes](https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html)

11/29/2022

It looks like before I'll code anything, there is some reading and research that I should do.
I'll need to separate learning about Rust from working on the actual project.

- [x] Read ~10 pages of a programming book
- [x] Study Rust language
- [x] Work on Smart Home App

11/30/2022

- [x] Read ~10 pages of a programming book
- [x] Study Rust language
  - [x] [look into how the online crate works](https://github.com/jesusprubio/online)

12/1/2022

The tutorials are out of date as the technology is still being developed. It's 0.20.0.
Not even 1.0.0 yet.
Things are likely to change.
It looks like I'll need to understand yew from scratch.
I might even need to look directly at the codebase since the documentation might not be there.

- [x] Read ~10 pages of a programming book
- [x] looked into yew

12/3/2022

- [x] [read yew documentation](https://yew.rs/docs/category/concepts)
- [x] [read about *move* keyword](https://doc.rust-lang.org/std/keyword.move.html)

12/4/2022

The main thing that I'm trying to learn is:
- how can I implement abstractions in Rust and Yew
- getting comfortable with Rust code patterns

- [x] build a simple counter app with yew
- [x] extract *increase* to its own function
- [x] further extract *increase* to its own function (extract cloning)
- [x] make a function that does increase, decrease, and reset from a variable
  - [reference](https://github.com/prithivirajmurugan/Simple-counter/blob/main/src/main.rs)
- [ ] [read about smart pointers in Rust](https://doc.rust-lang.org/book/ch15-00-smart-pointers.html)

12/5/2022

- [ ] build a simple to-do app with yew

**Dailies**
- [ ] Read ~10 pages of a programming book
- [ ] Study Rust language
- [ ] [Study Cargo tool](https://doc.rust-lang.org/cargo/index.html)
- [ ] Work on Smart Home App

**Wonders**
- [ ] [learn about writing tests in Rust](https://doc.rust-lang.org/book/ch11-01-writing-tests.html)
- [ ] [read redis documentation](https://redis.io/docs/)
- [ ] [look into Aspect Oriented Programming](https://en.wikipedia.org/wiki/Aspect-oriented_programming)
- [ ] [look into Composite Orient Programming](https://en.wikipedia.org/wiki/Composite_pattern)
- [ ] [review slice type](https://doc.rust-lang.org/book/ch04-03-slices.html)
- [ ] [review smart pointers](https://doc.rust-lang.org/book/ch15-01-box.html)

---
**Home**
- [ ] update resume
- [ ] update portfolio-blog-fresh and linkedIn with new resume
- [ ] get active in the rust community and see which libraries need contributors
- [ ] create a post about figuring out what you want to do with rust
- [ ] fix disqus

## Bookmarks

- [The Pragmatic Programmer](file:///Users/tieje/Desktop/the-pragmatic-programmer.pdf)
  - pdf page left off here:
    - 141
    - Other Useful Invariants

## Useful links

- [zola docs](https://www.getzola.org/documentation/getting-started/overview/)
- [Excellent Review of Rust GUIs](https://dev.to/davidedelpapa/rust-gui-introduction-a-k-a-the-state-of-rust-gui-libraries-as-of-january-2021-40gl)
- [tauri](https://tauri.app/)

## Reading List

- [The List](https://www.best-books.dev/list/best-programming-books)

## Finished Books From Reading List

None so far
