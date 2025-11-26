+++
date = '2025-11-26T21:50:30+08:00'
draft = true
title = 'Abstract Data Structures (ADT) & Implementations'
+++

To implement a ADT Priority Queue, we can use a Binary Heap.

A Binary Heap, is a Binary Tree with a certain ordering constraint.

A Binary Tree can be represented as:

- group of nodes with pointers where by each node points to at most 2 other nodes.
- an array using implicit indexing

The insight here is that depending on context, the Binary Tree exists in two ontological:

1. Binary Tree as an implementation itself

- defining logical structure & its tree operations (i.e. traverse, search, delete etc.)
- when the tree structure solves the problem

2. Binary Tree as an ADT

- eg.a Priority Queue is implemented using a Binary Heap (an array that maintains Binary Tree properties)
