+++
date = '2025-11-26T21:50:30+08:00'
draft = false
title = 'Abstract Data Structures (ADT) & Implementations'
+++

In software engineering, depending on the nature of the problem, system architecture discussions can take take on different levels, going deeper as more technical details are considered & viewing same things differently.

If you break this down to simpler, constrained topics like data structures, a similar thing occurs. Depending on implementation details, a simple thing like a Binary Tree can take on different abstractions in one's mind.

# 🗒️ Context

To implement a ADT Priority Queue, we can use a Binary Heap. A Binary Heap, is a Binary Tree with a certain ordering constraint.

A Binary Tree can be implemented as either:

- a group of nodes with pointers where each node points to at most 2 other nodes
- an array using implicit indexing

---

# 💡 Insight

Depending on context, the Binary Tree exists in two ontological forms:

## Binary Tree is as an implementation itself

- if defining logical structure & its tree operations _(i.e. traverse, search, delete etc.)_
- when the tree structure solves the problem

## Binary Tree as an ADT

- eg. a Priority Queue is implemented using a Binary Heap _(an array that maintains Binary Tree properties)_

---

# Summary

A Binary Tree simultaneously functions as an ADT (abstracting over pointer vs array
implementations) & as an implementation mechanism (providing structure for Priority
Queue via a Binary Heap).

This dual role illustrates how abstraction is relative depending on context.
