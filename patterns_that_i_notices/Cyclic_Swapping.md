# Cyclic Swapping 

When performing operations like rotating a matrix (e.g., by 90 degrees) or doing certain array transformations, you can often interchange values **in-place** (without needing extra memory or a secondary matrix) by swapping elements in a **cycle**.

## The Pattern

Instead of moving elements one at a time to a new matrix/array, you group elements into cycles that represent their movement path, and then swap them sequentially. 

For example, to rotate a point `(i, j)` in an `N x N` matrix by 90 degrees clockwise, 4 elements form a cyclical group. By rotating them step-by-step, we place all 4 elements in their correct target positions while only requiring `O(1)` extra space for a temporary variable.

1. **Save** the top element.
2. **Move** left to top.
3. **Move** bottom to left.
4. **Move** right to bottom.
5. **Move** the saved top element to right.

### Code Example (C++)
```cpp
// Rotating an N x N matrix by 90 degrees clockwise in-place
int n = matrix.size();

// Iterate through the loops
for (int i = 0; i < n / 2; i++) {
    for (int j = i; j < n - i - 1; j++) {
        // 1. Save the top element
        int temp = matrix[i][j];
        
        // 2. Move left to top
        matrix[i][j] = matrix[n - 1 - j][i];
        
        // 3. Move bottom to left
        matrix[n - 1 - j][i] = matrix[n - 1 - i][n - 1 - j];
        
        // 4. Move right to bottom
        matrix[n - 1 - i][n - 1 - j] = matrix[j][n - 1 - i];
        
        // 5. Move saved top to right
        matrix[j][n - 1 - i] = temp;
    }
}
```

This pattern is extremely useful for reducing space complexity from `O(N^2)` to `O(1)`.
