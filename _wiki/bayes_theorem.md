---
layout   : wiki
category : Probability
title    : Bayes' theorem
summary  : 
created  : 18.06.22
updated  : 18.06.22
toc      : true
---

Bayes' theorem

* * *

* TOC
 {:toc}

* * *

# 정의

사건 B가 일어났을 때 사건 A가 일어날 확률 = (사건 A가 일어났을때 B가 일어날 확률) * (사건 A가 일어날 확률) / (사건 B가 일어날 확률)

수식으로는 아래와 같다.

$$ P(A|B) = \frac{P(B|A)P(A)}{P(B)} $$

위의 식에서 A 와 B 는 사건이고, $$ P(B) \neq 0 $$ 이다.

## Example

Q. 병원에서 정기검진을 했는데, 독감 양성 반응이 나왔다. 검사한 방법의 판독률은 99%라고 한다. 내가 진짜로 독감에 걸렸을 확률은?

A. 양성이 나왔을 때, 실제 독감에 걸린 확률을 구하는 문제.

양성을 +로, 독감을 Cold 로 쓰고 수식으로 쓰면 아래와 같다.

$$ P(Cold\mid+) $$ 을 구하는 문제. 아래 식의 답을 구하는 것과 같다.

$$ P(Cold\mid+) = \frac{P(+\mid Cold)P(Cold)}{P(+)} = \frac{P(+\mid Cold)P(Cold)}{P(+\mid Cold)P(Cold)+P(+\mid Cold')P(Cold')} $$

병에 걸렸는데, 양성일 확률이 99%이므로, $$ P(+\mid Cold) = 0.99 $$

동일한 원리로 $$ P(+\mid Cold') = 0.01 $$ 이다.

남은건 P(Cold)인데, 어느정도 임의의 숫자를 정할 수밖에 없는거 같다.

인구 100명중 병에 걸린 사람이 1명이라고 가정하자.

그럼 P(Cold) = 0.01이 된다.

위의 식을 다시 쓰면,

$$ \frac{P(+\mid Cold)P(Cold)}{P(+\mid Cold)P(Cold)+P(+\mid Cold')P(Cold')} = \frac{0.99*0.01}{0.99*0.01+0.01*0.99} = \frac{1}{2} $$

즉 99% 판독률 검사에서 독감 + 반응이 나왔다고 하더라도 실제로 독감에 걸렸을 확률은 50%라는 이야기.