# Searching and Sorting (STL)

Common STL algorithms for finding and arranging elements.

## Sorting

- **Sort in ascending order (Time Complexity: `O(N log N)`):**
  ```cpp
  sort(v.begin(), v.end());
  ```

- **Stable sort (Time Complexity: `O(N log N)`):**
  Preserves relative order of equal values, usually when sorting by multiple keys.
  ```cpp
  stable_sort(v.begin(), v.end());
  ```

## Binary Search

- **Check if element exists (Time Complexity: `O(log N)`):**
  _Note: The array must be sorted first._
  ```cpp
  binary_search(v.begin(), v.end(), key); // Returns true/false
  ```

## Bounds (Lower and Upper)
_Note: The array must be sorted first._

- **Lower Bound:**
  Returns an iterator to the first element that is **greater than or equal to** (`>=`) the key, tracking where a value can start.
  ```cpp
  lower_bound(v.begin(), v.end(), key);
  ```

- **Upper Bound:**
  Returns an iterator to the first element that is **strictly greater than** (`>`) the key, tracking where a value must end.
  ```cpp
  upper_bound(v.begin(), v.end(), key);
  ```

### Example: Counting Occurrences
You can efficiently count the numeric occurrences of a specific `key` in a sorted array using these bounds:
```cpp
vector<int> v = {1, 2, 2, 2, 4, 5};
int key = 2;
int count = upper_bound(v.begin(), v.end(), key) - lower_bound(v.begin(), v.end(), key);
// count will be 3
```
