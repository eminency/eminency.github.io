---
layout: page
title: "Python의 List Comprehension시 nested loop 사용"
date: 2016-10-18 14:38:00 +0900
categories: technical python
---

Python 사용시 List Comprehension 문법은 아마 일반적으로들 사용하는 것 중 하나일 듯 하다.

{% highlight python %}
>>> [ x**2 for x in xrange(1, 10) ]
[1, 4, 9, 16, 25, 36, 49, 64, 81]
{% endhighlight %}

가독성은 좀 떨어지지만 여기서 이중 for 문을 쓰는 것도 가능하다.

두 list의 cartesian product를 구한다고 생각해보자.

{% highlight python %}
>>> p = [1,2,3]
>>> q = ['a','b','c']
>>> [ (x, y) for x in p for y in q ]
[(1, 'a'), (1, 'b'), (1, 'c'), (2, 'a'), (2, 'b'), (2, 'c'), (3, 'a'), (3, 'b'), (3, 'c')]
{% endhighlight %}

for 부분을 generator 형태로 좀 이해하기 쉽게 재작성한다면 아래와 같다고 볼 수 있다.

{% highlight python %}
for x in p:
  for y in q:
    yield (x, y)
{% endhighlight %}

하지만 물론... 위같은 경우라면 나는 그냥 combination 모듈을 쓰고 말 것이다 -_-;;
