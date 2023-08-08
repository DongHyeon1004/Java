# 객체지향 프로그래밍 II

# 상속(inheritance)

## 상속의 정의와 장점

**상속** : 기존의 클래스를 재사용하여 새로운 클래스를 작성하는 것

- 상속을 통해서 클래스를 작성하면 보다 적은 양의 코드로 새로운 클래스를 작성할 수 있고 코드를 공통적으로 관리할 수 있기 때문에 코드의 추가 및 변경이 매우 용이하다.
- 코드의 재사용성을 높이고 코드의 중복을 제거하여 프로그램의 생산성과 유지보수에 크게 기여한다.

```java
상속을 구현하는 방법
새로 작성하고자 하는 클래스의 이름 뒤에 상속받고자 하는 클래스의 이름을 extends와 함께 작성.

class Child **extends Parent** {
			...
}
```

두 클래스는 서로 상속 관계에 있다고 한다.

**조상 클래스** : 상속해주는 클래스, 부모(parent) 클래스, 상위(super) 클래스, 기반(base)클래스

**자손 클래스** : 상속 받는 클래스, 자식(child) 클래스, 하위(sub) 클래스, 파생된(derived) 클래스

**상속계층도(class hierarchy)** : 클래스 간의 상속 관계를 그림으로 표현한 것

프로그램이 커질수록 클래스간의 관계가 복잡해지는데, 상속계층도로 표현하면 클래스간의 관계를 보다 쉽게 이해할 수 있다.

```java
class Parent { }
class Child extends Parent { }
```

![Untitled](%E1%84%80%E1%85%A2%E1%86%A8%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%B5%E1%84%92%E1%85%A3%E1%86%BC%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%86%E1%85%B5%E1%86%BC%20II%206ef6db32535a4e74bc495d8a496648df/Untitled.png)

자손 클래스는 조상 클래스의 모든 멤버를 상속 받기 때문에, Child 클래스는 Parent클래스의 멤버들을 포함한다고 할 수 있다. 다이어그램으로도 표현 가능하다.

![Untitled](%E1%84%80%E1%85%A2%E1%86%A8%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%B5%E1%84%92%E1%85%A3%E1%86%BC%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%86%E1%85%B5%E1%86%BC%20II%206ef6db32535a4e74bc495d8a496648df/Untitled%201.png)

```java
class Parent {
			int age;
}

class Child extends Parent {
			void play() {
					System.out.println("놀자~");
			}
}
```

![Untitled](%E1%84%80%E1%85%A2%E1%86%A8%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%B5%E1%84%92%E1%85%A3%E1%86%BC%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%86%E1%85%B5%E1%86%BC%20II%206ef6db32535a4e74bc495d8a496648df/Untitled%202.png)

- Parent클래스에 age라는 정수형 변수를 멤버변수로 추가하면, 자손 클래스는 조상의 멤버를 모두 상속 받기 때문에, Child클래스는 자동적으로 age라는 멤버변수가 추가된 것과 같은 효과를 얻는다.
- Child클래스에 새로운 멤버인 play()메서드를 추가해도 조상인 Parent클래스는 아무런 영향도 받지 않는다. 자손 클래스가 변경되는 것은 조상 클래스에 아무런 영향을 주지 못한다.

**생성자와 초기화 블럭은 상속되지 않는다. 멤버만 상속된다**

**자손 클래스의 멤버 개수는 항상 조상 클래스와 같거나 많다.**

```java
class Parent { }
class Child extends Parent { }
class Child2 extends Parent { }
class GrandChild extends Child { }
```

![Untitled](%E1%84%80%E1%85%A2%E1%86%A8%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%B5%E1%84%92%E1%85%A3%E1%86%BC%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%86%E1%85%B5%E1%86%BC%20II%206ef6db32535a4e74bc495d8a496648df/Untitled%203.png)

- Child클래스와 Child2클래스는 조상의 멤버를 상속 받기 때문에, Parent클래스 하나만 변경하면 되므로 작업이 간단해진다. 같은 내용의 코드를 한 곳에서 관리함으로써 코드의 중복이 줄어든다.
- 같은 내용의 코드를 하나 이상의 클래스에 중복적으로 추가해야하는 경우 상속관계를 이용해서 코드의 중복을 최소화 해야한다.
- GrandChild클래스는 Child클래스의 모든 멤버, Child클래스가 Parent클래스로부터 상속받은 멤버까지 상속받게 된다. Child클래스는 GrandChild클래스의 조상이고, Parent클래스는 간접 조상이 된다. 그러므로 GrandChild클래스는 Parent클래스와 간접적인 상속관계에 있다고 할 수 있다.

```java
class Tv {
    boolean power;
    int channel;

    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}

class CaptionTv extends Tv {
    boolean caption;
    void displayCaption(String text)
    {
        if (caption)
            System.out.println(text);
    }
}

class CaptionTvTest {
    public static void main(String[] args) {
        CaptionTv ctv = new CaptionTv();
        ctv.channel = 10;
        ctv.channelUp();
        System.out.println(ctv.channel);
        ctv.displayCaption("Hello, World");
        ctv.caption = true;
        ctv.displayCaption("Hello, World");
    }
}
```

**자손 클래스의 인스턴스를 생성하면 조상 클래스의 멤버와 자손 클래스의 멤버가 합쳐진 하나의 인스턴스로 생성된다.**

## 클래스간의 관계 - 포함관계

**포함관계** : 상속 이외에 클래스를 재사용하는 또 다른 방법

**포함 관계를 맺어준다 = 한 클래스의 멤버변수로 다른 클래스 타입의 참조변수를 선언한다**

```java
class Circle {                         class Circle {
			int x;                                 **Point c = new Point();**
			int y;              **-->**                int r;
			int r;                           }
}

class Point {
			int x;
			int y;
}
```

하나의 거대한 클래스를 작성하는 것보다 단위별로 여러 개의 클래스를 작성한 다음, 이 단위 클래스들을 포함관계로 재사용하면 보다 간결하고 손쉽게 클래스를 작성할 수 있다.

## 클래스간의 관계 결정하기

‘-은 -이다(is-a).’와 ‘-은 -을 가지고 있다(has-a)’를 넣어서 문장을 만들어보면 클래스 간의 관계가 보다 명확해진다.

ex)

- 원(Circle)은 점(Point)**이다.** - Circle **is a** Point.
- 원(Circle)은 점(Point)**을 가지고 있다.** - Circle **has a** Point.

두 번째 문장이 더 옳기에 포함관계를 맺어주는 것이 좋다.

**상속관계** : ‘-은 -이다.(is-a)’

**포함관계** : ‘-은 -을 가지고 있다.(has-a)’

```java
class DeckTest {
    public static void main(String[] args) {
        Deck d = new Deck();
        Card c = d.pick(0);
        System.out.println(c);

        d.shuffle();
        c = d.pick(0);
        System.out.println(c);
    }
}

class Deck {
    final int CARD_NUM = 52;
    Card cardArr[] = new Card[CARD_NUM];

    Deck() {
        int i = 0;

        for (int k = Card.KIND_MAX; k > 0; k--)
            for (int n = 0; n < Card.NUM_MAX; n++)
                cardArr[i++] = new Card(k, n + 1);
    }

    Card pick(int index) {
        return cardArr[index];
    }

    Card pick() {
        int index = (int)(Math.random() * CARD_NUM);
        return pick(index);
    }

    void shuffle() {
        for (int i = 0; i < cardArr.length; i++)
        {
            int r = (int)(Math.random() * CARD_NUM);

            Card temp = cardArr[i];
            cardArr[i] = cardArr[r];
            cardArr[r] = temp;
        }
    }
}

class Card {
    static final int KIND_MAX = 4;
    static final int NUM_MAX = 13;

    static final int SPADE = 4;
    static final int DIAMOND = 3;
    static final int HEART = 2;
    static final int CLOVER = 1;
    int kind;
    int number;

    Card() {
        this(SPADE, 1);
    }

    Card(int kind, int number) {
        this.kind = kind;
        this.number = number;
    }

    public String toString() {
        String kinds[] = {"", "CLOVER", "HEART", "DIAMOND", "SPADE"};
        String numbers = "0123456789XJQK";

        return "kind : " + kinds[this.kind] + ", number : " + numbers.charAt(this.number);
    }
}
```

pick(0)을 호출하면, 매개변수 index의 값이 0이 되므로, cardArr[0]에 저장된 Card객체의 주소가 참조변수 c에 저장된다.

예를 들어, index의 값이 0이고, cardArr[0]의 값이 0x200이라면 pick(0)은 다음 과정을 통해 계산된다

return cardArr[index];

→ return cardArr[0];

→ return 0x200;

그래서 참조변수 c에 cardArr[0]에 저장된 Card인스턴스의 주소가 저장된다.

## 단일 상속(single inheritance)

자바에서는 오직 단일 상속만을 허용하기 때문에 둘 이상의 클래스로부터 상속을 받을 수 없다.

```java
class TVCR extends TV, VCR {  // 에러. 조상은 하나만 허용.
			...
{
```

다중 상속을 허용할 경우 여러 클래스로부터 상속 받을 수 있기 때문에 복합적인 기능을 가진 클래스를 쉽게 작성할 수 있지만, 클래스간의 관계가 매우 복잡해지고, 서로 다른 클래스로부터 상속 받은 멤버간의 이름이 같은 경우 구별할 수 있는 방법이 없다.

단일 상속의 경우 하나의 조상 클래스만을 가질 수 있기 때문에 다중 상속에 비해 불편하지만, 클래스 간의 관계가 보다 명확해지고 코드를 더욱 신뢰할 수 있게 만들어준다.

```java
class Tv {
    boolean power;
    int channel;
    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}

class VCR {
    boolean power;
    int counter = 0;
    void power() { power = !power; }
    void play() { /*내용생략*/}
    void stop() { /*내용생략*/}
    void rew() { /*내용생략*/}
    void ff() { /*내용생략*/}
}

class TVCR extends Tv {
    VCR vcr = new VCR();

    void play() {
        vcr.play();
    }

    void stop() {
        vcr.stop();
    }

    void rew() {
        vcr.rew();
    }

    void ff() {
        vcr.ff();
    }
}
```

다중 상속을 허용하지 않으므로 Tv클래스를 조상으로 하고, VCR클래스는 TVCR클래스에 포함시켰다. 그리고 TVCR클래스에 VCR클래스의 메서드와 일치하는 선언부를 가진 메서드를 선언하고 내용은 VCR클래스의 것을 호출해서 사용하도록 했다.

외부적으로는 TVCR클래스의 인스턴스를 사용하는 것처럼 보이지만 내부적으로는 VCR클래스의 인스턴스를 생성해서 사용하는 것이다.

## Object클래스 - 모든 클래스의 조상

**Object클래스** : 모든 클래스 상속계층도의 최상위에 있는 조상 클래스

다른 클래스로부터 상속 받지 않는 모든 클래스들은 자동적으로 Object클래스로부터 상속받게 함으로써 가능하다.

```java
class Tv {
			...
}

//컴파일시 자동적으로 extends Object를 추가한다.
class Tv **extends Object** {
			...
}
```