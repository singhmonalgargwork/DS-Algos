# Boyer-Moore Voting Algorithm

## Table of Contents

- [Overview](#overview)
- [Core Intuition](#core-intuition)
- 

## Overview
- Moore's Voting Algorithm is an efficient algorithm used to find the majority element in an array.

- A majority element is an element that appears ```strictly more than N/2(floor) times```, where (N) is the size of the array.
- example- Input:  [2, 2, 1, 1, 1, 2, 2] -> Output: 2
  - The element 2 appears 4 times in an array of size 7.
  - Since (4 > 7/2), 2 is the majority element.

## Core Intuition
- The fundamental idea behind Moore's Voting Algorithm is **```cancellation```**.

  - Two different elements can be considered to cancel each other out.

  - The majority element appears more than all the other elements combined.

  - Therefore, even after cancelling different elements against it, at least one occurrence of the majority element must survive.