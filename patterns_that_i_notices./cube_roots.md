# Binary Bit-Matching Patterns in Perfect Cubes ($n \in [2, 9]$)

## 1. The Hypothesis
While analyzing the binary representations of integers and their perfect cubes, I observed a distinct pattern: for single-digit numbers, the binary representation of the root exactly matches either the **most significant bits** (first $m$ bits) or the **least significant bits** (last $m$ bits) of its perfect cube.

## 2. The Data (The Pattern)
The pattern alternates strictly based on whether the root is even or odd:
* **Even Roots:** The root perfectly matches the *first* $m$ bits of the cube.
* **Odd Roots:** The root perfectly matches the *last* $m$ bits of the cube.

Here is the data confirming the pattern for roots 2 through 9:

| Root (Base 10) | Root (Binary) | Cube (Base 10) | Cube (Binary) | Pattern Match |
| :--- | :--- | :--- | :--- | :--- |
| **2** | `10` | 8 | `10 00` | First 2 bits match the root |
| **3** | `11` | 27 | `110 11` | Last 2 bits match the root |
| **4** | `100` | 64 | `100 0000` | First 3 bits match the root |
| **5** | `101` | 125 | `1111 101` | Last 3 bits match the root |
| **6** | `110` | 216 | `110 11000` | First 3 bits match the root |
| **7** | `111` | 343 | `101010 111` | Last 3 bits match the root |
| **8** | `1000` | 512 | `1000 000000` | First 4 bits match the root |
| **9** | `1001` | 729 | `101101 1001` | Last 4 bits match the root |

## 3. The Boundary (Where the Pattern Breaks)
Through further testing, I discovered that this pattern is a mathematical coincidence bounded to single-digit integers. As the numbers grow larger, the arithmetic "carry-over" from binary multiplication permanently alters both the most and least significant bits, breaking the alignment.

The pattern fails starting at the number 10:

* **Root 10:** Binary is `1010` (4 bits)
* **Cube 1000:** Binary is `1111101000`

> **Analysis:** The first 4 bits are `1111` and the last 4 bits are `1000`. Neither matches the root `1010`.

## 4. Conclusion
While this cannot be used as a reliable $O(1)$ algorithm to determine if any given integer is a perfect cube, the observation highlights how base-2 multiplication naturally preserves early bit structures before carry-over operations overwhelm the sequence. It serves as an excellent exercise in bitwise analysis and pattern recognition.
