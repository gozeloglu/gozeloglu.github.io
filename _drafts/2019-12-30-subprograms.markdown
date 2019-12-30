---
layout: post
title: Subprograms
author: Gökhan Özeloğlu
date: 2019-12-30 12:27:32 +0300
categories: general
permalink: /:categories/subprograms
---

# Introduction

In this article, I am going to explain *subprograms* in programming languages. Subprogram provides some abstraction while building a program. When we write a program, we want to reuse statements in different places and different times. In modern programming language, we collect all statements in a subprogram. It will give us some conveniences like memory space, coding time, and  reusable codes. We call the subprogram from several places in our code blocks and details are hidden by calling only subprogram. Also, this can ensure writing more readable codes. 

# Fundamentals of Subprograms

- Each subprogram has a single entry point.
- The calling program unit is suspended during the execution of the called subprogram, which impiles that there is only one subprogram in execution at any given time.
- Control always returns to the caller when the subprogram execution terminates.

# Definitions

**Subprogram definiton:** Describes the interface to and the actions of the subprogram abstraction. There is a difference in Python subprogram definitions. In Python, function definitions can be executable and when you call the function, it will be executed. Let's look an example.

{% highlight python %}
a = 1

if a > 1:
    def func():
        print("a is bigger than 1")
        print("If block is executing")

else:
    def func():
        print("a is not bigger than 1")
        print("Else block is executing")

func() 
# Else block will be executed
# a is not bigger than 1
# Else block is executing
{% endhighlight python %}

In this example, a is declared as an integer and its value is 1. After the if-else blocks, we call `func()` and program executes **else** block, because *"a is not bigger than 1"*. So, in this case, function declarations was executed and produced output. If we were declared a with bigger than 1, i.e. 9, the program would be executed **if** block and prints out the `a is bigger than 1` `If block is executing` messages. 

{% highlight python %}
a = 1

if a > 1:
    def func():
        print("a is bigger than 1")
        print("If block is executing")

else:
    def func():
        print("a is not bigger than 1")
        print("Else block is executing")

func() 
a = 9
func()
# Else block will be executed in both function calls
{% endhighlight python %}

What would happen if we changed the `a` value. Nothing! Changing the value after the **if-else** blocks, does not affect the execution of **if-else** statements. `a` remains **1**, in this example. So, output of this function is the same for both `func()` calls.

**Subprogram call:** A request to execute specific subprogram. 

{% highlight python %}
def fun(a, b):
    return a + b

...

x = fun(12, 2)  # Subprogram call
{% endhighlight python %}

- A subprogram is **active** if a subprogram is called, started to execution, but have not terminated yet.

**Subprogram header:** The first part of the definition. It includes name of the function and the formal parameters.

`def func(params):` ==> Python header

`int func(params)` ==> C header

In some languages, like Python, JavaScript, Ruby, and so on, the subprogram definitions are indicated with a *special* words, which are **reserved word**. You should start with these kind of *reserved words* when you declare a subprogram. In Python and Ruby, `def` indicates that it is a subprogram, wheares `function` in JavaScript.

The *body of the subprograms* defines the actions. There are several ways of showing body in different languages. In C-based languages, you delimited by using *curly brackets*. In Ruby, `end` statement terminates the body of the subprogram. In Python, indentations play important role. 