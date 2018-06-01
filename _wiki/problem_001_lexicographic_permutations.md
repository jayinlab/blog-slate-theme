---
layout   : wiki
category : project euler
title    : Lexicographic permutations
summary  : 
created  : 18.06.01
updated  : 18.06.01
toc      : true
---
* TOC
{:toc}

* * *

## 문제

[Project euler](https://projecteuler.net/) 24번 문제

> A permutation is an ordered arrangement of objects. For example, 3124 is one possible permutation of the digits 1, 2, 3 and 4. If all of the permutations are listed numerically or alphabetically, we call it lexicographic order. The lexicographic permutations of 0, 1 and 2 are:
>
> 012   021   102   120   201   210
>
> What is the millionth lexicographic permutation of the digits 0, 1, 2, 3, 4, 5, 6, 7, 8 and 9?

사전식 순서로 0~9의 수를 배치할 때, 백만번 째 숫자를 맞추는 문제다.

## 풀이 1, Brute Force

첫 번째 수는 0123456789,
두 번째 수는 0123456798,
세 번째 수는 0123456879,
네 번째 수는 0123456897,
...
백만번 반복하면 되겠다.

```c++
#include <iostream>
#include <string>

using namespace std;

int perm[10] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

void swap(int i, int j) {
    int k = perm[i];
    perm[i] = perm[j];
    perm[j] = k;
}

void main(){

    int count = 1;
    int num = 1000000;
    while (count < num) {
        int N = 10;
        int i = N - 1;
        while (perm[i - 1] >= perm[i]) {
            i = i - 1;
        }
        int j = N;
        while (perm[j - 1] <= perm[i - 1]) {
            j = j - 1;
        }
        // swap values at position i-1 and j-1
        swap(i - 1, j - 1);
        i++;
        j = N;
        while (i < j) {
            swap(i - 1, j - 1);
            i++;
            j--;
        }
        count++;
    }
    string permNum = "";
    for (int k = 0; k < 10; k++) {
        permNum = permNum + std::to_string(perm[k]);
    }
    cout << permNum << endl;
    getchar();
}
```

## 풀이 2, 

0123456789 에서 0 뒤에 오는 숫자의 경우의 수는 9! = 362880개 임을 알고 있다.


## Link

https://projecteuler.net/problem=24