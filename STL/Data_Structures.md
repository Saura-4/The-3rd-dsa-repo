# STL Data Structures

A quick reference guide for initializing and working with essential C++ STL data structures.

## Vectors and Arrays

- **Initialize a 2D Vector with Default Values (`0` initially):**
  This creates a matrix of size `rows` x `cols`.
  ```cpp
  vector<vector<int>> grid(rows, vector<int>(cols, 0));
  ```
- **Copying a Vector:**
  ```cpp
  vector<int> v2 = v1; // Deep copy
  ```
- **Initialize Vector with same values:**
  ```cpp
  vector<int> v(10, -1); // 10 elements initialized to -1
  ```

## Heaps (Priority Queue)

- **Max-Heap (Default):**
  Yields the largest element first.
  ```cpp
  priority_queue<int> pq;
  ```
- **Min-Heap (Frequently Forgotten!):**
  Yields the smallest element first.
  ```cpp
  priority_queue<int, vector<int>, greater<int>> min_pq;
  ```
- **Custom Object Min-Heap:**
  Requires a custom comparator either by overloading `<` or passing a struct.

## Hash Maps & Sets

- **Check if Key Exists (Without Inserting!):**
  Accessing `m[key]` will insert `key` if it doesn't exist (default initialized). Avoid this to prevent map bloat.
  ```cpp
  // Best practice 1:
  if (m.find(key) != m.end()) { ... } 
  
  // Best practice 2:
  if (m.count(key)) { ... } 
  ```

- **Cleanly Iterate a Map:**
  Using structured binding (C++17 and later):
  ```cpp
  for (auto& [key, value] : m) {
      // Access key and value directly
  }
  ```

## Pairs and Tuples
- **Creating Pairs:**
  ```cpp
  pair<int, string> p = make_pair(1, "hello"); // Or just {1, "hello"} in C++11+
  ```
- **Unpacking Tuples / Pairs:**
  ```cpp
  auto [x, y, z] = my_tuple;
  ```
