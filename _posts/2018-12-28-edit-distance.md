---
layout: post
title: Levenshtein distance
mathjax: true
---

Levenshtein distance between two strings
=====================

Levenshtein distance is a kind of edit distance, that is a way of quantifying of how dissimilar two strings are. It measure the minimum number of edits needed to transform the first string into the second string.

Edits means:

  * Insert character at position $i$.
  * Remove character at position $i$.
  * Replace character at position $i$ with character $c$.

Please note that if one has a sequence of edits of length $len$ than it can be converted to another sequence with the same length but with the different  of edits. For example:
rder

  * There is a remove at position $i$ and later insert at position $j$ ($REMOVE(i)$ and $INSERT(j)$), $i < j$, then these two operations can be swapped: first $INSERT(j + 1)$ and then $REMOVE(i)$.
  * There is a replace of a character at position $i$ with a character $c$ and remove of a character at position $j$ ($REPLACE(i, c)$ and $REMOVE(j)$), $i < j$. Then these operations can be swapped: $REMOVE(j)$, $REPLACE(i, c)$.

We suppose that strings are indexed from 0. Let $s$ be a string, $a <= length(s)$, $b <= length(s)$ and $a <= b$, then $s[a:b)$ or $s[a:b-1]$ is a substring of a string that contains characters from $a$ to $b-1$ (including).

Let $f(i, j)$ be a Levenshtein distance between strings $s[0:j)$ and $t(0:i)$. Let's find a recursive formula for $f(., .)$.

* If $s[j - 1] = t[i - 1]$, then $f(i, j) = f(i - 1, j - 1)$.
* Otherwise, there are three possibilities:
  * We can convert string $s[0:j)$ to $t[0:i - 1)$ and add $t[i - 1]$ at the end of the final string: $f(i, j) = f(i - 1, j) + 1$.
  * Withing string $s[0:j)$, substring $s[0:j - 1)$ can be converted to $t[0:j-1)$ and character $s[j - 1]$ can be replaced with character: $t[i - 1]$: $f(i, j) = f(i - 1, j - 1) + 1$.
  * Finally, one can remove character $s[j - 1])$ from the end of substring $s[0: j)$ and convert substring $s[0:j-1)$ to $t[0:i)$: $f(i, j) = 1 + f(i, j - 1)$. I put deletion at the beginning because it is more understandable for me but thanks to the concept of reordering it can be put at the end.

We use the above rules to calculate $f(i, j)$ for all $i < length(t)$ and $j < length(s)$. This takes $O(length(s)*length(t)$ time. We don't need to store all previous solutions but just the solutions from the previous step. So the auxiliary space can be $O(min(length(s), length(t)))$.

It is possible to reconstruct the best sequence. This sequence includes steps where no change is done (the length of the sequence doesn't change, $s[j - 1] = t[i - 1]$). These steps corresponds to *the longest common subsequence* of both strings.
