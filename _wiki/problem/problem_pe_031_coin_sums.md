---
layout   : wiki
category : Project euler
title    : No.31 Coin sums
summary  : 
created  : 18.06.15
updated  : 18.06.15
toc      : true
---

* TOC
 {:toc}

* * *

# Project Euler 31번 문제

## 문제

> In England the currency is made up of pound, £, and pence, p, and there are eight coins in general circulation:
>
> 1p, 2p, 5p, 10p, 20p, 50p, £1 (100p) and £2 (200p).
> It is possible to make £2 in the following way:
>
> 1×£1 + 1×50p + 2×20p + 1×5p + 1×2p + 3×1p
> How many different ways can £2 be made using any number of coins?

## 개요

각각 1p, 2p, 5p, 10p, 20p, 50p, 100p, 200p의 동전을 사용하여 200p를 만드는 모든 방법은 몇 가지인지 구하는 문제.

## 풀이

200p라는 target number가 있고, 한 가지 방법을 셀 때마다 count 해주는 방법으로 해결할 수 있다.

즉, 한 번 셀 때마다 전체 target number에서 동전의 value 만큼을 빼고, 나머지를 1 동전으로 채운다고 생각하면 쉽다.

밑의 코드를 보고 이해하면 더 신기하다.

첫 iteration에서 g = 200부터 시작한다.

2를 빼면 198이 되고, 이는 2원은 2p로 세고 198개를 1p로 세는 경우를 의미한다.

첫 iteration을 다 돌고 나면 1p, 2p로 세는 모든 경우의 수(101가지)가 계산된다.

두 번째 iteration에서 f = 200부터 시작한다.

5를 빼면 195가 되고, 이에 대해 첫 번째 iteration을 돌면서 경우의 수를 모두 계산한다.

iteration을 모두 거치고 나면 1p, 2p, 5p로 200p를 세는 경우의 수가 계산된다.

동일하게 반복한다.

## Code

```c++
#include <iostream>
int main() {
    int target = 200;
    int ways = 0;

    for (int a = target; a >= 0; a -= 200) {
        for (int b = a; b >= 0; b -= 100) {
            for (int c = b; c >= 0; c -= 50) {
                for (int d = c; d >= 0; d -= 20) {
                    for (int e = d; e >= 0; e -= 10) {
                        for (int f = e; f >= 0; f -= 5) {
                            for (int g = f; g >= 0; g -= 2) {
                                ways++;
                            }
                        }
                    }
                }
            }
        }
    }
    std::cout << ways << std::endl;
    return 0;
}
```