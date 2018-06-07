---
layout   : wiki
category : Project euler
title    : No.27 Quadratic primes
summary  : 
created  : 18.06.07
updated  : 18.06.07
toc      : true
---

* TOC
 {:toc}

* * *

# Project Euler 27번 문제

## 문제

> Euler discovered the remarkable quadratic formula:
>
> n2+n+41
> It turns out that the formula will produce 40 primes for the consecutive integer values 0≤n≤39. However, when n=40,402+40+41=40(40+1)+41 is divisible by 41, and certainly when n=41,412+41+41 is clearly divisible by 41.
>
> The incredible formula n2−79n+1601 was discovered, which produces 80 primes for the consecutive values 0≤n≤79. The product of the coefficients, −79 and 1601, is −126479.
>
> Considering quadratics of the form:
>
> n2+an+b, where $$ \lvert a \rvert <1000 and \lvert b \rvert ≤1000 $$
>
> where $$ \lvert n \rvert  $$ is the modulus/absolute value of n
> e.g. $$ \lvert 11 \rvert =11 and \lvert −4 \rvert =4 $$
> Find the product of the coefficients, a and b, for the quadratic expression that produces the maximum number of primes for consecutive values of n, starting with n=0.

## 개요

$$ n^2 + an + b $$, where $$ \lvert a \rvert < 1000 $$ and $$ \lvert b \rvert < 1000 $$

위의 식을 만족하면서, n=0부터 n=p까지 차례대로 대입했을때 식의 결과가 소수가 나오도록 가장 큰 숫자 p, a, b에 대하여 a*b를 구하는 문제.

## 풀이

가능한 경우의 수는 아래와 같다.

a에 대하여 -1000 ~ 1000, 약 2000개

b에 대하여 -1000 ~ 1000, 약 2000개

Worst case인 경우에 2000*2000개에 대한 Prime 검사를 한다.

왠지 무작정 풀어도 될 것 같다.

## Code

무식하게 전 경우에 대해 검사하도록 짜 본다.

```c++
#include <iostream>
#include <cmath>

int primes[1000] = {
  2,  3,  5,  7, 11, 13, 17, 19, 23, 29,
 31, 37, 41, 43, 47, 53, 59, 61, 67, 71,
 73, 79, 83, 89, 97,101,103,107,109,113,
127,131,137,139,149,151,157,163,167,173,
179,181,191,193,197,199,211,223,227,229,
233,239,241,251,257,263,269,271,277,281,
283,293,307,311,313,317,331,337,347,349,
353,359,367,373,379,383,389,397,401,409,
419,421,431,433,439,443,449,457,461,463,
467,479,487,491,499,503,509,521,523,541,
547,557,563,569,571,577,587,593,599,601,
607,613,617,619,631,641,643,647,653,659,
661,673,677,683,691,701,709,719,727,733,
739,743,751,757,761,769,773,787,797,809,
811,821,823,827,829,839,853,857,859,863,
877,881,883,887,907,911,919,929,937,941,
947,953,967,971,977,983,991,997,};

bool isPrime(int temp)
{
    int i = 0;
    while (primes[i] <= temp) {
        if (primes[i] == temp) {
            return true;
        }
        i++;
    }
    return false;
}

int main()
{
    int aMax = 0, bMax = 0, nMax = 0;
    for (int a = -1000; a < 1000; a++) {
        for (int b = -1000; b < 1000; b++) {
            int n = 0;
            while (isPrime(abs(n * n + a * n + b))) {
                n++;
            }
            if (n > nMax) {
                aMax = a;
                bMax = b;
                nMax = n;
            }
        }
    }

    std::cout << aMax << "," << bMax << "," << nMax << std::endl;
    std::cout << aMax * bMax << std::endl;
    getchar();
}
```