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

## 4. Shift Formula

Let:

**j = index of the mismatching character in the pattern.**

last[c] = rightmost index of character c in the pattern.

last[c] = -1 if c does not occur in the pattern.

The shift is:  ```shift = max(1, j - last[c])```

### Example-  
Text    = ABAAABCD  
Pattern = ABC

  - The last pattern character C does not match the text character A.

  - Since A occurs at index 0 in the pattern, shift the pattern by:  
  (here , j=2 , last[c]=0), c is A in this case 

  shift = max(1, 2 - 0) = 2  


## 5. C++ Code Implementation
```cpp
#include<bits/stdc++.h>
using namespace std;

int BoyerMoore(string text , string pattern){
    int n=text.size();
    int m=pattern.size();

    if(m==0) return 0;
    if(m>n) return -1;

    vector<int> lastseen(256,-1); // store the last occurences of each character in pattern

    for(int i=0;i<m;i++){
        lastseen[pattern[i]]=i;
    }

    int s=0; // starting position(traversed over text to match pattern)

    while(s<=n-m){
        int j=m-1; // start from right of the pattern to match in text

        while(j>=0 && pattern[j]==text[s+j]){
            j--;
        }

        if(j<0) return s; // if j becomes negative that means we have traversed through complete pattern and every character in text matches , hence return that index(s);

        int shift=max(1,j-lastseen[text[s+j]]);
        s+=shift;
    }

    return -1;
}

int main(){
    string text="ABAAABCD";
    string pattern="ABC";

    cout<<BoyerMoore(text,pattern)<<'\n'; // function returns first index where pattern matches in text

    return 0;
}