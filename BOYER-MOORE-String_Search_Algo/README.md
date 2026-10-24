# Boyer–Moore String-Search Algorithm

## Overview

The Boyer–Moore String-Search Algorithm is an efficient string-matching algorithm used to find **```occurrences of a pattern inside a larger text.```**

Unlike the brute-force approach, which checks possible starting positions one by one, Boyer–Moore compares characters from right to left and uses mismatch information to shift the pattern by multiple positions whenever possible.
<br>

- It primarily uses two heuristics:  
  - Bad-Character Rule  
  - Good-Suffix Rule

## 1. Problem Statement

Given a text string ```text of length n``` and a ```string pattern of length m```, find the starting index of the first occurrence of the pattern in the text.

If the pattern does not exist, return -1.

## 2. Intuition

The brute-force approach checks every possible starting position and compares characters from left to right.

- Boyer–Moore improves the search by following these steps:

   - Align the pattern with a portion of the text.

   - Start comparing from the last character of the pattern.

   - If characters match, continue moving from right to left.

   - If a mismatch occurs, use the bad-character rule and/or good-suffix rule to determine a safe shift.

   - Repeat until the pattern is found or no valid alignment remains.

- **The main objective is to skip unnecessary character comparisons and avoid checking alignments that cannot produce a match.**

- We will be using ``` Bad-Character Rule``` in code implementations

## 3. Bad-Character Rule

The bad-character rule uses the character in the text that caused a mismatch.

- Steps:

   - 1.  Identify the mismatching character in the text.

   - 2. Find its rightmost occurrence in the pattern.

   - 3. Shift the pattern to align that occurrence with the mismatching text character.

   - 4. If the character does not occur in the pattern, shift the pattern past the mismatching character.

### Shift Formula

Let:

j = index of the mismatching character in the text.

last[c] = rightmost index of character c in the pattern.

last[c] = -1 if c does not occur in the pattern.

The shift is:  ```shift = max(1, j - last[c])```