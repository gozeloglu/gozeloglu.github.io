---
layout: post
title: 30 Days of LeetCoding Challenge Journey - April 2020
author: Gökhan Özeloğlu
date: 2020-04-02 19:24:43 +0300
categories: general
tags: [interview, leetcode, challange]
permalink: /:categories/30-days-of-leetcoding-challange
---

Hi! I have not been written any post in my blog for a while. So, I decided to publish [30-day LeetCode Challenge](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/) solutions day-by-day. I am going to update this post everyday until end of the challenge. I will give my solution as a Python code and my solution in textual way. Maybe you will find more efficient solution in terms of space and time complexity, you can contact with me. In some question, I can learn better solution after I solved the question. In this case, I can share better solution(s) with my solution. 


## Day 1 - Single Number
*Here is the question link : [Week #1 - Single Number](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3283/)*

First day challenge was easy to understand and solve it. It says that there is an array which has integer numbers and every element appears in twice except for one. We should have found out this number. I firstly sorted and started to traversing array. At each step, I compared two integers. So, I defined two variables for comparision. I incremented `i` and `j` by 2, because each numbers are twice except one number. So, I need to compare pairs. I left my code below. You can look at my Python code. 


{% highlight python %}
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        nums.sort()
        i, j = 0, 1
        
        while i < len(nums):
            if j == len(nums):
                return nums[i]
            elif nums[j] != nums[i]:
                return nums[i]
            
            i += 2
            j += 2
{% endhighlight python %}

## Day 2 - Happy Number
*Here is the question link : [Week #1 - Happy Number](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3284/)*

This question has a trick to solve easily. The question says that there is a happy number which is defined by following process: *tarting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.* So, there can be two different situations. The first one is we can reach the 1 by applying happy number process. The second one is we cannot reach the 1 and we go through the *infinite loop*. Actually, we need to prevent this infinite loop. So, I keep the all numbers which is the result of each step and compare the new ones with previous results. If our result is already occuring in our previous numbers, we do not need to continue happy number process. We can cut the operation and return `False`. Otherwise, we continue our process, reach 1, and return `True`. I used `set` to store previous results. I left my Python solution below.

{% highlight python %}
class Solution:
    def isHappy(self, n: int) -> bool:
        number_set = set()
        is_repeated = False
        
        while True:
            tmp_num = list(str(n))
            tmp_num = list(map(int, tmp_num))
            result = 0
            for num in tmp_num:
                result += num**2
            n = result
            if result in number_set:
                return False
            elif result == 1:
                return True
            else:
                number_set.add(result)
{% endhighlight python %}

## Day 3 - Maximum Subarray

*Here is the question link : [Week #1 - Maximum Subarray](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3285/)*

Actually, I learned that this question is a popular interview and computer science question. There are several methods. One of the most popular one is **Kadane's algorithm**. There are lots of different resources on the internet. You can look at them by just typing the question name. Anyway, question explanation is simple. We should find the maximum subarray in given array and return the sum of the subarray. Subarray should be created with contiguous elements. There can be three different scenarios. The first scenario is all elements can be positive, so we can sum all elements and reach the maximum subarray. The second scenario is all elements can be non-positive and maximum subarray will be the meximum element of the array. In the first scenario, maximum subarray consists of all elements, but in the second scenario, maximum subarray consists of the maximum element of the array. The last scenario is our main concern. We basically traverse the array and add elements at each step. After adding the element, we should make comparision to decide maximum one. We update the maximum results if it is necessary. I left the solution below. 

{% highlight python %}
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        a, ans = 0, float('-inf')
        for num in nums:
            a += num
            ans = max(ans, a)
            a = max(0, a)

        return ans
{% endhighlight python %}

## Day 4 - Move Zeroes

*Here is the question link : [Week #1 - Move Zeroes](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3286/)*

This question requires that we need to do operations **in-place**. *In-place* means that extra array should not be used and every operation do in given array. So, we do not need to return any array. The question asks that all zero elements should be moved to end of the array with relative order of the non-zero elements. For example, the array is `[4,1,0,4,5,0,3]`. So, in this case, our result array should be `[4,1,4,5,3,0,0]`. In my approach, I keep 2 different pointers(`i` and `j` in my code) to traverse and swap. `i` is being used for traverseing the array and it is being updated in every iteration. `j` is being used for swapping two elements and it is being updated when two numbers are swapped. Swap condition is occurred when current element is not zero. For example, if I execute my code with above example, the steps are being like this.

{% highlight C %}
i = 0, j = 0 --> [4,1,0,4,5,0,3] --> i = 1, j = 1 
i = 1, j = 1 --> [4,1,0,4,5,0,3] --> i = 2, j = 2 
i = 2, j = 2 --> [4,1,0,4,5,0,3] --> i = 3, j = 2 
i = 3, j = 2 --> [4,1,4,0,5,0,3] --> i = 4, j = 3 (First swap with zero) 
i = 4, j = 3 --> [4,1,4,5,0,0,3] --> i = 5, j = 4 (Second swap with zero) 
i = 5, j = 4 --> [4,1,4,5,0,0,3] --> i = 6, j = 4 
i = 6, j = 4 --> [4,1,4,5,3,0,0] --> i = 7, j = 5 (Third swap with zero) 
{% endhighlight C %}

{% highlight python %}
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        j = 0
        
        for i in range(len(nums)):    
            if nums[i] != 0:
                nums[i], nums[j] = nums[j], nums[i]
                j += 1       
{% endhighlight python %}

## Day 5 - Best Time to Buy and Sell Stock II

*Here is the question link : [Week #1 - Best Time to Buy and Sell Stock II](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3287/)*

My code may be seen a little bit compilcated but I am going to explain each of them. There are some more clear and short codes in terms of *dynamic programming* and you can find them on the internet. Anyway, I am going with my solution. Firstly, I want to summarize question. The question says that you have an array and it represents the price of the stock. And you are trying to find maximum profit by using these prices. There is one note and it says that you are not allowed to multiple transactions, so you firstly need to sell stock and buy new one. You cannot buy stock without selling it. There can be 3 different situations in this question. The first scenario is array can be sorted increasingly and you buy a new stock at the first and you will sell it at the end. Because the cheapiest stock is in the beginning of the array and the most expensive one is in the end of the array. The second scenario is array can be sorted decreasingly. So, if you buy a stock in anywhere of the array, you will loose. Because you cannot sell with profit. So, the answer will be zero. The third scenario is unordered situation. 

My approach is keeping purchase price and looking for the local maximum price with comparing at each step. If I can sell the product with maximum price, I will buy a new minimum stock and, again, looking for new local maximum price. I used two pointers(`i` and `j`). `j` is used for traversing the array and `i` is used for keeping the minimum price.
{% highlight python%}
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        i, j = 0, 0
        
        # Edge case control
        if len(prices) == 0:
            return 0
        
        while j < len(prices)-1:
            if prices[i+1] < prices[i]:
                i += 1
                j = i
                continue
            if prices[j+1] < prices[j]:
                profit += (prices[j] - prices[i])
                i = j + 1
                
            j += 1
        
        # 2 different situations.
        # 1- If array is sorted increasingly
        # 2- To compare the last element
        if prices[j] >= prices[j-1]:
            profit += (prices[j] - prices[i])

        return profit
{% endhighlight python %}

## Day 6 - Group Anagrams 

*Here is the question link : [Week #1 - Group Anagrams](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3288/*)

This question is about anagram. *An anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.* says in [Wikipedia](https://en.wikipedia.org/wiki/Anagram). The question says that we need to make group of strings in terms of anagram. To solve this problem, we need count of the each letter. So, I stored the letters count in array which size is 26 because of the English alphabet. I defined zero for each letter, initially. Then, I incremented by one at each step. Then, I converted to string my list to make comparision. I stored strings and count string in `dictionary`(`map` in other programming languages). Actually, I could use other data structures like list or set, but it would not be efficient in terms of searching. We can search the string in $O(n)$ complexity. But, in *dictionary*, string search can be done in $O(1)$. At the final step, I've just transferred the groups in the *list*. 

{% highlight python %}
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        map_ = dict()
        
        for s in strs:
            count_list = [0]*26
            for i in s:
                count_list[ord(i) - ord('a')] += 1
            
            count_list = "".join(list(map(str, count_list)))
            if count_list not in map_:
                map_[count_list] = [s]
            else:
                map_[count_list].append(s)
                
        result = []
        
        for k in map_:
            result.append(map_[k])
        return result
{% endhighlight python %}

## Day 7 - Counting Elements

*Here is the question link : [Week #1 - Counting Elements](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3289/)*

This is another counting question. There is a simple rule. The rule says that count the elements such that `x` and `x+1` is in given array. I want to warn you about the question. You do not need to match `x` and `x+1`. So, maybe you have 4 `x` and 2 `x+1`, but it is OK. You should count as 4 instead of 2. 

{% highlight python %}
class Solution:
    def countElements(self, arr: List[int]) -> int:
        
        arr_dict = {num : arr.count(num) for num in set(arr)}
        counter = 0
    
        for num in arr:
            num_count = arr_dict[num]
            if num+1 in arr_dict:
                counter += 1
                
        return counter
{% endhighlight python %}

## Day 8 - Middle of the Linked List

*Here is the question link : [Week #2 - Middle of the Linked List](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/529/week-2/3290/)*

This question is a classic linked list problem. It says that we need to find middle node of the given linked list. Firstly, I am going to explain my approach and then, I am going to more efficient solution that I learned. My approach is iterative solution. Firstly, I copied `head` node into another `ListNode` object. I should keep my head node of the linked list. Then, I traversed the linked list to find length of the all linked list. After that, I found middle point of the list. Finally, I traversed the linked list until the middle node. Then, I returned it. Space complexity is $O(1)$ and time complexity is $O(n)$. But I am traversing 1.5 times the linked list.

{% highlight c++ %}
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        
        ListNode *tmpNode = head;
        
        int len = 0;
        
        while (tmpNode != NULL) {
            tmpNode = tmpNode -> next;
            len++;
        }
        
        int mid = len/2;
        int i = 0;
        
        while (i < mid) {
            head = head -> next;
            i++;
        }
        
        return head;
    }
};
{% endhighlight c++ %}

Another approach is similar but 2 pointer is being used to traverse one time. We are defining `slowNode` and `fastNode`. While `fastNode` is incrementing by 2, `slowNode` is incrementing by 1. So, when we reach at the end of the linked list with `fastNode`, we also reach middle of the linked list with `slowNode`. So, we do not need to traverse list again. We can reach the middle node with one iteration. Space comlexity is $O(1)$, time complexity is $O(n)$ in this approach. 

{% highlight c++ %}
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode *slowNode = head, *fastNode = head;
        while (fast && fast->next)
            slowNode = slow->next, fastNode = fast->next->next;
        return slowNode;
    }
};
{% endhighlight c++ %}

## Day 9 - Backspace String Compare

*Here is the question link : [Week #2 - Backspace String Compare](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/529/week-2/3291/)*

This question is similar to brackets problem. The question says that two strings which has **#** character as special are giving and you need to find these are equal or not. **#** means *backspace*. So, it is being deleted the character just before the **#**. I used *stack* data structure. The approach is simple. I declared 2 stack to push or pop characters at each iteration. In `for` loops, I control current character is `#` or not. If character is `#` and the length of the stack is not zero, I pop last pushed character. If the character is not `#`, then I push the character into stack. After applying these operations for both strings, I convert the stack to string. Then, I compare 2 strings. Actually, this solution does not satisfy the $O(1)$ space complexity. My solution has $O(N)$ space complexity. Nevertheless, it satisfies $O(N)$ time complexity.

{% highlight python %}
class Solution:
    def backspaceCompare(self, S: str, T: str) -> bool:
        s_stack, t_stack = [], []
        
        for i in range(len(S)):
            if "#" == S[i]:
                if len(s_stack) != 0:
                    s_stack.pop()
            else:
                s_stack.append(S[i])
            
        for i in range(len(T)):
            if "#" == T[i]:
                if len(t_stack) != 0:
                    t_stack.pop()
            else:
                t_stack.append(T[i])
        
        if "".join(s_stack) == "".join(t_stack):
            return True
        else:
            return False
{% endhighlight python %}

## Day 10 - Min Stack

*Here is the question link : [Week #2 - Min Stack](https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/529/week-2/3292/)*

There is another data structure question, stack. Stack is a basic and important data structure. Basically, I can explain that stack is a data structure which provides some of functionalities such as *push*, *pop*, *top* in nature. You cannot access elements directly as in *array*. You can only access top of the element in stack. So, if you need to access an element instead of top element, you need to *pop* elements until reaching destination. In this question, it says that write basic functions like `push()`, `pop()`, `top()`, and `getMin()`. Also, it expects that retrieving minimum element in constant time. I used 2 different stack to solve retrieving minimum element problem. Because of not accessing element directly, I stored the minimum elements in second stack. I used `list` data structure in **Python** because it satisfies some stack operations like *push* or *pop*. Let's say we are pushing some elements, `3, 4, 1, 7, 8, 10, 0`. So, our normal stack will be like this:

{% highlight python %}

| 0 |       | 0 |
|10 |       | 1 |
| 8 |       | 1 |
| 7 |       | 1 |
| 1 |       | 1 |
| 4 |       | 3 | 
| 3 |       | 3 |
|___|       |___|
stack      minStack
{% endhighlight python %}
So, I can access the minimum element by just removing top element from `minStack`.
{% highlight python %}
class MinStack:

    def __init__(self):
        self.stack = []
        self.minStack = []        

    def push(self, x: int) -> None:
        self.stack.append(x)
        if len(self.minStack) == 0:
            self.minStack.append(x)
        else:
            if self.minStack[-1] > x:
                self.minStack.append(x)
            else:
                last_val = self.minStack[-1]
                self.minStack.append(last_val)
        
    def pop(self) -> None:
        if len(self.stack) != 0:
            self.stack.pop()
            self.minStack.pop()

    def top(self) -> int:
        if len(self.stack) != 0:
            return self.stack[-1]
        return None
        

    def getMin(self) -> int:
        if len(self.minStack) != 0:
            return self.minStack[-1]
        return None
{% endhighlight python %}