---
title: "Leetcode 3"
date: 2020-12-06T11:07:11Z
draft: true
description: "Median of Two Sorted Arrays"
---

### Brief

Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

### First Attempt

First, we need to merge the two arrays. With a sorted, merged array, we only need to look at the midpoint value. To merge the arrays, we iterate through both arrays one element at a time, checking which array has the smaller value and adding that to the new array. Once that is complete, we can get the median from the midpoint of this array.