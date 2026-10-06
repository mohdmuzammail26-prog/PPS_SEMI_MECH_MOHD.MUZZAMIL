# Conditional Statements in C

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

**Objective**

_if_ and _else_ are two of the most frequently used conditionals in C/C++, and they enable you to execute zero or one conditional statement among many such dependent conditional statements. We use them in the following ways:

1. ```if```: This executes the body of bracketed code starting with $statement1$ if $condition$ evaluates to *true*.
	
    	if (condition) {
        	statement1;
            ...
        }

2. ```if - else```: This executes the body of bracketed code starting with $statement1$ if $condition$ evaluates to *true*, or it executes the body of code starting with $statement2$ if $condition$ evaluates to *false*. Note that only *one* of the bracketed code sections will ever be executed.

		if (condition) {
        	statement1;
            ...
        }
        else {
            statement2;
        	...
        }

3. ```if - else if - else```: In this structure, dependent statements are chained together and the $condition$ for each statement is only checked if all prior conditions in the chain are evaluated to *false*. Once a $condition$ evaluates to *true*, the bracketed code associated with that statement is executed and the program then skips to the end of the chain of statements and continues executing. If each $condition$ in the chain evaluates to false, then the body of bracketed code in the *else* block at the end is executed.

		if(first condition) {
        	...
        }
        else if(second condition) {
        	...
        }
        .
        .
        .
        else if((n-1)'th condition) {
            ....
        }
        else {
        	...
        }
        
**Task**

Given a positive integer denoting $n$, do the following:

- If $1 \le n \le 9$, print the lowercase English word corresponding to the number (e.g., `one` for $1$, `two` for $2$, etc.).
- If $n \gt 9$, print `Greater than 9`.

**Input Format**

The first line contains a single integer, $n$.

**Constraints**

- $1 \le n \le 10^9$

**Output Format**

If $1 \le n \le 9$, then print the lowercase English word corresponding to the number (e.g., `one` for $1$, `two` for $2$, etc.); otherwise, print `Greater than 9` instead.

## Solution

**Language:** C  
**Runtime:** N/A  
**Memory:** N/A  
**Submitted:** 2026-10-06T10:39:57.230Z  

```c
#include <assert.h>
#include <limits.h>
#include <math.h>
#include <stdbool.h>
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* readline();

int main()
{
    int n;

    scanf("%d", &n);

    if (n == 1)
        printf("one");
    else if (n == 2)
        printf("two");
    else if (n == 3)
        printf("three");
    else if (n == 4)
        printf("four");
    else if (n == 5)
        printf("five");
    else if (n == 6)
        printf("six");
    else if (n == 7)
        printf("seven");
    else if (n == 8)
        printf("eight");
    else if (n == 9)
        printf("nine");
    else
        printf("Greater than 9");

    return 0;
}



char* readline() {
    size_t alloc_length = 1024;
    size_t data_length = 0;
    char* data = malloc(alloc_length);

    while (true) {
        char* cursor = data + data_length;
        char* line = fgets(cursor, alloc_length - data_length, stdin);

        if (!line) { break; }

        data_length += strlen(cursor);

        if (data_length < alloc_length - 1 || data[data_length - 1] == '\n') { break; }

        size_t new_length = alloc_length << 1;
        data = realloc(data, new_length);

        if (!data) { break; }

        alloc_length = new_length;
    }

    if (data[data_length - 1] == '\n') {
        data[data_length - 1] = '\0';
    }

    data = realloc(data, data_length);

    return data;
}

```

---

[View on HackerRank](https://www.hackerrank.com/challenges/conditional-statements-in-c/problem)