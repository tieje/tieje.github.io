+++
title = "Personal Smart Home"
date = 2022-11-26
draft = false
[taxonomies]
tags=["smart-home-app"]
[extra]
toc=true
+++

## Scope

The aim of this project is to build a personal smart home application that can be deployed on a Raspberry Pi 3 running vanilla Raspberry Pi OS.

## Motivation

I want to build the application in Rust as much as I can, including the web frontend.
The purpose of this approach is to learn about Rust's pros and cons as much as I can.

## Architecture and Technologies

### Information Flow

- Sensor attached to Raspberry Pi (RPI) (source) &rarr; Rust API
- redis db hosted locally on the RPI &harr; Rust API
- Rust API &rarr; Tauri desktop GUI

### Template Used

- [Yew, Axum, Tauri template](https://github.com/jetli/rust-yew-axum-tauri-desktop)

### Rust Frontend

- [yew](https://yew.rs/)

### Rust API

The API will be hosted on localhost in a production server environment.

- [online](https://crates.io/crates/online)
- [redis-rs](https://docs.rs/redis/latest/redis/)
- [actix-web](https://actix.rs/)
- maybe [diesel](https://diesel.rs/)
- [tauri](https://tauri.app/)

## Ideas

- make it so that more sensors can be added over time
- start with monitoring network uptime (my wifi has been a bit spotty lately and I want proof to show my internet provider)
- temperature
- monitor air quality
- clap twice to turn off lights
