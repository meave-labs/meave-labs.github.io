---
layout: post
title: Levenshtein distance
mathjax: true
---

Levenshtein distance between two strings
=====================

Levenshtein distance is a kind of edit distance, that is a way of quantifying of how dissimilar two strings are. It measure the minimum number of edits needed to transform the first string into the second string.

We suppose that strings are indexed from 0. Let $s$ be a string, $a <= length(s)$, $b <= length(s)$ and $a <= b$, then $s[a:b)$ or $s[a:b-1]$ is a substring of a string that contains characters from $a$ to $b-1$ (including).

Let $f(i, j)$ be a Levenshtein distance between strings $s[0:j)$ and $t(0:i)$. Let's find a recursive formula for $f(., .)$.

* If $s[j - 1] = t[i - 1]$, then $f(i, j) = f(i - 1, j - 1)$.
* Otherwise, there are three possibilities:
  * We can convert string $s[0:j)$ to $t[0:i - 1)$ and add $t[i - 1]$ at the end of the final string: $f(i, j) = f(i - 1, j) + 1$.
  * Withing string $s[0:j)$, substring $s[0:j - 1)$ can be converted to $t[0:j-1)$ and character $s[j - 1]$ can be replaced with character: $t[i - 1]$: $f(i, j) = f(i - 1, j - 1) + 1$.
  * Finally, one can remove character $s[j - 1])$ from the end of substring $s[0: j)$ and convert substring $s[0:j-1)$ to $t[0:i)$: $f(i, j) = 1 + f(i, j - 1)$.
