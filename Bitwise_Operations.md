# Bitwise Operations

Here are some common and useful bitwise operations:

- **Check if integer is odd/even:**
  ```cpp
  n & 1 // Returns 1 if odd, 0 if even
  ```

- **Left and Right Shifts (Multiply/Divide by 2):**
  ```cpp
  n << 1 // Multiply by 2
  n >> 1 // Divide by 2
  ```

- **Check if a number is a power of 2:**
  ```cpp
  (n > 0 && (n & (n - 1)) == 0)
  ```

- **Isolate the rightmost 1-bit:**
  ```cpp
  n & (-n)
  ```

- **Clear the rightmost 1-bit:**
  ```cpp
  n & (n - 1)
  ```

- **Toggle the `i`-th bit:**
  ```cpp
  n = n ^ (1 << i)
  ```

- **Check if the `i`-th bit is set:**
  ```cpp
  if (n & (1 << i))
  ```
