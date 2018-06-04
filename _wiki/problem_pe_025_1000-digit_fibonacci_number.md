---
layout   : wiki
category : Project euler
title    : No.24 1000-digit fibonacci number
summary  : 
created  : 18.06.04
updated  : 18.06.04
toc      : true
---

* TOC
 {:toc}

* * *

# Project Euler 25번 문제

## 문제

> The Fibonacci sequence is defined by the recurrence relation:
>
> $$ F_n = F_{n−1} + F_{n−2} $$, where $$ F_1 = 1 $$ and $$ F_2 = 1 $$ .
> Hence the first 12 terms will be:
>
> $$ F_1 = 1, F_2 = 1, F_3 = 2, F_4 = 3 $$
>
> $$ F_5 = 5, F_6 = 8, F_7 = 13, F_8 = 21 $$
>
> $$ F_9 = 34, F_{10} = 55, F_{11} = 89, F_{12} = 144 $$
>
> The 12th term, F12, is the first term to contain three digits.
>
> What is the index of the first term in the Fibonacci sequence to contain 1000 digits?

첫 번째 1000자리 피보나치 숫자의 first term을 찾아내는 문제다.

## 개요

## 풀이 1, 손으로 풀기

피보나치 수가 충분히 클 때, 피보나치 수는 아래의 식으로 수렴함이 알려져 있다.

$$ F(n) = [\frac{\phi^n} {\sqrt{5}}] $$

$$ \phi $$ 는 황금비로 약 1.618의 수다.

1000자리 수라면, 아래의 식을 만족하는 수 n을 찾아내면 된다.

$$ \frac{\phi^n} {\sqrt{5}} > 10^{999} $$

풀어쓰면,

$$ n > \frac{log(10) \cdot 999 + log(5)/2} {log(\phi)} = 4781.859 $$

즉, 답은 4782.

## 추가

피보나치 수열이 신기해서 좀 더 알아보았다.

1. 일반항은 아래와 같다.

$$ F_n = \frac{1}{\sqrt{5}} \left \{ ({\frac{1+\sqrt{5}}{2}})^{n} - ({\frac{1-\sqrt{5}}{2}})^{n} \right \} $$

2. 인접한 두 수열의 비가 황금비로 수렴한다.

$$ \lim_{n\to\infty}\frac{F_{n+1}}{F_n}=\varphi=\frac{1+\sqrt5}{2}=1.6180339887\cdots $$

## Link

[Wikipedia, Fibonacci number - closed form expression](https://en.wikipedia.org/wiki/Fibonacci_number#Closed-form_expression)