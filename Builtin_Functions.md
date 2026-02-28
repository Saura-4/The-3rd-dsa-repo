# GCC Built-in Functions

Useful built-in functions available in GCC compilers:

- **Count the number of set bits (1s):**
  ```cpp
  __builtin_popcount(n)
  ```

- **Count leading zeros (before the first set bit):**
  ```cpp
  __builtin_clz(n)
  ```

- **Count trailing zeros (after the last set bit):**
  ```cpp
  __builtin_ctz(n)
  ```

- **Check parity (odd/even number of set bits):**
  ```cpp
  __builtin_parity(n) // Returns 1 if number of set bits is odd, 0 if even
  ```
