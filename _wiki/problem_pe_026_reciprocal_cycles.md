---
layout   : wiki
category : Project euler
title    : No.26 Reciprocal cycles
summary  : 
created  : 18.06.05
updated  : 18.06.05
toc      : true
---

* TOC
 {:toc}

* * *

# Project Euler 26번 문제

## 문제

> A unit fraction contains 1 in the numerator. The decimal representation of the unit fractions with denominators 2 to 10 are given:
>
> 1/2 = 0.5
>
> 1/3 = 0.(3)
>
> 1/4 = 0.25
>
> 1/5 = 0.2
>
> 1/6 = 0.1(6)
>
> 1/7 = 0.(142857)
>
> 1/8 = 0.125
>
> 1/9 = 0.(1)
>
> 1/10 = 0.1
>
> Where 0.1(6) means 0.166666..., and has a 1-digit recurring cycle. It can be seen that 1/7 has a 6-digit recurring cycle.
>
> Find the value of d < 1000 for which 1/d contains the longest recurring cycle in its decimal fraction part.

## 개요

d < 1000 인 수 중 1/d 중 가장 긴 recurring cycle을 가진  값을 찾아야 하는 문제.

## 풀이

손으로 풀다 보면 3가지 유리수 종류가 있음을 알 수 있다.

* 반복되지 않는 수. 예를 들어, 1/4 = 0.25 - ( $$ 2^{-\alpha} \cdot 5^{-\beta} $$ )
* 처음부터 반복되는 수. 예를 들어, 1/7 = 0.(142857) - ( $$ 1^{-p} $$ )
* 중간부터 반복되는 수. 예를 들어, 1/14 = 0.0(714285) - ( $$ 1^{-p} \cdot 2^{-\alpha} \cdot 5^{-\beta} $$ )

( $$ p $$는 소수, $$ \alpha , \beta $$ 는 각각 임의의 자연수 )

가장 긴 반복 cycle을 찾아내기 위해선, 소수에 대해서만 검사하면 된다.
왜냐면, 중간부터 반복되는 수는 처음부터 반복되는 수와 동일한 반복 cycle을 가질 것이기 때문이다.

검사 범위는 소수에 대해 하는 것으로 정해졌고, 어떻게 검사하면 좋은지?

검색해보면 아래와 같은 방법이 있다.

1/7 = 0 (나머지 1)

1*10 / 7 = 1 (나머지 3)

3*10 / 7 = 4 (나머지 2)

2*10 / 7 = 2 (나머지 6)

6*10 / 7 = 8 (나머지 4)

4*10 / 7 = 5 (나머지 5)

5*10 / 7 = 7 (나머지 1) -> 처음과 같다

142857의 recurring cycle을 가지며, 6번 수행했으므로 step 수는 6임을 알 수 있다.

그러므로, 10을 곱하고 나머지를 곱하는 연산을 1~1000까지, 소수에 대하여 되풀이 하면 된다.

## Code

코드 풀이는 1~1000까지의 모든 숫자에 대해 검사하도록 하였다.
for 문에 해당하는 부분을 소수에 대해서만 검사하도록 치환할 수 있겠다.

```c++
#include <iostream>

int main()
{
    int temp = 0;
    int result = 0;
    int targetNum = 1000;

    for (int i = 1; i < targetNum; i++) {
        int counter = 0;
        int value = 10 % i;
        int z = targetNum;
        while (value != 1 && z > 0) {
            value = value * 10;
            value = value % i;
            counter++;
            z--;
        }

        if (counter > temp && z > 1) {
            temp = counter;
            result = i;
        }
    }
    std::cout << result;
}
```

## Links

[Explanation](https://eli.thegreenplace.net/2009/02/25/project-euler-problem-26)

[Solution in C](https://www.programminglogic.com/solution-to-problem-26-on-project-euler/)

[Discrete logarithm](https://en.wikipedia.org/wiki/Discrete_logarithm)