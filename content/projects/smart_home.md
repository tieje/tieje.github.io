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

The aim of this project is to build a personal smart home application that can be deployed on a Raspberry Pi 3 running vanilla Raspbian.

## Motivation

I want to build the application in Rust as much as I can, including the web frontend.
The purpose of this approach is to learn about Rust's pros and cons as much as I can.

## Architecture and Technologies

### Info Flow

- Sensor attached to Raspberry Pi (RPI) ->
- Surreal db database hosted locally on the RPI ->
- Rust Backend App on the RPI ->
- Tauri desktop GUI (possibly for web later, but we'll see)

## Useful Links

- [tauri](https://tauri.app/)
- [surrealdb](https://surrealdb.com/)

## Ideas

- make it so that more sensors can be added over time
- start with monitoring network uptime (my wifi has been a bit spotty lately and I want proof to show my internet provider)
- temperature
- monitor air quality
- clap twice to turn off lights
