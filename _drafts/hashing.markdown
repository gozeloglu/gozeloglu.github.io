---
layout: post
title:  "Hashing"
author: Gökhan Özeloğlu
date:   2019-12-29 00:00:52 +0300
categories: general
permalink: "/:categories/hashing"
---

In this article, I am going to try explain hashing concept. I hope it helps you and you can find your answers.

# What is hashing?

Hashing is an important data structure that used in computer science. It solves many problems easily. There are some advantages to use it. It basically has a *hash function* which is used for mapping data. It speeds up the inserting, deleting, or removing data from hash table. The hashing performance depends on hash function. If you use a good hash function, you can decrease the collisions and probe number. 

# Real World Example

I want to explain hashing concept by given an example. Let's say, you have a database which includes information about students, lectures, and teachers. Your goal is holding these all informations as possible as *efficiently*. What I mean by *efficiently*? **Efficiency** means that making some operations on data fast and reliable by obstructing any unexpected situations. You should retrieve some special or all data, updating data fastly. The best scenario to reach data is accessing at the first time. We call **O(1)** in terms of algorithmic complexity. It means that we access the target value at the first or a few times. We can ignore 2, 3, or 4 times, if we have a big data. 