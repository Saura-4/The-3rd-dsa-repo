# DSA Notes and Concepts

Welcome to my collection of Data Structures and Algorithms (DSA) notes. This repository is structured to provide quick, easy-to-understand reference material for revising concepts and solving coding problems efficiently.

## 🗂️ Table of Contents

### 1. Core Concepts (Root)
* [**C++ Core Syntax & Fundamentals**](Core_Syntax.md)
  A survival guide for commonly forgotten syntax: custom sort comparators, `<climits>` (infinity values), and range-based loops.
* [**Bitwise Operations**](Bitwise_Operations.md)
  Contains common tricks and techniques for manipulating individual bits in integers (e.g., checking powers of 2, isolating bits).
* [**GCC Built-in Functions**](Builtin_Functions.md)
  A reference for highly optimized GCC compiler built-ins (like counting set bits, leading zeros, parity checks).
* [**Strings and Numbers**](Strings_and_Numbers.md)
  Quick guides for converting between strings, integers, reversing strings, handling substrings (`s.substr(pos, len)`), and character traits.

### 2. Standard Template Library (`STL/`)
* [**Data Structures Reference**](STL/Data_Structures.md)
  The cheat sheet for initializing tricky structures like 2D-vectors, Min-Heaps (`priority_queue<int, vector<int>, greater<int>>`), and cleanly iterating hash maps.
* [**Array Manipulation**](STL/Array_Manipulation.md)
  Vector operations, reversing, filling (`iota`), finding unique elements, and next permutations.
* [**Math and Number Theory**](STL/Math_and_Number_Theory.md)
  Arithmetic operations, GCD/LCM, and rounding utilities (`ceil`, `floor`, `round`).
* [**Searching and Sorting**](STL/Searching_and_Sorting.md)
  Binary search, bounds (`lower_bound`, `upper_bound`), and stable sorting algorithms.

### 3. Patterns & Observations (`patterns_that_i_notices/`)
* [**Cube Roots**](patterns_that_i_notices/cube_roots.md)
  _Note: This section contains specific math patterns and observations around cube roots noticed during problem-solving._
* [**Cyclic Swapping**](patterns_that_i_notices/Cyclic_Swapping.md)
  _Note: A cool pattern to rotate a matrix or perform array manipulations in-place._
* [**Grid to 1D Greedy Swaps**](patterns_that_i_notices/Grid_to_1D_Greedy_Swaps.md)
  _Note: A technique to convert 2D grid criteria into a 1D array to optimize adjacent swaps from O(N^3) to O(N^2)._
* [**Minimum Non-Zero Product**](patterns_that_i_notices/Minimum_Non_Zero_Product.md)
  _Note: A pattern for minimizing product or cost when splitting/reducing elements, usually by making one component as small as possible (e.g., 1)._

### 4. Questions I Got Stuck On (`questions_i_got_stuck_on/`)
* [**Find Unique Binary String (Cantor's Diagonalization)**](questions_i_got_stuck_on/Find_Unique_Binary_String.md)
  _Note: The $i$-th bit should be different to construct a string not present in the array._
* [**Find the Smallest Balanced Index (Prefix/Suffix Arrays: Space Optimization & Overflow Avoidance)**](questions_i_got_stuck_on/Find_Smallest_Balanced_Index.md)
  _Note: Opt for $O(1)$ space with reverse traversal over bulky $O(N)$ prefix/suffix arrays. Break early when monotonic functions (like running product vs shrinking sum) cross, mitigating integer overflow risks._
* [**Minimum Flips to Make Alternating (Sliding Window on Doubled Array)**](questions_i_got_stuck_on/Minimum_Flips_Alternating_String.md)
  _Note: Double the string `s = s + s` to convert circular shifts into a sliding window problem, dynamically tracking errors against target patterns._
* [**Minimum K to Reduce Array Within Limit (Binary Search on Answer)**](questions_i_got_stuck_on/Minimum_K_to_Reduce_Array.md)
  _Note: Avoid precision issues and integer overflow during binary search checks by using manual ceiling division `(a + b - 1) / b` and proper `1LL` and `(long long)` casting._

---
_Feel free to explore the topics above to aid in your DSA journey!_
