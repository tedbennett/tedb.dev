---
title: "Leetcode 1"
date: 2020-12-02T21:38:52Z
description: "Add Two Numbers"
website: "https://leetcode.com/problems/add-two-numbers/"
---

### Brief
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

### First Attempt
My first attempt involved recursively moving through the linked lists until the end of the longest list is reached. For each pair of nodes, a new node for the output was created and it's value set to the sum of the values of the pair. This was the return value for the recursive call. It's `next` attribute was set as returned node from further recursive calls. 

This method involved a bit of logic in avoiding null errors when trying to access nodes at the ends of either list. This was a bit messy since a call would be made to the recursive function where both nodes were None, and so the return value had to be None too.

This method was very average in its speed (faster than 50%) and poor in its memory usage (better than 10%)

### Second Attempt
This can be simplified by just iterating through the linked lists instead. The logic required is still the same but the layout is allowed to be much tidier. This still required making the first iteration outside of the loop and had almost the same speed and memory usage as the previous attempt.


### Post-Submission Attempt
Using the same iterative method as before, a few optimisations could be made. 
- Firstly, using a sentinel node allows all of the iterations to be done inside the loop, making the code neater. The return value was changed to the sentinel's *next* list item.
- Next, the carry var did not need to be stored and could simply be taken by updating the result var to `result // 10` at the start of each iteration.
- Due to being a bit rusty with Python, there were some untidy checks (i.e `is not None`) I was making, and I also was making the same if-checks twice, which could be refactored.


### Final Code 
```python
def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
    sentinel = ListNode(0)
    next_node = sentinel
    result = 0
    while l1 or l2:
        result = result // 10  # Equal to 0 or 1 so equiv to carry
        if l1:
            result += l1.val
            l1 = l1.next
        if l2:
            result += l2.val
            l2 = l2.next
        next_node.next = ListNode(result % 10)
        next_node = next_node.next
    if result // 10 != 0:
        next_node.next = ListNode(1)
    return sentinel.next
```