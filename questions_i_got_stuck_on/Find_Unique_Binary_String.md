# Cantor's Diagonalization

## Where I Got Stuck

I initially struggled to find a way to construct a string that is guaranteed to not be present in the array without resorting to complex generation or nested checking combinations. The core learning that unstuck me was realizing that simply ensuring the $i$-th bit of our new string is different from the $i$-th bit of the $i$-th string solves this elegantly.

When faced with constraints like given $N$ strings of length $N$ (or an $N \times N$ setup) and you're asked to find a string that **is not present** in the given array, a powerful and highly elegant technique is **Cantor's Diagonalization**.

## The \"Aha!\" Moment

To guarantee our new string is not equal to any of the strings in the array, we can ensure that our new string differs from the $i$-th string at the $i$-th character. Since every string in the array will have at least one character difference (at the $i$-th index) from our output string, it's impossible for our string to exist in the array.

- For `nums[0]`, we look at character `0`. If it's `'0'`, we pick `'1'`. If `'1'`, we pick `'0'`. Our string differs from `nums[0]`.
- For `nums[1]`, we look at character `1` and flip it. Our string now differs from `nums[1]`.
- We repeat this for all $n$ characters.

### Code Example (C++)
```cpp
// LeetCode 1980. Find Unique Binary String
string findDifferentBinaryString(vector<string>& nums) {
    int n = nums.size();
    string s = \"\";
    for(int i = 0; i < n; i++) {
        // Flipping the i-th character to guarantee uniqueness
        if(nums[i][i] == '0') {
            s += '1';
        } else {
            s += '0';
        }
    }
    return s;
}
```

### Complexity
- **Time Complexity:** $O(N)$ since we iterate through the $N$ strings exactly once.
- **Space Complexity:** $O(N)$ (the space needed for the output string).
- **The Core Learning:** \"The $i$-th bit should be different.\"
