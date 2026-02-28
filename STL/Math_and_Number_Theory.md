# Math and Number Theory

Useful math and number theory operations available in C++.

## Basic Arithmetic

- **Absolute Value:**
  ```cpp
  abs(x)
  ```
- **Power:**
  ```cpp
  pow(base, exp)
  ```

## Greatest Common Divisor and Least Common Multiple

- **GCD:**
  ```cpp
  gcd(a, b) // Included in <numeric> (C++17 onwards)
  ```

- **LCM:**
  Returns the least common multiple. Also available natively, but to compute manually without overflow:
  ```cpp
  lcm(a, b) // Included in <numeric> (C++17 onwards)
  
  // Manual, overflow-preventing formula:
  (a / gcd(a, b)) * b;
  ```

## Rounding Utilities

- **Ceiling:**
  Returns the smallest integer `>= x`.
  - `ceil(3.2)` -> `4`
  - `ceil(-3.2)` -> `-3`
  ```cpp
  ceil(x)
  ```

- **Floor:**
  Returns the largest integer `<= x`.
  - `floor(3.8)` -> `3`
  - `floor(-3.2)` -> `-4`
  ```cpp
  floor(x)
  ```

- **Round:**
  Returns the nearest integer to `x`. For values ending in `.5`, rounds away from zero.
  - `round(3.5)` -> `4`
  - `round(-3.5)` -> `-4`
  - `round(2.4)` -> `2`
  ```cpp
  round(x)
  ```
