+++
date = '2025-11-30T14:13:50+08:00'
draft = false
title = 'Internals of Hashmaps'
+++

# Context

Hash tables were invented in 1953 by Hans Peter Luhn at IBM to enable fast lookups in computer memory systems.

A hash table (or hash map) is an ADT implemented using an array. Whilst an element is accessed via an index in an array, a hash table accesses items via a hashed index.

Hash tables solve the problem of retrieving a name/label (not an integer) associated with some value.

Hashing a name/label as a key to some value might unknowingly override the previous value in that slot when collisions occur.

The Pigeonhole Principle mathematically guarantees a collision will occur, hence, a ready collision resolution strategy is necessary.

---

# Main Collision Resolution Types

## Separate Chaining

Stores a linked list at each array index. If a collision occurs, instead of overwriting, we simply append the new key-value pair to the end of the linked list at that given index. This allows multiple entries to be at the same slot.

```python
hash_table[4] = LinkedList([
    ("John", "555-1234"),
    ("Peter", "555-5678"),
])
```

## Open Addressing

Instead of chaining at each slot, open addressing finds another empty slot within the array itself. When a collision occurs, we probe for the next available position.

This keeps all entries in the array, improving cache locality at the cost of more complex insertion logic.

### Linear Probing

Check the next slot sequentially until an empty one is found.

```python
def insert(hash_table, key, value):
    index = hash(key) % len(hash_table)
    while hash_table[index] is not None:
        index = (index + 1) % len(hash_table)
    hash_table[index] = (key, value)
```

The downside is clustering — consecutive filled slots form "clumps" which will slow down future insertions.

When the load factor exceeds ~0.7, the array is resized, then all entries are rehashed to reduce clustering.

### Quadratic Probing

Instead of checking the next slot, we jump by increasing squares: +1, +4, +9, +16...

This spreads entries out more evenly, reducing primary clustering but introducing secondary clustering _(keys with the same hash still follow the same probe sequence)_.

Resizing typically doubles the array to a prime number, ensuring the quadratic sequence can probe all slots.

### Double Hashing

Uses a second hash function to determine the probe step size.

```python
step = second_hash(key)
index = (index + step) % len(hash_table)
```

This eliminates both clustering types since even keys with the same initial hash take different probe paths.

---

# Summary

Hash Table = Array + Hash Function + Collision Resolution + Resizing Logic
