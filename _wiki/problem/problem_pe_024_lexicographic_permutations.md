---
layout   : wiki
category : Project euler
title    : No.24 Lexicographic permutations
summary  : 
created  : 18.06.01
updated  : 18.06.04
toc      : true
---

* TOC
 {:toc}

* * *

# Project Euler 24번 문제

## 문제

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

## 풀이 2, 이미 알고 있는 정보로 풀기

0123456789 에서 0 뒤에 오는 숫자의 경우의 수는 9! = 362880개 임을 알고 있다.
마찬가지로, 1로 시작하는 숫자의 경우의 수도 9!개이다. 우리가 찾는 백만번째 숫자는 2로 시작하는 숫자임을 추정할 수 있다.

위의 과정을 반복하여 백만번째 수를 찾을 수 있다.

1. 1000000 - n!를 계산했을 때의 숫자가 0보다 큰 경우에 count를 증가시킨다.
2. perm 에서 count 번째에 해당하는 숫자를 출력한다.
3. 이미 출력되었으니, count 번째에 해당하는 숫자를 지운다.
4. 1~3을 10회 반복한다.

위의 과정에서 [std::vector::erase](http://en.cppreference.com/w/cpp/container/vector/erase)가 사용되었다.

```c++
#include <iostream>
#include <vector>

int Factorial(int n) {
    int result = 1;
    while (n > 1){
        result *= n;
        n--;
    }
    return result;
}

int main()
{
    std::vector<int> perm = { 0,1,2,3,4,5,6,7,8,9 };

    int target = 1000000;
    int num = 0;
    int result;
    int i = 10;

    while (i > 0) {
        int count = 0;
        result = Factorial(i-1);
        while ((target - result) > 0) {
            target -= result;
            count++;
        }
        std::cout << perm.at(count);
        perm.erase(perm.begin() + count);
        i--;
    }
}
```

## 풀이 3, Brute Force 2

[std::next_permutation](http://en.cppreference.com/w/cpp/algorithm/next_permutation) 으로 무식하게 풀어낼 수 있다.

std::next_permutation은 input 배열을 다음 순열로 바꿔주는 함수다.
예를 들면, 이 함수에 input으로 1-2-3-4를 전달하면 1-2-4-3으로 바뀌고 함수가 true를 반환한다.

```c++
#include <iostream>
#include <string>
#include <algorithm>

int main()
{
    unsigned int num = 1000000;
    std::string current = "0123456789";
    while (--num)
        std::next_permutation(current.begin(), current.end());
    std::cout << current << std::endl;
}
```

## Link

[Project euler problem 24](https://projecteuler.net/problem=24)