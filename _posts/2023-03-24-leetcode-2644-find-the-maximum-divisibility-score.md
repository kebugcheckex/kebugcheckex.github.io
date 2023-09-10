---
title: LeetCode 2644 Find the Maximum Divisibility Score
layout: post
category: coding
tags:
- leetcode
math: true
---

This problem has a pretty straightforward solution. Don't over-think about math tricks like multiplying all the numbers, etc. The most intuitive solution just works.

<!--more-->

The tricky part is actually the third paragraph of the problem description
> Return the integer `divisors[i]` with the maximum divisibility score. If there is more than one integer with the maximum score, return the minimum of them.

We need two variables to keep track of the current maximum score and the minimum divisor with the maximum score. Here the sample code.

```cpp
class Solution {
public:
    int maxDivScore(vector<int>& nums, vector<int>& divisors) {
        long minDivisor = divisors[0];
        int maxScore = 0;
        for (const auto divisor : divisors) {
            int score = 0;
            for (const auto num : nums) {
                if (num % divisor == 0) {
                    score++;
                }
            }
            if (score > maxScore) {
                maxScore = score;
                minDivisor = divisor;
            } else if (score == maxScore && divisor < minDivisor) {
                minDivisor = divisor;
            }
        }
        return minDivisor;
    }
};
```

Note that without any math tricks, the time complexity is $$O(i*j)$$, where i and j are the length of the two arrays. To optimize for memory (space), you can keep track of the minimum divisor and maximum score on the fly, without storing them in additional arrays.
