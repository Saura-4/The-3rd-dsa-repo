# Array Manipulation (STL)

Useful STL functions for manipulating vectors and arrays.

## Reversing and Filling

- **Reverse elements:**
  ```cpp
  reverse(v.begin(), v.end());
  ```

- **Fill with sequential increasing values:**
  Fills the range starting from `start_val` (e.g., `0, 1, 2, 3, 4...`).
  ```cpp
  iota(v.begin(), v.end(), start_val);
  ```

- **Fill entire container with a value:**
  ```cpp
  fill(v.begin(), v.end(), val);
  ```

## Duplicates and Permutations

- **Unique:**
  Shifts all duplicates to the end and returns an iterator to the new logical end.
  ```cpp
  unique(v.begin(), v.end());
  ```
- **Remove Duplicates (Erase-Unique Idiom):**
  _Note: The array must be sorted first._
  ```cpp
  v.erase(unique(v.begin(), v.end()), v.end());
  ```

- **Next Permutation:**
  Rearranges elements into the next lexicographically greater permutation. Returns `true` if next permutation exists.
  ```cpp
  next_permutation(v.begin(), v.end());
  ```

## Finding Info (Min, Max, Sum, Count)

- **Max and Min Elements:**
  Returns an iterator to the max or min element.
  ```cpp
  max_element(v.begin(), v.end());
  min_element(v.begin(), v.end());
  ```

- **Accumulate (Sum of array):**
  Sums the array. Always use `0LL` instead of `0` for the initial value to avoid overflow.
  ```cpp
  accumulate(v.begin(), v.end(), 0LL);
  ```

- **Count Occurrences:**
  Counts how many times `key` appears in the container.
  ```cpp
  count(v.begin(), v.end(), key);
  ```
