# Longest Consecutive Sequence

Given an unsorted array of integers `nums`, return _the length of the longest consecutive elements sequence._

You must write an algorithm that runs in `O(n)` time.

**Example 1:**

```text
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```

**Example 2:**

```text
Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
```

**Constraints:**

* `0 <= nums.length <= 105`
* `-109 <= nums[i] <= 109`

## Solution

{% tabs %}
{% tab title="solution.py" %}
```python
# Time complexity : O(n)
def longestConsecutive(nums):
    nums_set = set(nums)
    ans = 0
    for num in nums_set:
        if num-1 not in nums_set:
            temp = num + 1
            while temp in nums_set:
                temp += 1
            ans = max(ans, temp-num)

    return ans

print(longestConsecutive([100,4,200,1,3,2]))
```
{% endtab %}
{% endtabs %}

**Complexity Analysis**

* Time complexity : O\(n\)

  Although the time complexity appears to be quadratic due to the `while` loop nested within the `for` loop, closer inspection reveals it to be linear. Because the `while` loop is reached only when `num` marks the beginning of a sequence \(i.e. `num-1` is not present in `nums`\), the `while` loop can only run for n iterations throughout the entire runtime of the algorithm. This means that despite looking like O\(n \* n\) complexity, the nested loops actually run in O\(n + n\) = O\(n\) time. All other computations occur in constant time, so the overall runtime is linear.

