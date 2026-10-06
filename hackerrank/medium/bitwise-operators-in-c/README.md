# Bitwise Operators

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

In this challenge, you will use logical bitwise operators.  All data is stored in its binary representation.  The logical operators, and C language, use $1$ to represent true and $0$ to represent false. The logical operators compare bits in two numbers and return true or false, $0$ or $1$, for each bit compared.  

- `Bitwise AND operator &`  The output of bitwise AND is *1* if the corresponding bits of two operands is *1*. If either bit of an operand is *0*, the result of corresponding bit is evaluated to *0*. It is denoted by &.

- `Bitwise OR operator |`  The output of bitwise OR is *1* if at least one corresponding bit of two operands is *1*. It is denoted by |.

- `Bitwise XOR (exclusive OR) operator ^`  The result of bitwise XOR operator is *1* if the corresponding bits of two operands are opposite. It is denoted by $\oplus$.

For example, for integers 3 and 5,
```c
3 = 00000011 (In Binary)
5 = 00000101 (In Binary)

AND operation        OR operation        XOR operation
  00000011             00000011            00000011
& 00000101           | 00000101          ^ 00000101
  ________             ________            ________
  00000001  = 1        00000111  = 7       00000110  = 6

```

You will be given an integer $n$, and a threshold, $k.  For each number $i$ from $1$ through $n$, find the maximum value of the logical and, or and xor when compared against all integers through $n$ that are greater than $i$.  Consider a value only if the comparison returns a result less than $k$.  Print the results of the and, or and exclusive or comparisons on separate lines, in that order.  

**Example**  
$n = 3$  
$k = 3$  

The results of the comparisons are below:

```
a b   and or xor
1 2   0   3  3
1 3   1   3  2
2 3   2   3  1
```

For the `and` comparison, the maximum is $2$.  For the `or` comparison, none of the values is less than $k$, so the maximum is $0$.  For the `xor` comparison, the maximum value less than $k$ is $2$.  The function should print:  

```
2
0
2
```

**Function Description**  

Complete the *calculate_the_maximum* function in the editor below.  

*calculate_the_maximum* has the following parameters:  

- *int n:* the highest number to consider  
- *int k:* the result of a comparison must be lower than this number to be considered  

**Prints**  

Print the maximum values for the `and`, `or` and `xor` comparisons, each on a separate line.  

**Input Format**

The only line contains $2$ space-separated integers, $n$ and $k$.

**Constraints**

* $2 \le n \le 10^3$
* $2 \le k \le n$

**Output Format**

## Solution

**Language:** C  
**Runtime:** N/A  
**Memory:** N/A  
**Submitted:** 2026-10-06T10:36:24.454Z  

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main()
{
    int n, k;
    int max_and = 0, max_or = 0, max_xor = 0;

    scanf("%d %d", &n, &k);

    for (int i = 1; i <= n; i++)
    {
        for (int j = i + 1; j <= n; j++)
        {
            int and = i & j;
            int or = i | j;
            int xor = i ^ j;

            if (and < k && and > max_and)
                max_and = and;

            if (or < k && or > max_or)
                max_or = or;

            if (xor < k && xor > max_xor)
                max_xor = xor;
        }
    }

    printf("%d\n%d\n%d\n", max_and, max_or, max_xor);

    return 0;
}

```

---

[View on HackerRank](https://www.hackerrank.com/challenges/bitwise-operators-in-c/problem)