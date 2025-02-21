+++
title = "How to Code Anywhere, Anytime with Termux"
date = 2025-02-20
draft = false
[taxonomies]
tags=["termux", "raspberry_pi", "ssh", "emacs", "android"]
[extra]
toc=true
+++

As a doting husband, I often find myself comforting my wife. It is my greatest joy in life.

And yet.

It is completely antithetical to the merging of man with machine. It is polar opposite of the hustle, grindset mindset that has earned me everything that I have. I must admit, I'm an American.

So I was born an American with a smartphone in one hand, a fist of cash in the other, and even worse, I'm a developer. Here's how I augmented my cybernetic skill tree:

## Requirements

- A smartphone. I use Android, but Termux should work on IPhone.
- A low-power computer. I recommend a raspberry pi with Rasbian Lite OS installed. It's much cheaper than an EC2 instance. But I guess AWS offers one free T3 micro instance (720 h of compute time per month) per AWS account.
- Control over your router. This is optional if you're really looking to code outside of your home and not just from bed next to your spouse.
- A spouse/family you would do anything to protect, even set up a sub-optimal method of coding on yout phone.

## General Idea

The basic idea is to use the Termux smartphone app to SSH into into your Raspberry Pi (RPI). The RPI will do the bulk of the computing and development using a text-based editor like emacs.

### Why Termux

There are other alternatives, some free, some expensive, but I used Termux in the past and it's still updated and it seems to be very popular still.

### Why Emacs

Because I hate myself. And because I think Emacs is more approachable than Vim. Don't get too wrapped up in syncing your emacs settings across devices. I recommend setting up Emacs prelude with Emacs classic on your RPI. Install emacs using the snap store. You can keep the editor on Termux pretty barebones. You shouldn't be doing much development on your phone anyways because handling dependencies on a Linux emulation on your smartphone is not worth it.

### Coding From Anywhere

If you truly want to code from anywhere with cell reception, you'll want to set up port forwarding to your RPI on your router. When you open up your SSH port on your RPI, consider setting up UFW with a limit on SSH connections. If you want to be extra secure, you could change the default port that you use for SSH to be something else.

## Tips

- Turn off auto-rotate feature on your phone. Rotating your screen while you have a file open causes emacs to error out in Termux.
