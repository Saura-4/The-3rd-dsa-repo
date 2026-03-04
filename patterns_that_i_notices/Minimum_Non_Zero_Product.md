# Minimum Non-Zero Product & Cost Splitting

**Observation:**
Whenever a problem asks for the **minimum non-zero product** or **minimum cost to split/reduce elements** (where cost is an arithmetic operation like multiplication), our first thought should be to try and make one of the numbers as `1` (or as small as possible) and keep the other numbers as large as possible. 

This relates to the mathematical property that to minimize `A * B` for a fixed sum `A + B = X`, we should make the difference between `A` and `B` as large as possible (e.g., `1` and `X - 1`).

---

## 1. 1969. Minimum Non-Zero Product of the Array Elements

**Approach:**
In this problem, we swap bits between pairs of numbers. To minimize the product, we make as many numbers as possible equal to `1`, and their corresponding paired numbers will become `(2^p - 2)`. The largest number `(2^p - 1)` remains untouched.

**Code:**
```cpp
class Solution {
public:
    long long mod = 1e9 + 7;
    
    long long power(long long base, long long exp) {
        if (exp == 0) return 1;
        if (exp == 1) return base % mod;

        long long half = power(base, exp / 2);

        if ((exp & 1) == 0) return (half * half) % mod;
        else return ((base % mod) * ((half * half) % mod)) % mod;
    }
    
    int minNonZeroProduct(int p) {
        // (2^p - 1) * (2^p - 2)^(2^(p-1) - 1)
        long long last = (1LL << p) - 1;
        long long sl = last - 1;
        long long sp = (1LL << (p - 1)) - 1;

        long long a = power(sl % mod, sp);
        long long ans = (last % mod) * a % mod;

        return (int)ans;
    }
};
```

---

## 2. 3857. Minimum Cost to Split into Ones

**Problem Summary:**
You are given an integer `n`. In one operation, you split an integer `x` into two positive integers `a` and `b` such that `a + b = x`. The cost is `a * b`. Find the minimum total cost to split `n` into `n` ones.

**Approach:**
Following the same logic, to minimize the cost `a * b` at each step, we should make one of the parts as small as possible, which is `1`. This means we split `n` into `1` and `n - 1` at each step. 
This forms an arithmetic progression of costs: `1 * (n - 1) + 1 * (n - 2) + ... + 1 * 1`, which sums up to `n * (n - 1) / 2`.

**Code:**
```cpp
class Solution {
public:
    int minCost(int n) {
        return (n * (n - 1)) / 2;
    }
};
```
