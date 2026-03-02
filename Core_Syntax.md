# C++ Core Syntax & Fundamentals

When you blank on exact syntax during problem-solving. 

## Type Limits and Infinity

When you need an initial "infinity" value for `min` or `max` operations.
_Requires `#include <climits>`_

- **Integer Extremes:**
  ```cpp
  int max_val = INT_MAX; // Use for finding minimums
  int min_val = INT_MIN; // Use for finding maximums
  ```

- **Long Long Extremes:**
  ```cpp
  long long max_ll = LLONG_MAX;
  long long min_ll = LLONG_MIN;
  ```

- **Alternative (Using `<limits>`):**
  ```cpp
  numeric_limits<int>::max();
  numeric_limits<long long>::min();
  ```

## Custom Sorting (Comparators)

If you need to sort structured data logically (e.g., pairs, structs) instead of standard ascending order.

- **Sorting an Array of Pairs by the Second Element:**
  Pass a lambda function that returns `true` if `a` should come before `b`.
  ```cpp
  vector<pair<int, int>> v = {{1, 5}, {2, 3}, {3, 8}};
  
  sort(v.begin(), v.end(), [](const pair<int,int>& a, const pair<int,int>& b) {
      return a.second < b.second; // Ascending order by second element
  });
  ```

- **Sorting Strings by Length:**
  ```cpp
  sort(words.begin(), words.end(), [](const string& a, const string& b) {
      return a.length() < b.length();
  });
  ```

## For Loops 

- **Range-Based `for` loop (by value):**
  ```cpp
  for (int x : arr) { ... } // Creates a copy
  ```

- **Range-Based `for` loop (by reference):**
  Use this to modify the original elements or to prevent copying heavy objects (like strings or vectors).
  ```cpp
  for (auto& x : arr) { // Modifies original
      x *= 2; 
  }
  ```
