---
title: "Leetcode 2"
date: 2020-12-03T16:50:52Z
description: "Longest Substring Without Repeating Characters"
website: "https://leetcode.com/problems/longest-substring-without-repeating-characters/"
---
### Brief

Given a string s, find the length of the longest substring without repeating characters.

### First Attempt

For each char in the string, search ahead to find the next matching char and the end of the substring. This would take O(n^2) at worst, but could be optimised e.g by exiting early if the end of the string is reached (no other substring could be longer).

### Ideas that didn't work

- Iterating through each char and adding it to a set of seen chars. When we iterate to the next char, we check if it exists in that set already, and if it does, we store the current length of that set as the substring length, and then resetting the set and continuing. This can miss substrings in between these matching chars and so doesn't search every substring.

- Iterating through the list and storing the index of each char in a map of lists of indices. This lets you see pairs of characters and so you can find the largest difference in indices to find the longest substring. This ignores the possibility of a pair of other characters in between that pair will make the substring invalid. To get around this, you'd need to check through every other pair of char indices too, which would make this an O(n^2) solution but much more complex to do.

### Second Attempt

This attempt draws on the first attempt and the first idea that didn't work. We create a dict of char keys and index values. We also define the substring start at 0 and the current max substring length at 0 too. We iterate through the map and store each char's index in the map. If the char already exists, we've found a substring, and update the max substring length if need be. We then update the start var to the next char and continue. There is no need to go back to the char after our previous start since we've already searched through that part of the list. This solution has O(n) time complexity.


### Learnings
- Sliding window solutions can bring down time complexity a lot and I should be thinking about them for problems like this.
- A dict is only necessary when storing values, otherwise use a set.

### Final Code 
```python
def lengthOfLongestSubstring(s: str) -> int:
    max_count = 0
    current_start = 0
    idxs = {}
    for idx, char in enumerate(s):
        if char in idxs and idxs[char] >= current_start:
            # Found dupe, move current_start to next character
            # e.g in sequence abca, move current_start to b
            current_start = idxs[char] + 1
        else:
            max_count = max(max_count, idx - current_start + 1)
        idxs[char] = idx
    return max_count
```