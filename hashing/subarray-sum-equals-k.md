# Subarray Sum Equals K

Given an array of integers `nums` and an integer `k`, return _the total number of continuous subarrays whose sum equals to `k`_.

**Example 1:**

```text
Input: nums = [1,1,1], k = 2
Output: 2
```

**Example 2:**

```text
Input: nums = [1,2,3], k = 3
Output: 2
```

**Constraints:**

* `1 <= nums.length <= 2 * 104`
* `-1000 <= nums[i] <= 1000`
* `-107 <= k <= 107`

## Solution

{% tabs %}
{% tab title="solution.py" %}
```python
def subarraySum(nums, k):
    count = 0
    sums = 0
    dict = {}
    dict[0] = 1
    for i in range(len(nums)):
        sums += nums[i]
        count += dict.get(sums-k,0)
        dict[sums] = dict.get(sums,0)+1
        
    return count

print(subarraySum([1,1,1], 2))
```
{% endtab %}
{% endtabs %}

