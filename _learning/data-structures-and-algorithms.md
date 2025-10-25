---
layout: learning
title: "Data Structures and Algorithms"
status: "In Progress"
description: "Notes for Data Structures and Algorithms with visualized diagrams and C++ examples and leetcode solutions."
---

# Welcome :)

I decided to study Data Structures and Algorithms and make some notes for the future,
after some time I forgot most of the stuff so this time I make notes and also I will
solve leetcode problems so it will be also nice place to showcase my code.
I will link all the solutions in seperate files in separate directory, however pseudo-code will
be provided here with all of the visualizations also made by me.

# Problems list to cover

- [ ] [`easy` Two Sum](https://leetcode.com/problems/two-sum/description/)
- [ ] [`medium` Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
- [ ] [`easy` Is Subsequence](https://leetcode.com/problems/is-subsequence/description/)
- [ ] [`medium` Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/)

# Problems solutions:

## Two Pointers

### `Reverse string`:

```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
        
        int i = 0;
        int j = s.size() - 1;
        
        while(i < j) {
            s[i] = s[i] ^ s[j];
            s[j] = s[i] ^ s[j];
            s[i] = s[i] ^ s[j];
            i++;
            j--;
        }
    }
};
```