# Prefix/Suffix Arrays: Space Optimization & Overflow Avoidance

Sometimes when trying to compute running sums and running products simultaneously, building prefix and suffix arrays uses $O(N)$ extra space, and aggressive multiplication easily runs into integer overflow limits. 

The most elegant and optimal solution is often achieved using **$O(1)$ space with reverse traversal**.

## Where I Got Stuck

When initially solving this, my first approach was directly computing the product, which quickly led to integer overflow limits triggering `cap`. My second approach successfully avoided extreme overflow and computed the right answers, but it relied on building an $O(N)$ Space Suffix Array (`suffProd`), which overcomplicated the memory footprint and logic.

## The \"Aha!\" Moment

Instead of making two passes to generate prefix and suffix arrays, you can:
1. Make a first pass to sum up *all* relevant elements, representing your current boundary condition (e.g., prefix sum at the end, or suffix sum at the beginning).
2. Start iterating backward (or forward, depending on the problem).
3. In each step, **incrementally update** the sum (by subtracting/adding the current element) and **incrementally update** the product, checking the condition *on the fly*.
4. This completely avoids storing bulky prefix/suffix arrays ($O(1)$ space) and often lets us stop early or identify issues before integer limits explode.

### Code Example (C++)
```cpp
// LeetCode 3862. Find the Smallest Balanced Index
int smallestBalancedIndex(vector<int>& nums) {
    long long sum = 0;
    long long prod = 1;
    int n = nums.size();

    // 1. Initial State: Compute total left sum up to n-2
    for(int i = 0; i < n - 1; i++) {
        sum = sum + nums[i];
    }
    
    // Check edge case for the last index
    if(sum == prod) return n - 1;

    // 2. Reverse Traversal: Update in O(1) space
    for(int i = n - 2; i >= 0; i--) {
        sum = sum - nums[i];      // Remove current from left sum
        prod = prod * nums[i+1];  // Add next element to right product
        
        if(sum == prod) {
            return i; 
        } else if (sum < prod) {
            // Because values are >= 1, product grows fast while sum shrinks. 
            // Once product strictly exceeds the sum, it can never balance again.
            break;
        }
    }
    return -1;
}
```

### Complexity
- **Time Complexity:** $O(N)$ single pass forward, and one pass backward.
- **Space Complexity:** $O(1)$ space.
- **The Core Learning:** \"Always look if a $O(N)$ Space Prefix/Suffix array can be reduced to $O(1)$ incremental updates! Also, notice that monotonically growing functions (like running product of positive integers) vs shrinking functions (like shrinking remaining sum) mean you can `break` early to brutally cut off integer overflow risks!\"
