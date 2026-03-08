# Sliding Window on Doubled Array for Circular Rotations

When a problem allows you to take elements from the front of an array and move them to the back (cyclic shifts/rotations), simulating this naively can lead to $O(N^2)$ time complexity. 

The most elegant way to handle string rotations is by **doubling the string** (`s = s + s`) and using a fixed-size **Sliding Window**.

## Where I Got Stuck

When dealing with the "Type-1" operation (moving the first character to the end), I was stuck trying to figure out how to recalculate the number of flips for every possible rotated version of the string without recounting from scratch. Recounting the flips for every possible rotation is a nested loop operation that causes a Time Limit Exceeded (TLE) error.

## The "Aha!" Moment

There are two major realizations that break this problem wide open:
1. **The Target Patterns:** A binary string can only alternate in two ways. Either it starts with `'1'` (`"101010..."`) or it starts with `'0'` (`"010101..."`). We can track the errors/flips needed for *both* patterns simultaneously.
2. **The Cyclic Trick:** By appending the string to itself (`s = s + s`), every possible rotation of `s` is just a contiguous subarray of size `n` within the doubled string. We can slide a window of size `n` across `s + s`, simply adding the error of the new character entering the window and subtracting the error of the character leaving the window.

### Code Example (C++)
```cpp
// LeetCode 1888. Minimum Number of Flips to Make the Binary String Alternating
int minFlips(string s) {
    int n = s.size();
    
    // a -> Flips needed to match pattern '101010...'
    // b -> Flips needed to match pattern '010101...'
    int a = 0; 
    int b = 0; 
    int ans = INT_MAX;

    // Double the string to handle cyclic shifts elegantly
    s = s + s;

    // Slide a window across the doubled string
    for(int i = 0; i < s.size(); i++) {
        // 1. Add current character's error to the window
        if((i & 1) == 0) { // even index
            if(s[i] == '0') a++; else b++;
        } else {           // odd index
            if(s[i] == '0') b++; else a++;
        }

        // 2. Remove the element that falls out of the sliding window of size n
        if(i >= n) {
            int l = i - n; // The index falling out
            if((l & 1) == 0) {
                if(s[l] == '0') a--; else b--;
            } else {
                if(s[l] == '0') b--; else a--;
            }
        }

        // 3. Once window size reaches n, capture minimum flips
        if(i >= (n - 1)) {
            ans = min(ans, min(a, b));
        }
    }
    
    return ans;
}
```

### Complexity
- **Time Complexity:** $O(N)$ since creating `s + s` takes $O(N)$ and sliding the window takes exactly one pass over the $2N$-length string.
- **Space Complexity:** $O(N)$ to store the doubled string (can be optimized to $O(1)$ if you simulate the indices using modulo `% n`).
- **The Core Learning:** "Use `s = s + s` to convert circular string problems into sliding window problems, and use a sliding window to keep track of differences against target patterns dynamically!"
