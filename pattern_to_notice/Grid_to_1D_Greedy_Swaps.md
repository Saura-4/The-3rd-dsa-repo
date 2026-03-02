# Grid to 1D + Greedy Adjacent Swaps

Often, a problem asks you to rearrange rows in a 2D grid to satisfy a specific condition using **only adjacent row swaps**.
Instead of simulating the swaps directly on the 2D grid (which requires `O(N^3)` time), it is much more efficient to **convert the grid into a 1D array of integers** representing the required metric for each row.

## The Pattern

1. **Convert to 1D Array**: Identify the core metric that determines if a row is valid at a certain position. For example, the number of trailing zeros, or the first occurrence of a '1'. Compute this metric for every row and store it in a 1D array.
2. **Greedy Match**: Iterate through the required positions `i = 0` to `n-1`. For each position, find the first available row `j >= i` that satisfies the condition for position `i`.
3. **Bubble Up**: Once the row `j` is found, simulate the adjacent swaps by swapping the element at index `j` backwards until it reaches index `i`. Add the number of swaps to your total count.

### Code Example (C++)
```cpp
// LeetCode 1536. Minimum Swaps to Arrange a Binary Grid
int minSwaps(vector<vector<int>>& grid) {
    int n = grid.size();
    vector<int> trailing_zeros;
    
    // 1. Convert Grid to 1D array of trailing zeros metrics
    for(int i = 0; i < n; i++) {
        int cnt = 0;
        for(int j = n - 1; j >= 0; j--) {
            if(grid[i][j] == 0) cnt++;
            else break;
        }
        trailing_zeros.push_back(cnt);
    }
    
    int ans = 0;
    
    // 2. Greedy Match & Bubble Up
    for(int i = 0; i < n; i++) {
        int j = i;
        // Require at least (n - i - 1) trailing zeros
        while(j < n && trailing_zeros[j] < (n - i - 1)) {
            j++;
        }
        
        // If no row satisfies the condition, grid cannot be valid
        if(j == n) return -1;
        
        // 3. Bubble up the valid row to position i
        int a = j;
        while(a != i) {
            swap(trailing_zeros[a], trailing_zeros[a-1]);
            ans++;
            a--;
        }
    }
    
    return ans;
}
```

### Complexity
- **Time Complexity:** `O(N^2)` because constructing the 1D array takes `O(N^2)` and the nested while loop for bubbling up also takes worst-case `O(N^2)`.
- **Space Complexity:** `O(N)` for the 1D array to store the metrics, which avoids repeatedly scanning the entire Grid.
