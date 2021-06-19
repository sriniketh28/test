# Longest Substring Without Repeating Characters

Given a string `s`, find the length of the **longest substring** without repeating characters.

**Example 1:**

```text
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

**Example 2:**

```text
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```text
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Example 4:**

```text
Input: s = ""
Output: 0
```

**Constraints:**

* `0 <= s.length <= 5 * 104`
* `s` consists of English letters, digits, symbols and spaces.

## Solution

{% tabs %}
{% tab title="solution.py" %}
```python
def lengthOfLongestSubstring(s):
    start = maxLength = 0
    dict = {}
    for i, char in enumerate(s):
        if char in dict and start<=dict[char]:
            start = dict[char]+1
        else:
            maxLength = max(maxLength,i-start+1)
        dict[char] = i
        
    return maxLength

print(lengthOfLongestSubstring("pwwkew"))            
```
{% endtab %}
{% endtabs %}

