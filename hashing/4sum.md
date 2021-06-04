# 4Sum

Given an array `nums` of `n` integers, return _an array of all the **unique** quadruplets_ `[nums[a], nums[b], nums[c], nums[d]]` such that:

* `0 <= a, b, c, d < n`
* `a`, `b`, `c`, and `d` are **distinct**.
* `nums[a] + nums[b] + nums[c] + nums[d] == target`

You may return the answer in **any order**.

**Example 1:**

```text
Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
```

**Example 2:**

```text
Input: nums = [2,2,2,2,2], target = 8
Output: [[2,2,2,2]]
```

**Constraints:**

* `1 <= nums.length <= 200`
* `-109 <= nums[i] <= 109`
* `-109 <= target <= 109`

## **Solution**

{% tabs %}
{% tab title="solution.py" %}
```python
def fourSum(nums, target):
    def kSum(nums, target, k):
        if len(nums) == 0 or nums[0] * k > target or nums[-1] * k < target:
            return []
        if k == 2:
            return twoSum(nums, target)
        result = []
        for i in range(len(nums)):
            if i == 0 or nums[i-1] != nums[i]:
                for j in range(len(kSum(nums[i+1:], target-nums[i], k-1))):
                    result.append([nums[i]]+kSum(nums[i+1:], target-nums[i], k-1)[j])
                    
                    
        return result

    def twoSum(nums, target):
        result = []
        nums_set = set()
        for i in range(len(nums)):
            if len(result) == 0 or result[-1][1] != nums[i]:
                if target - nums[i] in nums_set:
                    result.append([target-nums[i], nums[i]])
            nums_set.add(nums[i])
            
        return result
    
    nums.sort()
    return kSum(nums, target, 4)

print(fourSum([1,0,-1,0,-2,2],0))
```
{% endtab %}
{% endtabs %}

