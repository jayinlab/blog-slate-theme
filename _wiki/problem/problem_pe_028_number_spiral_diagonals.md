---
layout   : wiki
category : Project euler
title    : No.28 Number spiral diagonals
summary  : 
created  : 18.06.05
updated  : 18.06.05
toc      : true
---

* TOC
 {:toc}

* * *

# Project Euler 28번 문제

## 문제

> Starting with the number 1 and moving to the right in a clockwise direction a 5 by 5 spiral is formed as follows:
>
> 21 22 23 24 25
>
> 20  7  8  9 10
>
> 19  6  1  2 11
>
> 18  5  4  3 12
>
> 17 16 15 14 13
>
> It can be verified that the sum of the numbers on the diagonals is 101.
>
> What is the sum of the numbers on the diagonals in a 1001 by 1001 spiral formed in the same way?

## 개요

위의 모양을 한 1001 x 1001 모양에 대하여, 대각선 방향의 숫자를 모두 더하는 문제.

## 풀이

손으로 풀어보면, 숫자가 늘어선 모양을 따라 아래와 같이 분류할 수 있음을 알게 되었다.

$$ 1 $$

$$ (3,5,7,9) =  9*4-2-4-6    = (3^2)*4-2*(1+2+3) $$

$$ (13,17,21,25) = 25*4-4-8-12   = (5^2)*4-4*(1+2+3) $$

$$ (31,37,43,49) = 49*4-6-12-18  = (7^2)*4-6*(1+2+3) $$

$$ ... $$

$$ ((2n+1)^2)*4 + (-1)*(2n)*(1+2+3) $$

예외인 1을 제외하고, 구하려는 문제는 1001 x 1001 이므로 501까지 loop를 돌면 되겠다.

## Code

```c++
#include <iostream>
int main()
{
    int temp = 0;
    int result = 1;
    for (int n = 1; n < 501; n++) {
        temp = ((2*n+1) * (2*n+1))*4 + (-1)*(2 * n)*(1 + 2 + 3);
        result += temp;
    }
    std::cout << result;
}
```