# Boyer–Moore String-Search Algorithm

## Overview

The Boyer–Moore String-Search Algorithm is an efficient string-matching algorithm used to find **```occurrences of a pattern inside a larger text.```**

Unlike the brute-force approach, which checks possible starting positions one by one, Boyer–Moore compares characters from right to left and uses mismatch information to shift the pattern by multiple positions whenever possible.
<br>

- It primarily uses two heuristics:  
  - Bad-Character Rule  
  - Good-Suffix Rule