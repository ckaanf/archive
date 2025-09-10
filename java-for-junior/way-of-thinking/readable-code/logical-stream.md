---
description: 논리적인 생각과, 사고의 흐름이 정방향으로 흐르도록 코드를 작성합니다
---

# 논리, 사고의 흐름

### 빠른 리턴

**리턴해야 할 것을 빨리**해서 else 문을 줄이기

{% code lineNumbers="true" %}
```java
if (a > 3) {
    doSomething1();
} else if (a <= 3 && b > 1) {
    doSomething2();
} else {
    doSomething3();
} 
...

if (a > 3) {
	doSomething1();
	return;
}
if (a <=3 && b >1) {
	doSomnething2();
	return;
}
doSomething3();


```
{% endcode %}

### 사고의 깊이 줄이기

[추상화 수준의 통일](abstract.md#undefined-1)서  얘기 했듯이 **사고의 깊이를 통일** 하면 좋습니다.

* 무조건 depth 줄이기를 지양
* 코드의 흐름이 맞다면 이중 중첩 구조나 추상화 수준에 로직이 있어도 괜찮습니다.



**사용할 변수는 가깝게 선언하면 좋다**

우리 프로덕트 코드는 꽤 길고, 변수를 위에 전부 선언해두고 사용한다면 한참 밑에서 이 변수가 뭐 때문에 필요 했는 지 계속 올려봐야하는 수고가 듭니다.

### 부정어와 공백의 활용

**공백도 의미**

여러 로직이나 메서들의 묶음을 공백을 통해 의미를 나누어 보여주면 편합니다.

{% code lineNumbers="true" %}
```java
...
가져오는 로직()

결과를 반환하는 로직()
...
// 로직 간의 단위를 나누어 가독성을 올려줌
```
{% endcode %}

**부정어를 만들어서 제공해보자**

예를 들어

{% code overflow="wrap" %}
```java
// 긍정 표현
if (user.isActive()) {
    // 로직 실행
}

// 부정 표현
if (!user.isActive()) {
    throw new IllegalStateException("비활성화된 사용자입니다.");
}

->

if (user.active()) {
    // 로직 실행
}

if (user.inActive()) {
        throw new IllegalStateException("비활성화된 사용자입니다.");
}

```
{% endcode %}

예시는 간단히 표현 했지만, 봐야하는 조건이 많아질 수록 부정을 생각하는 것은 생각을 한 단계 더 거치게 만듭니다.
