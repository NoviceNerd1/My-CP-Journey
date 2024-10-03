# String Hashing

String hashing is a technique that allows you to convert strings into integer values (hashes) so that you can compare those integer values instead of the strings themselves. This method can significantly improve the efficiency of string comparisons, allowing them to be performed in constant time **O(1)**.

## Why Use Hashing?

1. **Efficiency**: The brute-force method of comparing two strings has a time complexity of **O(min(n1, n2))**, where **n1** and **n2** are the lengths of the two strings. Hashing allows you to compare strings in constant time **O(1)** after their hashes have been computed.
2. **Fixed-Length Comparison**: Comparing integers (hash values) is much faster than comparing potentially lengthy strings, especially when dealing with large datasets.

## How Does String Hashing Work?

1. **Hash Function**: A hash function maps strings to integers. The goal of a good hash function is:
   - If two strings **s** and **t** are equal, their hashes must also be equal: **hash(s) = hash(t) ⟹ s = t**.
   - If the hashes are equal, it does not guarantee that the strings are equal: **hash(s) = hash(t) ⇏ s = t**.
   
   This means that different strings can produce the same hash value, which is known as a collision.
   
2. **Collisions**: Collisions are an inherent issue with hashing. Since there are exponentially many possible strings, it's not feasible to have a unique hash for every string within a limited range (e.g., **[0, m)**). Therefore, hash functions are designed to minimize the probability of collisions.

## Characteristics of a Good Hash Function

- **Deterministic**: The same input string must always yield the same hash value.
- **Uniform Distribution**: The hash function should distribute hash values uniformly across the available range to minimize collisions.
- **Efficient Computation**: The hash function should compute the hash value quickly, ideally in linear time relative to the length of the string.

## Example Hash Function

A common way to define a hash function for strings is using a polynomial rolling hash function. Here’s a simple representation:
hash(s) = (s[0] * p^0 + s[1] * p^1 + s[2] * p^2 + ... + s[n−1] * p^(n−1)) mod m


Where:
- **s[i]** is the i-th character of the string, typically converted to an integer (e.g., ASCII value).
- **p** is a prime number (e.g., 31).
- **m** is the modulus to ensure the hash value falls within a specific range.

## Techniques to Minimize Collisions

1. **Choosing a Good Hash Function**: Use well-known hash functions that have been tested for performance and collision resistance.
2. **Resizing Hash Tables**: When using a hash table, resize the table when the load factor exceeds a certain threshold to keep the number of collisions low.
3. **Using Multiple Hash Functions**: When collisions occur, using more than one hash function can help verify the uniqueness of a hash.

## Applications of String Hashing

1. **Substring Search**: Efficiently search for substrings within a string using hashes.
2. **Data Deduplication**: Quickly identify duplicate entries by comparing hash values.
3. **Hash Tables**: Implementing hash tables for efficient data storage and retrieval.

## Conclusion

String hashing provides a powerful way to efficiently compare strings by mapping them to integers. While it introduces the possibility of collisions, good hash functions and techniques can help minimize this issue, making hashing a practical approach for many applications in computer science.
