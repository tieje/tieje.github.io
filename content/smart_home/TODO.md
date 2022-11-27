+++
title = "Smart Home TODO"
date = 2022-11-27
draft = false
[taxonomies]
tags=["smart-home-app"]
[extra]
toc=true
+++

## Chronology

11/27/2022

Surrealdb cannot be installed due to CPU architecture.
> Error: unsupported CPU architecture: armv7l

I might try supabase instead.
I don't want to use supabase because self-hosted deployment requires docker.
Considering Redis.
I'm going to try using Redis as a primary database. It's fast and persistent in memory.
I'd like to store as much data up to a specific limit on the application.
The more I think about how to add this application to another RPI, the harder it seems.
I would need to install it as a standalone application.
Or rather, I'd probably need to run it as a makefile.
It would need to do the following:
- install rust
- install redis
- set up redis. I don't actually need a username and password because it's just on a raspberry pi. Authentication and security should be handled by the raspberry pi. Setting up the actual database should not be difficult
- set up backend rust app. This should be a simple git clone and then build --release command
- the backend end API should subscribe to the redis database. It's ok to couple them together.
Instead of using a pub sub, I can use redis to directly stream to the frontend.
I would need to learn streaming, but there's actually not much to do here.
I can't just stream to the frontend.
I still need to grab data from the source using Rust.
Rust will invoke reads and writes to the redis database.
I'll need to look into the best way to stream data.
Working with the Redis CLI is easy enough, but is there a Rust client library for Redis?
There is a redis-rs crate but async await is not ready so neither is pub/sub for Redis.
https://github.com/redis-rs/redis-rs
This is fine.
This is good. I can use rust to interact with the Redis database.
I'll need to draw out the architecture though.

For the Rust backend framework, I'm considering the following
- [Rocket](https://rocket.rs/)
- Tower-web
- [actix-web](https://actix.rs/)

It looks like actix-web has the most community support, though Rocket has more Github stars.
I'll just stick with actix-web for now.

Then there's the ORM. I'll pick it up if I need to, but I hope it's functionality is covered with redis-rs.

- [x] image the rpi with default settings with rpi imager
- [x] set up ssh
  - [x] `ssh-copy-id <user>@<ip_address>` to rpi
- [x] install rust
  - [x] `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
- [x] choose a backend Rust API framework
- [x] choose an ORM

11/28/2022

**Important**: Record exactly what you did so that you can write an ansible script or makefile for it
- [ ] install redis on RPI
- [ ] model out data from scratch
- [ ] create database
- [ ] create tables
---
- [ ] create actix-web project on RPI
- [ ] determine how to gather data from the RPI
- [ ] test data collection system
- [ ] set up a single API endpoint
- [ ] set up more API endpoints
---
- [ ] create tauri project
- [ ] test querying data from the API
- [ ] build out a simple SPA for monitoring data

## Useful Links

- [tauri](https://tauri.app/)
- [redis-rs](https://docs.rs/redis/latest/redis/)
- [actix-web](https://actix.rs/)
- [diesel](https://diesel.rs/)
