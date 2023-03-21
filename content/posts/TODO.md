+++
title = "TODO"
date = 2022-11-20
draft = true
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

I almost emailed the Yew team to become a contributor.
Instead of totally committing to Yew, I should probably make the thing that I wanted to make first and then commit to Yew.

The main thing that I'm trying to learn is:
- how can I implement abstractions in Rust and Yew
- getting comfortable with Rust code patterns

- [x] build a simple counter app with yew
- [x] extract *increase* to its own function
- [x] further extract *increase* to its own function (extract cloning)
- [x] make a function that does increase, decrease, and reset from a variable
  - [reference](https://github.com/prithivirajmurugan/Simple-counter/blob/main/src/main.rs)
- [x] [read about smart pointers in Rust](https://doc.rust-lang.org/book/ch15-00-smart-pointers.html)
- [x] start a simple to-do app with yew
- [x] save your .zshrc file to your repo

12/5/2022

I'll read Rust files in Yew to learn things about Rust code and about Yew.
Then I'll spend the other half of my time actually practicing coding in Rust with Yew.

- [x] plan out todo app component tree
- [x] plan out some possible functions

12/6/2022

I might want to consider learning about commonly used libraries in Rust.

- [x] read some Yew code
- [x] programming read book
- [x] [read the cargo book and left off here](https://doc.rust-lang.org/cargo/guide/tests.html)
- [x] build a static version of the todo app
- [x] extract todo item component

12/7/2022

I was invoking it too soon with `collect()::`. The solution was `collect::<Html>()`. This is a basic syntax error that I should have been able to see, but I guess I need to get use to the syntax patterns.

- [x] fixed issue. I was using collect improperly.

12/10/2022

- [x] extract components

12/12/2022

- [x] implement the "onClick" property on your custom element that is normally found on normal HTML elements

12/13/2022

I have determined that the extraction is limited because we cannot simply get the value of
external variables into a fn item. What would need to occur instead is capturing the environment, which is simple enough.
Capturing the environment is not only simpler, but it is necessary for yew applications.

I'm close though. Let me look into it and try a little bit more.

12/14/2022

Finally figured how to abstract the delete_todo function. That took a while.

- [x] extract the delete_todo function

12/15/2022

I will want to take advantage of html form and input tags to add user input from a value.
Remember to prevent default if you need to.

- [ ] figure out how to handle input and form handling in yew

- [ ] write a blog post reporting your findings in the counter app
- [ ] write a blog post reporting your findings in the todo app
- [ ] read documentation on how [yew interfaces with basic web technologies](https://yew.rs/docs/category/using-basic-web-technologies-in-yew)
- [ ] implement input addition functionality
- [ ] update state on the app element
- [ ] think about updating Jet li's awesome yew projects to be modern implementations
- [ ] [Read wasm bindgen guide](https://rustwasm.github.io/wasm-bindgen/introduction.html)
- [ ] [Read wasm book](https://rustwasm.github.io/docs/book/introduction.html)

- [ ] pass callback function todo_items that updates the state
- [ ] pass callback functions todo_input
- [ ] try to turn callback functions into hooks
- [ ] add css to make it look decent enough

YEW TODO APP

COMPONENT TREE
- [ ] App
  - [ ] Todo container
    - [ ] Input
    - [ ] Todo list
      - [ ] list items

FUNCTIONS
- [ ] Input handling
- [ ] delete list item
- [ ] create list item
- [ ] event listener shortcuts
- [ ] Try to make everything a convenient hook

CSS

1/1/2023

New year, new me.

I want to get better at coding in Rust. I need to be a bit more incremental in my approach and maybe not be so ambitious.
My new rule is to only use libraries that are at least 1.0.

1. Codewars, 1 problem.
2. Neetcode, 1 problem in Rust.
3. Read a page of documentation: Cargo, Rust, or a Library.
4. Recreate common functions or command line operations such as:
   1. touch and folder file generator.
   2. web scraping
   3. A simple tic-tac-toe game written in Rust.
   4. A penguin animation written in Rust.
      1. Penguin loading icon where the penguin jumps and slides on its belly (this is closer to CSS though).
   5. Something related to networking.
5. Try to find a codebase that you'd like to contribute to.

Above were my initial thoughts. But I feel like understanding how to do basic things with Rust will matter a lot.
1. Styling and the best way to provide documentation in Rust.
2. Making something from scratch in Rust.
3. Creating an API with Rust (possibly use Rocket).
4. Creating a basic frontend with Rust (using established Rust frameworks).
5. Having a good understanding of common Rust libraries.

I eventually decided to learn Rust by looking at the most downloaded libraries on crates.io.
It looks like I'll will also be able to learn about the direction of the language, as in what is it currently being used for.
Right now, I'm trying to figure out what the [Syn](https://github.com/dtolnay/syn) library is being used for.
It's used in procedural macros, which is used to generate Rust code.

I feel that I have a basic understanding of Rust macros now. Code that generates the code: meta programming.

As a side note, even though The Pragmatic Programmer was useful, the concepts become increasingly higher level and they don't apply to me professionally yet.

- [x] read [procedural macros docs rust](https://doc.rust-lang.org/reference/procedural-macros.html)

1/2/2023

Good article on the [difference between .clone() and .to_owned()](https://www.becomebetterprogrammer.com/rust-clone-vs-to_owned/).

- [ ] complete the derive(Builder) project for the workshop
- [ ] do the [procedural macros workshop](https://github.com/dtolnay/proc-macro-workshop)
- [ ] go back to the [Syn](https://github.com/dtolnay/syn) library and try to understand the problem it solves

1/3/2023

It was going well... and then I got stuck with Result. I'm not sure how to progress and there are no answers...
I guess I'll need to choose a simpler exercise.

- [x] build a curriculum

1/4/2023

The rustling course work is doable for me right now.
In the future, I'd like to continue working on Rust, but only do very simple things just to get the hang of it.

- [x] intro
- [x] variables
- [x] functions
- [x] if
- [x] quiz1

1/11/2023

- [x] primitive_types
- [x] vecs

1/12/2023

It's better to go slow and learn a lot than to go fast and learn nothing.
- [x] move_semantics

1/17/2023

Yesterday, I asked my boss to perform a code review. I learned a lot about what I don't know.
Namely, I don't know design patterns very well.
It seems like I'm lacking a lot of foundational knowledge.
Foundational knowledge, however, is useless without applying it.
Refactoring Guru is a great website and it has design pattern examples for four languages that I'm interested in:

1. Rust
2. Python
3. TypeScript
4. C#

I want to learn how to use design patterns for all of these languages.
For each design pattern, I'd like to build a small associated Rust project and an associated blog post explaining the project and the pattern.
As much as I would like to build something revolutionary and cool, I have a lot of foundational knowledge that I need to build.
For the most part, I'd prefer to fully transition to Rust.
Because Python, TypeScript, and C# are all object-oriented languages, it makes sense to just use one language as a representative. In this case, I'd like to practice C# since I'm using it a lot at work.
It makes sense to build the same sample project in Rust and C# and make a post for each to design each design pattern.
While mastering design patterns, I'd like to go through the Rust design patterns book as well as the rustlings course.
For the rustlings course, I'll go through one problem per day, with a hard limit of 25 min.
For Rust design patterns, I'll devote 25 min to studying a page per day. This is not as easily quantified and it will take about 5 min for me to transition to the next subject.
For design patterns, I'd like to take 25 min per day to study a design pattern.
I'd like to study the design pattern on its own first.
Since C# is a bit easier to understand, I'd like to go through the C# example of the design pattern first, then go through the Rust example.
Then I'll create a simple Rust and C# projects that applies the design pattern.
Unless I can think of an interesting thing to build for the design pattern, my projects may be heavily influenced by the example.
The end result will be a blog post for each project, explaining the design pattern.
After learning design patterns, I'd like to start building physical things. Probably the smart home project. Or whatever is interesting to build in Rust. Maybe Yew will be 1.0 by then.

- [x] build a curriculum for coding

1/18/2023

I hate Powell 365. And SharePoint. But rather than let this technology stress me out, I will seek to understand it. I will create unofficial documentation under my personal email. Writing good documentation is a valuable skill to have. It's probably a good idea to build up this skill with something that I'm stressed out about.

When it comes to reading about Rust Design Patterns, it's probably best to spend some time on each topic. It's probably best to passively read and try to understand what is going on. Ultimately, I will be coming back to these topics anyways as I write more Rust.

I think I'll need to rethink my approach to learning design patterns. I'm curious about what's out there, so I'd much rather just get a general overview of everything and make examples of the ones that I would use the most, especially those that are relevant to my work. I've been going back and forth about depth vs breadth of knowledge. It's best to do breadth first with multiple passes, layering knowledge and making connections to other design patterns first, and then building upon that knowledge.

- [x] rustlings
  - unit structs are used for implementing traits without data
```rs
pub struct Error;
// used for implementing the Error trait although it does not have data, although their return is the same as an empty tuple, ()
```
- [x] [Rust Design Patterns](https://rust-unofficial.github.io/patterns/idioms/deref.html)
  - we want to treat collection like smart pointers by using the Deref trait. This allows for both owning and borrowing views of data.
```rs
use std::ops::Deref;

struct Vec<T> {
    data: RawVec<T>,
    //..
}

impl<T> Deref for Vec<T> {
    type Target = [T];

    fn deref(&self) -> &[T] {
        //..
    }
}
```
- [x] [Design Patterns](https://refactoring.guru/design-patterns/catalog)
  - [x] Singleton
    - [x] C#
      - There is a naive and thread-safe implementation of singletons. Both use constructors, however, the thread-safe version requires the use of locks
    - [x] Rust
      - I am not knowledgeable about Rust yet to understand the Rust implementation yet, but I'll move on for now.
    - Although singleton is very simple, it's also an anti-pattern due to a variety of reasons. I will avoid singleton patterns for now.
- [x] Write Powell Documentation
  - [x] create repo
  - [x] create zola site with documentation theme
  - [x] deploy site on github pages

1/19/2023

I want to revise studying Rust Design Patterns. Since I don't understand Rust enough yet, the concepts in the book don't make enough sense to me. I'd like to replace it something more hands-on.
I think it's best for me for me to get the basics down.
This means going through the rustlings course, reading the book, and creating very small projects.
Rather than focusing on multiple Rust resources, I should focus on learning one resource very well.
I'm going to focus on learning the Rust language well first through the book and through Rustlings. Then I'll read associated books like cargo, rustdoc, rustc, and rustnomicon in that order while creating simple programs in Rust.

- [x] Write Powell Documentation
- [x] rustlings
  - [struct2: update syntax](https://doc.rust-lang.org/book/ch05-01-defining-structs.html#creating-instances-from-other-instances-with-struct-update-syntax). Rather than typing out all of the fields, simply update only the fields you need to update and keep the rest of the object the same
  - [struct3: Self is a keyword for the constructor that simply gets replaced with the instance of the struct that its calling](https://doc.rust-lang.org/book/ch05-03-method-syntax.html)

1/21/2023

Reorganized Powell docs and got links working between local and prod. This took a bit of time.
Deleted other branches mostly because they simply impeded my progress. As one-man show, I should prioritize myself first. No need to scale yet.

- [x] Write Powell Documentation
- [x] rustlings
  - [x] [enums1: ](https://doc.rust-lang.org/book/ch06-03-if-let.html)
  - [x] enums2

1/22/2023

- [x] rustlings
  - [x] enums3
  - [x] strings1
  - [x] strings2
  - [x] strings3
  - [x] strings4
  - [x] modules1
  - [x] modules2
  - [x] modules3

1/24/2023

- [x] Write Powell Documentation
- [x] rustlings
  - [x] hashmaps1
  - [x] hashmaps2
  - [x] hashmaps3

1/25/2023

- [x] Write Powell Documentation

1/29/2023

- A value can be retrieved from the Option trait with Some().
- `while let` is helpful for checking over an item with the same test like in a while loop, however, the while loop breaks automatically without us needing to implement it ourselves.
- `ref` allows for borrowing without moving. In a match arm, this allows the value to be used inside of the match arm
- map_err() is a function that will apply a function as a result of an error. This helps with grouping errors together by an implementation.
- the best way to think of question marks in rust is that their previous implementation was the `try!` macro

- [x] rustlings
  - [x] quiz2
  - [x] options1
  - [x] options2
  - [x] options3
  - [x] errors1
  - [x] errors2
  - [x] errors3
  - [x] errors4
  - [x] errors5
  - [x] errors6

1/30/2023

- [x] rustlings
  - [x] generics1
  - [x] generics2
  - [x] traits1
  - [x] traits2

1/1/2023

Traits are not really something you'll be making yourself most of the time, I think. There will instead mostly be existing traits that you'll need to implement.

- [x] rustlings
  - [x] traits3
  - [x] traits4
  - [x] traits5
  - [x] quiz3

1/4/2023

- [x] rustlings
  - [x] test1
  - [x] test2
  - [x] test3
  - [x] lifetimes1
  - [x] lifetimes2
  - [x] lifetimes3
  - [x] iterators1
  - [x] iterators2

1/11/2023

I think I'm done with rustlings for now.
I'm going to focus on learning different web frameworks with Rust, starting with the most developed and working my way down from there.

Actix-web is the most developed right now. I don't see other web frameworks catching up its level. However, its future as a web framework is unclear. It looks like it's in [maintenance mode](https://actix.rs/docs/whatis).

- [rocket](https://rocket.rs/)

- [x] rustlings
  - [x] iterators3
  - [x] iterators4
  - [x] iterators5

1/12/2023

There has been so much JS frontend development, that it is now ridiculously fast. It was made fast by using Rust in the JS runtime. It doesn't really make sense to use Rust for the frontend because no other language has had as much development as JS. And JS is fast enough.

I feel like the best way to really start using Rust is for embedded systems programming.

I could go off and learn embedded systems programming...
Or, I could focus on learning how to replace my existing tech stack with Rust. It's best to specialize right now. I specialized in web development.

Yew has a great proposition: no more JS.
Using Rust for frontend and backend.
Frontend JS has a lot of lessons for this tricky space.
I'll focus on becoming a Yew contributor for now.

1/13/2023

```rust
#![allow(clippy::needless_doctest_main)]
```
This is an [inner attribute](https://doc.rust-lang.org/reference/attributes.html). The inner attribute applies to the entire closure that it resides in. If it's in a file, then it must apply to the entire file. The above can therefore be translated as ***"Only for this document, have the attribute _____"***. The `#![allow(unused_variables)]` variables attribute is a good example of what is going to occur. The compiler will see the `allow` attribute and allow something to occur that it normally would not occur such as having unused variables. In this case, we are allowing [`needless_doctest_main`](https://rust-lang.github.io/rust-clippy/master/index.html) from `clippy`.

- [x] read the [contributing guide](https://github.com/yewstack/yew/blob/master/CONTRIBUTING.md)

2/13/2023

*doctests* refer to [documentation tests](https://doc.rust-lang.org/rustdoc/write-documentation/documentation-tests.html), which is part of the larger rustdoc tool.
- [x] why would we want to use [needless_doctest_main](https://rust-lang.github.io/rust-clippy/master/index.html)?

2/16/2023

```rust
#![cfg_attr(documenting, feature(doc_cfg))]
#![cfg_attr(documenting, feature(doc_auto_cfg))]
```
[`cfg_attr`](https://doc.rust-lang.org/reference/conditional-compilation.html) specifies rust documentation features. documenting turns out to be a custom feature that if implemented, will cause any feature with the condition of documenting (see Cargo.toml) to activate.
[`doc_cfg`](https://docs.rs/doc-cfg/latest/doc_cfg/attr.doc_cfg.html?search=doc_auto_cfg) is a feature where the item (in this case the entire file) being documented will show up in the final documentation. [`doc_auto_cfg`](https://doc.rust-lang.org/stable/unstable-book/language-features/doc-auto-cfg.html) is an unstable feature.

```rust
#![cfg_attr(nightly_yew, feature(fn_traits, async_closure, unboxed_closures))]
```

The features fn_traits, async_closure, and unboxed_closures are only activated if the `--cfg nightly_yew` is used in compilation.

`extern crate` is a deprecated rust method for importing modules

```rust
// Rust 2015

#[macro_use]
extern crate log;

// Rust 2018

use log::error;
```

I needed the `html_nested!` macro a few months ago, but I did not know it existed.

The `props!` macro allows for building Properties of components.

---

I will be building a simple console project that creates a file

- [x] read `yew/lib.rs`

Rust File Creator
- [x] ask to create either a file or folder
- [x] take user input

A file creator console app, similar to the unix touch command, except with prompts. I'm learning how to write in Rust.

2/17/2023

[Tokens](https://web.mit.edu/rust-lang_v1.25/arch/amd64_ubuntu1404/share/doc/rust/html/reference/tokens.html) are primitive productions in grammar defined regular languages. Literals consist of a single token and are strings, escapes, bytes, numbers, and more. Therefore, a stream of tokens is a stream of literals, which is why "hello", as a string literal, is actually just one token. Streams of tokens are probably separated by commas.

```rust
pub struct Classes(Punctuated<ClassExpr, Token![,]>);
```
The struct above is a [tuple struct](https://doc.rust-lang.org/std/keyword.struct.html). Tuple structs don't have named fields, but their input must match the type.

[Token!](https://docs.rs/syn/latest/syn/token/index.html) is a type-macro that expands to the token type of the given token. In this case, we are defining the delimiter as a comma.

[Punctuated<T, P>](https://docs.rs/syn/latest/syn/punctuated/struct.Punctuated.html) is a syntax tree of type `T` being separated by type `P`.

The type we are matching for is custom type `ClassExpr` defined in `packages/yew-macro/src/classes/mod.rs`

- [x] look at line 115 of `yew/lib.rs` for `classes!` macro. Investigate what it does and how it does it

2/17/2023

It's not the best idea to get caught up in the details of a specific function. Unless I'm building something related to the features implemented, I should continue focusing on getting the bigger picture.

At this point, it may be best to start actually start using yew again so I have an incentive to read the source code.

I have decided to not build it because its just not very interesting to me.

I'll focus on yew Github issues instead.

- [x] read `packages/yew-macro/src/classes/mod.rs`
- [x] yew issues
  - [ ] sent email to be a collaborator

2/19/2023

- [x] [yew issues](https://github.com/yewstack/yew/issues)
- [x] coolmetsu site
  - [x] template from [github](https://github.com/yewstack/yew-trunk-minimal-template)
  - [x] update metadata
    - [x] cargo.toml
      - [x] name
      - [x] version
      - [x] description
      - [x] repository
    - [x] index.html
      - [x] <title>
    - [x] README.md
    - [x] License
      - [x] year
      - [x] author
  - [x] replace sample code app.rs
  - [x] replace sample code index.scss
  - [x] push to [github](https://github.com/tieje/coolmetsu)
- [x] choose temporary SVG logo
  - use the [yew logo](https://yew.rs/img/logo.png) for now
- [x] create a layout for big ideas in Figma

2/20/2023

- [x] [yew issues](https://github.com/yewstack/yew/issues) - no more than 30 min
- [x] [update yew-tailwind template](https://github.com/Ja-sonYun/yew-template-for-github-io)
  - [x] install homebrew 4.0
  - [x] install pkg-config
  - [x] install open ssl
  - [x] install cargo update (didn't need to do this actually)
  - [x] install cargo edit
  - [x] run cargo upgrade to upgrade all packages in cargo.toml

2/21/2023

- [x] [yew issues](https://github.com/yewstack/yew/issues)
- [x] [update yew-tailwind template](https://github.com/Ja-sonYun/
  - [x] update README
  - [x] fix startapp problem
  - [x] fix router problem
  - [x] merge with yew-0.20
  - [x] email for push access

- [x] coolmetsu site
  - [x] update template
  - [x] update README
  - [x] create road map

2/22/2023
- [x] [coolmetsu site](https://github.com/tieje/coolmetsu)
  - [x] build general layout with Yew for mobile

2/23/2023

padding in tailwind is actually static.


- [x] [coolmetsu site](https://github.com/tieje/coolmetsu)
  - [x] get down nav bar

2/26/2023

- [x] finish with navbar

2/27/2022

- [ ] look into how to create a store

3/19/2023

The best way I can think of to make more money is to focus on three things:
I will study from 8 to 11pm every day and spend one hour on each topic.

- get AWS certification
  - pick up where you left off. 30 min of video and making new cards. 30 min of learning anki cards.
- study design patterns
  - focus on one design pattern per week. Learn the implementation in your main languages.
- study coding problems on leetcode
  - spend half the time working on a solution and the other half learning about the real solution

The recipe for a factory method is:
```
class Creator(ABC_base_class):
  factory_method()
  shared_method()

class Creator1(Creator):
  def factory_method(): Common_Interface
    return Product1()

class Creator2(Creator):
  def factory_method(): Common_Interface
    return Product2()

class Common_Interface(ABC_base_class):
  @abstractmethod
  def shared_operation():

class Product1(Common_Interface):
  def shared_operation():
    overrides

class Product2(Common_Interface):
  def shared_operation():
    overrides

def client_code(creator: Creator):
```

This way we can define the creator and use the methods that are in Product, except they're overridden to Product1 or Product2.

- [x] [study AWS](https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/learn/lecture/11851422#overview)
- [x] [study design patterns](https://refactoring.guru/design-patterns/factory-method)
- [x] [study coding problems](https://leetcode.com/)

3/20/2023

AWS is mostly watching videos and creating flashcards. Only the last ten minutes or so is reviewing flashcards. I'll need to re-watch everything again, as well as keep reviewing my AWS flashcards in the future.

For design patterns, it's better if I just take a week to really learn each pattern in multiple languages.

In Rust, the Factory Method design pattern looks like it's built into the language itself.

https://leetcode.com/problems/unique-number-of-occurrences/

I should also apply to at least one job during this time-frame as well.

- [x] [study AWS](https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/learn/lecture/11851422#overview)
- [x] [study design patterns](https://refactoring.guru/design-patterns/factory-method)
- [x] [study coding problems](https://leetcode.com/problems/valid-parentheses/solutions/2411675/very-easy-100-fully-explained-c-java-python-js-python3/?languageTags=python)

3/21/2023

- [ ] [study AWS](https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/learn/lecture/11851434#overview)
- [ ] [study design patterns](https://refactoring.guru/design-patterns/factory-method)
  - [ ] [what is & in the Rust example?](https://refactoring.guru/design-patterns/factory-method/rust/example)
- [ ] [study coding problems](https://leetcode.com/problems/valid-parentheses/solutions/2411675/very-easy-100-fully-explained-c-java-python-js-python3/?languageTags=python)
- [ ] apply to one job

4/20/2023

- [ ] [solve Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)


## Daily TODO

- [ ] [study AWS](https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/learn/lecture/11851422#overview)
- [ ] [study design patterns](https://refactoring.guru/design-patterns/factory-method)
- [ ] [study coding problems](https://leetcode.com/)
- [ ] apply to one job



- [ ] [yew issues](https://github.com/yewstack/yew/issues)
- [ ] [coolmetsu site](https://github.com/tieje/cool-metsu)
- [ ] [update yew-tailwind template](https://github.com/Ja-sonYun/yew-template-for-github-io)
  - [ ] submit PR

- [ ] read [Rust API Guidelines](https://rust-lang.github.io/api-guidelines/naming.html)
- [ ] read [Elegant Library APIs in Rust](https://deterministic.space/elegant-apis-in-rust.html)

## Simple Projects
- "touch" - file creator in Rust
- "checki" - command to check if there is internet connection in Rust

## Rust Resources In Order

- [ ] [Design Patterns](https://refactoring.guru/design-patterns/catalog)
  - After each n<sup>th</sup> pass:
    1. General overview.
    2. Write a post.
    3. Create a C# example and explain it in a post.
    4. Create a Rust example and explain it in a post.
- [rust](https://doc.rust-lang.org/book/)
- [cargo](https://doc.rust-lang.org/cargo/index.html)
- [rustdoc](https://doc.rust-lang.org/rustdoc/index.html)
- [rustc](https://doc.rust-lang.org/rustc/index.html)

- [ ] https://github.com/rust-lang/rustlings
- [ ] 
- [ ] https://rust-unofficial.github.io/patterns/
- https://rust-lang.github.io/async-book/01_getting_started/01_chapter.html
- https://rust-unofficial.github.io/too-many-lists/
- https://nnethercote.github.io/perf-book/title-page.html
- https://tokio.rs/tokio/tutorial
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
    - 171
    - Business Logic

## Useful links

- [zola docs](https://www.getzola.org/documentation/getting-started/overview/)
- [Excellent Review of Rust GUIs](https://dev.to/davidedelpapa/rust-gui-introduction-a-k-a-the-state-of-rust-gui-libraries-as-of-january-2021-40gl)
- [tauri](https://tauri.app/)

## Reading List

- [The List](https://www.best-books.dev/list/best-programming-books)

## Finished Books From Reading List

None so far
