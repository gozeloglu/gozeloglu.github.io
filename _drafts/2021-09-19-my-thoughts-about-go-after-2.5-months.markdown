---
layout: post
title: My Thoughts About Go After 2,5 Months
author: Gökhan Özeloğlu
date: 2021-09-19 22:08:09 +0300
categories: general
tags: [go]
permalink: /:categories/go
---

I've been writing Go for 2,5 months. I started to write Go with my new job. After leaving my part-time job, I've started to a new company, SabancıDx, as a software engineer. In this company, I involved a newly started project which is being written in Go. 

### How I learned?

I firstly completed [Go Tour](https://tour.golang.org/welcome/1). In my opinion, Go Tour is the best starting point of learning Go. It starts with basics like initializing variables, loops, conditions, functions, and goes until concurrency. Actually, I did not complete the concurrency part because it was not so much necessary for me to start to the Go. Then, I started to write some code for the project. Firstly, I tried to write a TCP-server by using [`net`](https://pkg.go.dev/net) package. After that I started to take tasks and complete them. While writing code and trying something that I learned, I kept reading blog posts, documentations, reading code, reading Go packages, and source code. I tried to understand what are the best practices, what other developers do, how them define variables, functions and lots of other things related to Go. 

#### Writing package 

Always I have a plan to write a client package to support open source and improve my coding skills. I started to write [GOP3](https://github.com/gozeloglu/gop-3) package towards the end of August. It is POP3 client package for Go. It stands for Go + POP3. I used [RFC-1939](https://www.ietf.org/rfc/rfc1939.txt) document as a reference while developing client package. RFC-1939 specificies the network protocol of the POP3. Writing a package like this helped me to understand basic concepts of Go like `struct type`, `receivers`, `pointers`. I advice to everyone to write a package to learn Go and apply knowledge that learned. You will make mistakes and see your weaknesses about the Go, then, you will fix them. 

### Pros and Cons

Main topic of this article is my thoughts about the Go. Before listing them, in general, I definitely loved Go. Here's the pros:

#### Pros

* Installing Go in your local machine is easy and fast. You download and install binaries and makes it ready for you. 

* Creating a project and starting to write some code is so easy. All you need to do is writing `go mod init <package-name>` and creating a `main.go` file. Then, you can start writing code. 

* **Writing simple code.** Writing code and creating something are so fast. For instance, let's say, you want to create a TCP server, you can create it with ~20 lines. Also, there is no long lines. I jumped to Go from Java and I wrote Java/Spring ~10 months. Creating something was taking more time and I had to write more and long lines. I love simplicity as like in Python and Go. That's why this one is my one of the favorite feature of Go. 

* **Code readability.** Some people can think that understanding Go code is hard because of the Go convention, but I am not agree with that. In general, Go variables, receivers, function parameter names are defined with short names. Of course, you can define with long names but generally Go developers prefer to write short ones. It is not a big problem in my experience so far. Go developers choose meaningful names like `ctx` for `context`, `mu` for `mutex`, `c` for `Client`. In contrast, long names are preferred in Java language and it makes verbose language. I don't like verbose languages. I get lost while reading code and struggle to understand code. We are not reading novel, we are reading code :) 

* Non-verbose language

* Close to network 

* Installing Go packages

* Releasing package

* Go community

* IDE