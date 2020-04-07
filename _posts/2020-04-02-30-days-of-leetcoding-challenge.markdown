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