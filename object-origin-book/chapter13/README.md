# 서브클래싱과 서브타이핑

상속의 두가지 용도

- 타입계층  
  : 타입 계층의 관점에서 부모 클래스는 자식 클래스의 **일반화(generalization)**이고 자식 클래스는 부모 클래스의 **특수화(specialization)**이다.
- 코드재사용  

`상속을 사용하는 일차적인 목표는 코드 재사용이 아니라 타입 계층을 구현하는 것이어야 한다.`



> 결론부터 말하자면 동일한 메시지에 대해 서로 다르게 행동할 수 있는 다형적인 객체를 구현하기 위해서는 객체의 행동을 기반으로 타입 계층을 구성해야 한다.



## 올바른 타입 계층을 구성하는 원칙?

### 타입 계층이란 무엇인가? 상속을 이용해 타입 계층을 구현한다는 것은 무엇을 의미하는가?



## 타입

- **개념 관점의 타입**  
  \> 우리가 인지하는 세상의 사물의 종류, 다시 말해 우리가 인식하는 객체들에 적용하는 개념이나 아이디어를 가리켜 타입.
  - **심볼** - 타입에 이름을 붙인것
  - **내연** - 타입의 정의로서 타입에 속하는 객체들이 가지는 공통적인 속성이나 행동을 가리킴 (ex, 프로그래밍 언어 는 '컴퓨터에게 특정한 작업을 지시하기 위한 어휘와 문법적인 규칙의 집합')
  - **외연** - 타입에 속하는 객체들의 집합 (ex, 프로그래밍 언어 는 자바, 루비, 자바스크립트 등등등)
- **프로그래밍 언어 관점의 타입**  
  \> 연속적인 비트에 의미와 제약을 부여하기 위해 사용, 프로그래밍 언어의 관점에서 타입은 비트 묶음에 의미를 부여하기 위해 정의된 제약과 규칙을 가리킴
  - 타입에 수행될 수 있는 유효한 오퍼레이션의 집합을 정의 ( + )
  - 타입에 수행되는 오퍼레이션에 대해 미리 약속된 문맥을 제공( ex, a + b )
- **객체지향 패러다임 관점의 타입**
  - 프로그래밍 언어의 관점에서 타입은 호출 가능한 오퍼레이션의 집합을 정의한다. 객체지향 프로그래밍에서 오퍼레이션은 객체가 수신할 수 있는 메시지를 의미한다. 따라서 **객체의 타입**이란 객체가 수신할 수 있는 메시지의 종류를 정의하는 것
  - 메시지의 종류 = **퍼블릭 인터페이스**
  - **객체지향 프로그래밍에서 타입을 정의하는 것은 객체의 퍼블릭 인터페이스를 정의하는 것과 동일**
  - **객체의 퍼블릭 인터페이스가 객체의 타입을 결정한다. 따라서 동일한 퍼블릭 인터페이스를 제공하는 객체들은 동일한 타입으로 분류된다.**
  - 객체에게 중요한 것은 속성이 아니라 행동, 어떤 객체들이 동일한 상태를 가지고 있더라도 **퍼블릭 인터페이스**가 다르다면 이들은 서로 다른 타입으로 분류해야 된다.

## 타입 계층

- **타입 사이의 포함관계**

  \> 타입 안에 포함된 객체들은 좀 더 상세한 기준으로 묶어 새로운 타입을 정의하면 **이 새로운 타입은 자연스럽게 기존 타입의 부분집합이 된다.**

  - 타입 계층을 구성하는 두 타입 간의 관계에서 더 일반적인 타입을 슈퍼타입(supertype)이라고 부르고 더 특수한 타입을 서브타입(subtype)이라고 부름.
  - 집합을 의미하는 외연의 관점에서 일반적인 타입의 인스턴스 집합은 특수한 타입의 인스턴스 집합을 포함하는 **슈퍼셋**, 반대로 특수한 타입의 인스턴스 집합은 일반적인 타입의 인스턴스 집합에 포함된 **서브셋**
  - **일반화**는 다른 타입을 완전히 포함하거나 내포하는 타입을 식별하는 행위 또는 그 행위의 결과를 가르킨다. **특수화**는 다른 타입 안에 전체적으로 포함되거나 완전히 내포되는 타입을 식별하는 행위 또는 그 행위의 결과를 가리킨다.
  - **슈퍼타입**
    - 집합이 다른 집합의 모든 멤버를 포함
    - 타입 정의가 다른 타입보다 좀 더 일반적
  - **서브타입**
    - 집합에 포함되는 인스턴스들이 더 큰 집합에 포함
    - 타입 정의가 다른 타입보더 좀 더 구체적

- **객체지향 프로그래밍과 타입 계층**

  - 객체의 타입을 결정하는 것은 퍼블릭 인터페이스
  - **슈퍼타입**
    - 서브타입이 정의한 퍼블릭 인터페이스를 일반화시켜 상대적으로 범용적이고 넓은 의미로 정의한 것
  - **서브타입**
    - 슈퍼타입이 정의한 퍼블릭 인터페이스를 특수화시켜 상대적으로 구체적으고 좁은 의미로 정의한 것
  - 여전히 포인트는, 일반적인 타입과 구체적인 타입 간의 관계를 형성하는 기준이 **'퍼블릭 인터페이스'**
  - 더 일반적인 퍼블릭 인터페이스를 가지는 객체들은 더 특수한 퍼블릭 인터페이스를 가지는 객체들의 슈퍼타입
  - 서브타입의 인스턴스는 슈퍼타입의 인스턴스로 간주될 수있다. 이게 바로 **대체가능성**



## 서브클래싱과 서브타이핑

### 그럼, 언제 상속을 사용해야 하는가?

- **상속 관계가 is-a 관계를 모델링하는가?**  
  : 이것은 애플리케이션을 구성하는 어휘에 대한 우리의 관점에 기반, 일반적으로 "자식 클래스는 부모 클래스다." 라고 말해도 이상하지 않다면 상속을 사용할 후보로 간주할 수 있다
- **클라이언트 입장에서 부모 클래스의 타입으로 자식 클래스를 사용해도 무방한가?**  
  : 상속 계층을 사용하는 클라이언트의 입장에서 부모클래스와 자식클래스의 차이점을 몰라야 한다. 이를 자식 클래스와 부모 클래스 사이의 **행동 호환성**이라고 부른다.



### 코드를 통해 is-a 관계와 행동 호환성을 이해하자.

- 어떤 타입 S가 다른 타입 T의 일종이라면 당연히 "타입 S는 타입 T다"라고 말할 수 있어야 한다. 하지만, is-a 관계가 생각처럼 직관적이고 명쾌한 것은 아니다. 

- 예를 들어 설명해보자.  

  ```
  - 팽귄은 새다.
  - 새는 날 수 있다.
  
  public class Bird{
  	public void fly(){ ... }
  	...
  }
  
  public class Penguin extends Bird {
  	...
  }
  ```

  이 코드는 반은 맞고 맞은 틀리다. 왜? 펭귄은 분명 새지만 날 수 없는 새다. 하지만 코드는 분명히 "펭귄은 새고, 따라서 날 수 있다" 라고 주장한다.

  이 예는 어휘적인 정의가 아니라 기대되는 행동에 따라 타입 계층을 잘 구성해야 한다는 사실을 잘 보여준다.

  **슈퍼타입과 서브타입 관계에서는 is-a보다 행동 호환성이 더 중요하다.**

### 행동호환성

- 팽귄이 새가 아니라는 사실을 받아들이기 위한 출발점은 타입이 행동과 관련이 있다는 사실에 주목하는 것.
- 분명 팽귄과 새라는 단어가 풍기는 향기는 두 타입을 is-a 관계로 묶고 싶을 만큼 매혹적인 것이 사실이다. 하지만 새와 펭귄의 서로 다른 행동 방식은 이 둘을 동일한 타입 계층으로 묶어서는 안된다고 강하게 경고한다.
- 여기서 중요한 것은 행동의 호환 여부를 판단하는 기준은 **클라이언트의 관점** 이라는 것이다.
- **그러므로, 여기서 말하는 클라언트의 관점이란 무엇을 말하는 걸까?**  
  : 바로 `interface walker` , `interface flyer` 을 만들어 Bird는 flyer, walker를 상속받도록, `penguin`은` Bird`를 상속받으면서 `interface walker` 를 상속 받아 처리한다.
- 이처럼 인터페이스를 클라이언트의 기대에 따라 분리함으로써 변경에 의해 영향을 제어하는 설계 원칙을 `인터페이스 분리 원칙(Interface Segregation Principle, ISP)` 이라고 부른다.
- 요점은 자연어에 현혹되지 말고 요구사항 속에서 클라이언트가 기대하는 행동에 집중하라는 것이다. 



### 진짜 서브클래싱과 서브타이핑

그래서, 코드 재사용을 목적으로 사용할 때는 **서브클래싱**, 다른 하나는 타입 계층을 구성하기 위해서는 **서브타이핑**

>클래스 상속은 객체의 구현을 정의할 때 이미 정의된 객체의 구현을 바탕으로 한다. 즉, 코드 공유의 방법이다. 이에 비해 인터페이스 상속(서브 타이핑)은 객체가 다른 곳에서 사용될 수 있음을 의미한다. ... 인터페이스 상속 관계를 갖는 경우 프로그램에는 슈퍼타입으로 정의하지만 런타임에 서브타입의 객체로 대체할 수 있다. ... 대부분의 프로그래밍 언어들은 인터페이스와 구현 상속을 구분하고 있지 않지만, 프로그래머들은 실제로 구분해서 사용하고 있다. 스몰토크 프로그래머들은 서브클래스들은 서브클래스를 서브타입으로 사용하고 있고, C++ 프로그래머들은 구체적인 클래스를 정의하고 요청을 보내기보다 추상 클래스의 객체에 메시지를 보내도록 프로그래밍한다. 이렇게 하면 런타임에 구체 클래스의 인스턴스를 대체할 수 있다. 즉, 추상 클래스를 상속한다는 것은 단순한 코드의 재사용을 위한 상속이 아니라 추상 클래스가 정의하고 있는 인터페이스를 상속하겠다는 의미인 것이다.

- 서브타이핑 관게가 유지되기 위해서는 서브타입이 슈퍼타입이 하는 모든 행동을 동일하게 할 수 있어야 한다. 즉, 어떤 타입이 서브타입이 되기 위해서는 `행동 호환성` 을 만족
- 자식 클래스가 부모클래스를 대신할 수 있기 위해서는 자식 클래스가 부모 클래스가 사용되는 모든 문맥에서 자식클래스와 동일하게 행동할 수 있어야 한ㄷ. 그리고 행동 호환성을 만족하는 상속 관계는 부모클래스를 새로운 자식 클래스로 대체하더라도 시스템이 문제없이 동작할 것이라는 것을 보장해야 한다.
- 자식 클래스와 부모 클래스 사이의 행동 호환성은 부모 클래스에 대한 자식 클래스의 **대체 가능성** 을 포함

## 리스코프 치환 원칙

- 행동을 고려하지 않은 두 타입의 이름이 단순히 is-a로 연결 가능하다고 해서 상속 관계로 연결하지 마라. 이름이 아니라 행동이 먼저다. 객체지향과 관련된 대부분의 규칙이 그런 것처럼 is-a 관계 역시 행동이 우선이다.
- 결론적으로 상속이 서브타이핑을 위해 사용될 경우에만 is-a관계다. 서브클래싱을 구현하기 위해 상속을 사용했다면 is-a 관계라고 말할 수 없다.

## 계약에 의한 설계와 서브타이핑

이 부분은 따로 정의한 내용을 참조하는 것이 더욱 도움이 될 것이다.

[여기!]: https://github.com/LenKIM/object-book/tree/master/object8
