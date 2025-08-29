---
description: 추상, extract method 등을 활용하여 의미 부여 할 때 상황
---

# 추상화 수준의 통일

### 추상(抽象)

{% hint style="info" %}
사물이나 표상(表象)을 어떤 성질·공통성·본질에 착안하여 그것을 추출(抽出)하여 파악하는 것.
{% endhint %}

### 메서드의 추상화

메서드로  추출을 통해 코드를 의미 있는 단위의 묶음으로 바꿀 수 있습니다.

```
public void someMethod() {
    Product product = ...
    // 상품을 가져오는 로직 
        ...
    Stock stock = ...
    // 재고를 가져오는 로직 
        ...
}

public void someMethod() {
 // 상품가져오기
 // 재고가져오기
 ...
}
```

예시는 간단해서 와닿지 않을 수 있지만, 분명 로직이 길어지면 해석이 들어갈 겁니다.

{% hint style="warning" %}
그러나 함수를 무조건 추출하진 말아야합니다.

의미 있는 함수 추출이 아닌 무조건 적인 추출은 별 의미가 없을 수 있습니다.

ex)\
for(Product product: ProductList) {

&#x20;   상품으로 무언갈 하는 로직

}

위와 같은 경우는 실질적으로 의미 있는 메서드 추출이 아닐 수 있습니다.

우리는 메서드를 추출할 때 관계를 보고 의미 있는 단위로 만들거나,

로직이 이해를 하는데 필요하다면 남겨두는 선택도 할 수 있어야 합니다.
{% endhint %}

### 추상화 수준

엄밀히 Java에서 말하는 추상화는 아닙니다.

저는 이 추상화 수준이 한 메서드 내에서는 **동일**해야 한다고 생각합니다.

예를 들어

```
public void someMethod() {
 // 상품가져오기
 // 재고가져오기
 ...
}
```

위와 같은 형식입니다.

추상화 레벨에 구현과   로직이 섞이면 우리는 코드를 읽다가 `해석` 하는 과정이 필요합니다.

```
public void someMethod() {
    // 상품가져오기
    // 재고가져오기
    if(재고 == 구매가능) {
     재고에 대한 로직
    }
    ...
}
```

저는 이런 경우에는 추상화 레벨이 맞지 않다고 생각합니다.

위와 같은 경우에서는 재고의 로직을 객체지향적으로 `재고` 에 넣어서 처리할 수도 있고

혹은 의미 단위의 private 메서드로 추출하여 **추상화 레벨을 올려 추상화 수준을 통일** 할 수 있을 겁니다.



> ref.
>
> [https://techblog.lycorp.co.jp/ko/techniques-for-improving-code-quality-18](https://techblog.lycorp.co.jp/ko/techniques-for-improving-code-quality-18)
>
> [https://www.inflearn.com/course/%EC%9D%B8%ED%94%84%EB%9F%B0-simple-design-25/dashboard](https://www.inflearn.com/course/%EC%9D%B8%ED%94%84%EB%9F%B0-simple-design-25/dashboard)
>
>
