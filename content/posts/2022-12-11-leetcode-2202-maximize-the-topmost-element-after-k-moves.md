---
title: LeetCode 2202 Maximize the Topmost Element After K Moves
layout: post
category: coding
math: true
tags:
- leetcode
---

This is an interesting question. Upon first look, it seems to be a stack-related question, as the operation of moving stuff from a pile resembles a stack data structure. However, it actually has nothing to do with stacks.

<!--more-->

Let's use our intuition to think about how to get the max element on the top. Ideally, we want to find the element with max value and remove everything above it. However, we have to make exact _k_ moves. There are three cases:
1. _k_ is smaller than the max value's index. This means that we won't be able to reach this element before exhausting the moves.
2. _k_ is equal to the max value's index. This is the ideal case where removing _k_ elements just make the max value on the top.
3. _k_ is larger than max value's index. This case requires further investigation as we need to figure out how to consume the remaining moves and make sure the max value is still on the top.

Let's talk about the third case above. Let __i_ be the index of the max value.
1. **k - i = 1** This means we have one extra step after exposing the max value. Unfortunately either moving away the top element or putting back another element will destroy our success.
2. **k - i = 2** In this case we can just remove the top element and put it back.
3. **k - i = 3** In this case we can remove two elements and put the max element back on top.
4. **k - i > 3** With more than 3 moves remaining, we can combine the second and third case here to achieve the goal. For example, if k - i = 7, we can treat it as 2+2+3, which will make sure the max element remains on the top after all moves are done.

So, what if the max element cannot be achieved? Just find the second largest element, the third largest element, until all elements are tested.

Note that if there is only one element, we need to handle it slightly differently. In this case, when _k_  is an even number, we can remove and put back that element many times and end up with that single element still on the pile. Otherwise the pile will be empty after an odd number of moves.

A sample code in C++ is shown below.
```cpp
class Solution {
public:
    int maximumTop(vector<int>& nums, int k) {
        if (nums.size() == 1) {
            return k % 2 == 1 ? -1 : nums[0];
        }
        int maxValue = numeric_limits<int>::min();
        for (int i = 0; i < nums.size(); i++) {
            if (i > k) {
                break;
            } else if (k - i == 1) {
                continue;
            } else {
                if (nums[i] > maxValue) {
                    maxValue = nums[i];
                }
            }
        }
        return maxValue >= 0 ? maxValue : -1;
    }
};
```
