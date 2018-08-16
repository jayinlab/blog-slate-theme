---
layout   : wiki
category : Project euler
title    : No.30 Digit fifth powers
summary  : 
created  : 18.06.11
updated  : 18.06.11
toc      : true
---

* TOC
 {:toc}

* * *

# Project Euler 30번 문제

## 문제

> Surprisingly there are only three numbers that can be written as the sum of fourth powers of their digits:
>
> $$ 1634 = 1^4 + 6^4 + 3^4 + 4^4 $$
>
> $$ 8208 = 8^4 + 2^4 + 0^4 + 8^4 $$
>
> $$ 9474 = 9^4 + 4^4 + 7^4 + 4^4 $$
>
> As $$ 1 = 1^4 $$ is not a sum it is not included.
>
> The sum of these numbers is 1634 + 8208 + 9474 = 19316.
>
> Find the sum of all the numbers that can be written as the sum of fifth powers of their digits.

## 개요

각 자리 숫자의 5승의 합으로 나타날 수 있는 모든 수의 합을 구하는 문제.

## 풀이

$$ 6*9^5 = 354294 $$ 이므로, 6자리 숫자에 대해 확인해보면 된다.

그러니까 $$ abcdef = a^5+b^5+c^5+d^5+e^5+f^5 $$ 정도가 되겠다.

여기까지만 확인하고, 매우 게으른 방법으로 코딩해서 풀어보면 되겠다.

## Code

모든 숫자에 대해 검사하는 방법으로 풀 수 있다.

```c++
#include <iostream>

int main()
{
    int result = 0;

    for (int a = 0; a < 10; a++) {
        for (int b = 0; b < 10; b++) {
            for (int c = 0; c < 10; c++) {
                for (int d = 0; d < 10; d++) {
                    for (int e = 0; e < 10; e++) {
                        for (int f = 0; f < 10; f++) {
                            if ((a * 100000 + b * 10000 + c * 1000 + d * 100 + e * 10 + f) == (pow(a, 5) + pow(b, 5) + pow(c, 5) + pow(d, 5) + pow(e, 5) + pow(f, 5))) {
                                result += a * 100000 + b * 10000 + c * 1000 + d * 100 + e * 10 + f;
                                std::cout << a << b << c << d << e << f << std::endl;
                            }
                        }
                    }
                }
            }
        }
    }
    std::cout << "result : " << result - 1 << std::endl;

    return 0;
}
```