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

![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/7-1.png)

자손 클래스는 조상 클래스의 모든 멤버를 상속 받기 때문에, Child 클래스는 Parent클래스의 멤버들을 포함한다고 할 수 있다. 다이어그램으로도 표현 가능하다.

![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/7-2.png)

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

![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/7-3.png)

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

![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/7-4.png)

- Child클래스와 Child2클래스는 조상의 멤버를 상속 받기 때문에, Parent클래스 하나만 변경하면 되므로 작업이 간단해진다. 같은 내용의 코드를 한 곳에서 관리함으로써 코드의 중복이 줄어든다.
- 같은 내용의 코드를 하나 이상의 클래스에 중복적으로 추가해야하는 경우 상속관계를 이용해서 코드의 중복을 최소화 해야한다.
- GrandChild클래스는 Child클래스의 모든 멤버, Child클래스가 Parent클래스로부터 상속받은 멤버까지 상속받게 된다. Child클래스는 GrandChild클래스의 조상이고, Parent클래스는 간접 조상이 된다. 그러므로 GrandChild클래스는 Parent클래스와 간접적인 상속관계에 있다고 할 수 있다.

```java
//ex1
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

실행결과
11
Hello, World
```

**자손 클래스의 인스턴스를 생성하면 조상 클래스의 멤버와 자손 클래스의 멤버가 합쳐진 하나의 인스턴스로 생성된다.**

## 클래스간의 관계 - 포함관계

**포함관계** : 상속 이외에 클래스를 재사용하는 또 다른 방법

**포함 관계를 맺어준다 = 한 클래스의 멤버변수로 다른 클래스 타입의 참조변수를 선언한다**

```java
class Circle {                         class Circle {
    int x;                                 Point c = new Point();
    int y;                -->              int r;
    int r;                             }
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
//ex2
class DrawShape {
    public static void main(String[] args) {
        Point p[] = { new Point(100, 100),
                new Point(140, 50),
                new Point(200, 100)};

        Triangle t = new Triangle(p);
        Circle c = new Circle(new Point(150,150), 50);

        t.draw();
        c.draw();
    }
}

class Shape {
    String color = "black";
    void draw() {
        System.out.printf("[color = %s]%n", color);
    }
}

class Point {
    int x;
    int y;

    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
    Point() {
        this(0,0);
    }

    String getXY() {
        return "(" + x + "," + y + ")";
    }
}

class Circle extends Shape {
    Point center;
    int r;

    Circle() {
        this(new Point(0,0), 100);
    }
    Circle(Point center, int r) {
        this.center = center;
        this.r = r;
    }

    void draw() {
        System.out.printf("[center = (%d, %d), r = %d, color = %s]%n", center.x, center.y, r, color);
    }
}

class Triangle extends Shape {
    Point p[] = new Point[3];

    Triangle(Point p[]) {
        this.p = p;
    }

    void draw() {
        System.out.printf("[p1 = %s, p2 = %s p3 = %s, color = %s]%n", p[0].getXY(), p[1].getXY(), p[2].getXY(), color);
    }
}

실행결과
[p1(100,100), p2(140,50), p3(200,100), color = black]
[center = (150, 150), r = 50, color = black]
```

```java
//ex3
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

실행결과
kind : SPADE, number : 1
kind : HEART, number : 7
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
//ex4
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

자동적으로 추가함으로써 Object클래스가 모든 클래스의 조상이 되도록 한다.

모든 상속계층도의 최상위에는 Object클래스가 위치하기 때문에 자바의 모든 클래스들은 Object클래스의 멤버들을 상속 받기 때문에 Object클래스에 정의된 멤버들을 사용할 수 있다.

toString()이나 equals(Object s) 같은 메서드를 따로 정의하지 않고 사용할 수 있었던 이유는 이 메서드들이 Object클래스에 정의된 것들이기 때문이다.-

---

# 오버라이딩(overriding)

## 오버라이딩이란?

**오버라이딩** : 조상 클래스로부터 상속 받은 메서드의 내용을 변경하는 것

상속 받은 메서드를 자손 클래스에 맞게 변경해야하는 경우에 오버라이딩한다.

```java
class Point {
    int x;
    int y;

    String getLocation() {
        return "x : " + x + ", y : " + y;
    }
}

class Point3D extends Point {
    int z;
		
    String getLocation() {    // 오버라이딩
        return "x : " + x + ", y : " + y + ", z : " + z;
    }
}
```

Point3D클래스는 3차원 좌표계의 한 점을 표현하기 위한 것이므로 조상인 Point클래스로부터 상속 받은 getLocation()은 맞지 않기 때문에, 자신에 맞게 z축의 좌표값도 포함하여 반환하도록 오버라이딩 했다.

## 오버라이딩의 조건

자손 클래스에서 오버라이딩하는 메서드는 조상 클래스의 메서드와

- **이름이 같아야 한다.**
- **매개변수가 같아야 한다.**
- **반환타입이 같아야 한다.**

즉, 선언부가 서로 일치해야 한다. 

접근 제어자(access modifier)와 예외(exception)는 제한된 조건 하에서만 다르게 변경 가능하다.

1. **접근 제어자는 조상 클래스의 메서드보다 좁은 범위로 변경 할 수 없다.**
    
    만약 조상 클래스에 정의된 메서드의 접근 제어자가 protected라면, 오버라이딩하는 자손 클래스의 메서드는 접근 제어가자 protected / public 이어야 한다. 대부분의 경우 같은 범위의 접근 제어자를 사용한다.
    
    public → protected → (default) → private
    

1. **조상 클래스의 메서드보다 많은 수의 예외를 선언할 수 없다.**

```java
class Parent {
    void parentMethod() throws IOException, SQLException {
        ...
    }
}
    
class Child extends Parent {
    void parentMethod() throws IOException {
        ...
    }
}
```
    
    Child클래스의 parentMethod()에 선언된 예외의 개수가 조상인 Parent클래스의 parentMethod()에 선언된 예외의 개수보다 적으므로 바르게 오버라이딩 됐다.
    
```java
class Parent {
    void parentMethod() throws IOException, SQLException {
        ...
    }
}
    
class Child extends Parent {
    void parentMethod() throws Exception {
        ...
    }
}
```
    
단순히 선언된 예외의 개수의 문제가 아니다.
    
    분명히 조상 클래스에 정의된 메서드보다 적은 개수의 예외를 선언한 것처럼 보이지만 Exception은 모든 예외의 최고 조상이므로 가장 많은 개수의 예외를 던질 수 있도록 선언한 것이다.
    
    조건을 만족시키지 못하는 잘못된 오버라이딩이다.
    
3. **인스턴스메서드를 static메서드로 또는 그 반대로 변경할 수 없다.**

## 오버로딩 vs 오버라이딩

**오버로딩(overloading)** : 기존에 없는 새로운 메서드를 정의하는 것

**오버라이딩(overriding)** : 상속 받은 메서드의 내용을 변경하는 것

```java
class Parent {
    void parentMethod() {}
}

class Child extends Parent {
    void parentMethod() {} // 오버라이딩
    void parentMethod(int i) {} // 오버로딩
		
    void childMethod() {}
    void childMethod(int i) {} // 오버로딩
    void childMethod() {} // 오류.
}
```

## super

**super** : 자손 클래스에서 조상 클래스로부터 상속 받은 멤버를 참조하는데 사용되는 참조 변수

- 상속 받은 멤버와 자신의 이름이 같을 때 super를 붙여서 구분할 수 있다.
- 조상 클래스로부터 상속 받은 멤버도 자손 클래스 자신의 멤버이므로 super대신 this를 사용할 수 있지만, 조상 클래스의 멤버와 자손 클래스의 멤버가 중복 정의되어 서로 구별해야 하는 경우에만 super를 사용하는 것이 좋다.
- this와 마찬가지로 super 역시 static메서드에서는 사용할 수 없고 인스턴스메서드에서만 사용할 수 있다.

```java
//ex5
class SuperTest {
    public static void main(String[] args) {
        Child c = new Child();
        c.method();
    }
}

class Parent {
    int x = 10;
}

class Child extends Parent {
    int x = 20;
    void method() {
        System.out.println("x = " + x);  
        System.out.println("this.x = " + this.x);  
        System.out.println("super.x = " + super.x);  
    }
}

실행결과
x = 10
this.x = 10
super.x = 10
```

이 경우 모두 같은 변수를 의미하므로 모두 같은 값이 출력된다.

```java
//ex5
class SuperTest {
    public static void main(String[] args) {
        Child c = new Child();
        c.method();
    }
}

class Parent {
    int x = 10;
}

class Child extends Parent {
    void method() {
        System.out.println("x = " + x);
        System.out.println("this.x = " + this.x);
        System.out.println("super.x = " + super.x);
    }
}

실행결과
x = 20
this.x = 20
super.x = 10
```

조상 클래스에 선언된 멤버변수와 같은 이름의 멤버변수를 자손 클래스에서 중복해서 정의하는 것이 가능하며 참조변수 super를 이용해 서로 구분할 수 있다.

변수만이 아니라 메서드 역시 super를 써서 호출할 수 있다. 특히 조상 클래스의 메서드를 자손 클래스에서 오버라이딩한 경우에 super를 사용한다.

 

## super( ) - 조상 클래스의 생성자

- this()와 마찬가지로 super()역시 생성자인데 this()는 같은 클래스의 달느 생성자를 호출하는데 사용되지만, super()는 조상 클래스의 생성자를 호출하는데 사용된다.
- 자손 클래스의 인스턴스를 생성하면, 자손의 멤버와 조상의 멤버가 모두 합쳐진 하나의 인스턴스가 생성된다. 이 때 조상 클래스 멤버의 초기화 작업이 수행되어야 하기 때문에 자손 클래스의 생성자에서 조상 클래스의 생성자가 호출되어야 한다.
- 자손 클래스의 멤버가 조상 클래스의 멤버를 사용할 수도 있으므로 조상의 멤버들이 먼저 초기화 되어 있어야 하기 때문에 생성자의 첫 줄에서 조상 클래스의 생성자를 호출해야 한다.
- **Object클래스를 제외한 모든 클래스의 생성자 첫 줄에 생성자, this() / super()를 호출해야 한다. 그렇지 않으면 컴파일러가 자동적으로 super(); 를 생성자의 첫 줄에 삽입한다.**

```java
//ex7
class PointTest {
    public static void main(String[] args) {
        Point3D p3 = new Point3D(1,2,3);
    }
}

class Point {
    int x, y;

    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    String getLocation() {
        return "x : " + x + ", y : " + y;
    }
}

class Point3D extends Point {
    int z;

    Point3D(int x, int y, int z) {
        // 컴파일러가 여기에 super(); 를 삽입한다.
        this.x = x;
        this.y = y;
        this.z = z;
    }

    String getLocation() {
        return "x : " + x + ", y : " + y + ", z : " + z;
    }
}

실행결과
Point()를 찾을 수 없다는 내용의 컴파일 에러 발생.
```

Point3D클래스의 인스턴스를 생성하면, 생성자 Point3D(int x, int y, int z)가 호출되면서 첫 문장인 super();를 수행하게 되고, super()는 Point3D의 조상인 Point클래스의 기본 생성자인 Point()를 뜻하므로 Point()가 호출된다.

하지만 Point클래스에 생성자 Point()가 정의되어 있지 않기 때문에 컴파일 에러가 발생한다. 에러를 수정하기 위해서는 Point()클래스에 생성자 Point()를 추가해주던가, 생성자 Point(int x, int y, int z)의 첫 줄에서 Point(int x, int y, int z)를 호출하도록 변경하면 된다.

```java
Point 3D(int x, int y, int z) {
			**super(x, y);**  // 조상클래스의 생성자 Point(int x, int y) 호출
			this.z = z;
}
```

**조상 클래스의 멤버변수는 조상의 생성자에 의해 초기화 되도록 해야 하는 것이다.**

```java
//ex8
class PointTest2 {
    public static void main(String[] args) {
        Point3D p3 = new Point3D();
        System.out.println("p3.x = " + p3.x);
        System.out.println("p3.y = " + p3.y);
        System.out.println("p3.z = " + p3.z);
    }
}

class Point {
    int x = 10;
    int y = 20;

    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

class Point3D extends Point {
    int z = 30;

    Point3D() {
        this(100, 200, 300);
    }

    Point3D(int x, int y, int z) {
        super(x, y);
        this.z = z;
    }
}

실행결과
p3.x = 100
p3.y = 200
p3.z = 300
```

---

# package와 import

## 패키지(package)

**패키지** : 클래스의 묶음

- 패키지에는 클래스 / 인터페이스를 포함시킬 수 있으며, 서로 관련된 클래스들끼리 그룹 단위로 묶어 놓음으로써클래스를 효율적으로 관리할 수 있다.
- 같은 이름의 클래스 일지라도 서로 다른 패키지에 존재하는 것이 가능하므로, 자신만의 패키지 체계를 유지함으로써 다른 개발자가 개발한 클래스 라이브러리의 클래스와 이름이 충돌하는 것을 피할 수 있다.
- **클래스가 물리적으로 하나의 클래스파일(.class)인 것처럼 패키지는 물리적으로 하나의 디렉토리이다.** 그래서 어떤 패키지에 속한 클래스는 해당 디렉토리에 존재하는 클래스파일(.class)이어야 한다.
- 디렉토리가 하위 디렉토리를 가질 수 있는 것처럼, 패키지도 다른 패키지를 포함할 수 있으며 점 ‘.’으로 구분된다.

**하나의 소스파일에는 첫 번째 문장으로 단 한 번의 패키지 선언만을 허용한다.**

**모든 클래스는 반드시 하나의 패키지에 속해야 한다.**

**패키지는 점(.)을 구분자로 하여 계층구조로 구성할 수 있다.**

**패키지는 물리적으로 클래스 파일(.class)을 포함하는 하나의 디렉토리이다.**

## 패키지의 선언

```java
// 패키지 선언 방법
package 패키지명;
```

- 패키지 선언문은 반드시 소스파일에서 주석과 공백을 제외한 첫 번째 문장이어야 하며, 하나의 소스파일에 단 한번만 선언될 수 있다.
- 해당 소스파일에 포함된 모든 클래스나 인터페이스는 선언된 패키지에 속하게 된다.
- 패키지명은 대소문자를 모두 허용하지만, 클래스명과 쉽게 구분하기 위해서 소문자로 하는 것을 원칙으로 한다.
- 소스파일에 자신이 속할 패키지를 지정하지 않은 클래스는 자동적으로 이름 없는 패키지(unnamed package)에 속하게 된다.

```java
//ex9
package com.codechobo.book;

class PackageTest {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

- -d 옵션을 추가하여 컴파일을 한다.
    
    **C:\jdk1.8\work>javac -d . packageTest.java**
    
- -d 옵션은 소스파일에 지정된 경로를 통해 패키지의 위치를 찾아서 클래스파일을 생성하는데 지정된 패키지와 일치하는 디렉토리가 존재하지 않는다면 자동적으로 생성한다.
- -d 옵션 뒤에는 해당 패키지의 루트(root)디렉토리의 경로를 적어준다.

## import문

**import문의 역할** : 컴파일러에게 소스파일에 사용된 클래스의 패키지에 대한 정보를 제공하는 것

- 클래스의 코드를 작성하기 전에 import문으로 사용하고자 하는 클래스의 패키지를 미리 명시해주면 소스 코드에 사용되는 클래스 이름에서 패키지명은 생략할 수 있다.
- 컴파일 시에 컴파일러는 import문을 통해 소스파일에 사용된 클래스들의 패키지를 알아 낸 다음, 모든 클래스이름 앞에 패키지명을 붙여 준다.

## import문의 선언

모든 소스파일(.java)에서 import문은 package문 다음에, 그리고 클래스 선언문 이전에 위치해야 한다. import문은 package문과 달리 한 소스파일에 여러 번 선언할 수 있다.

```java
일반적인 소스파일(*.java)의 구성은 다음의 순서로 되어 있다.
1. package문
2. import문
3. 클래스 선언

// import문 선언 방법
import 패키지명.클래스명;
	또는
import 패키지명.*;
```

같은 패키지에서 여러 개의 클래스가 사용될 때, 클래스 이름을 지정해주는 대신 *****을 사용하면, 컴파일러는 해당 패키지에서 일치하는 클래스이름을 찾아야 하는 수고를 더 하지만, 실행 시 **성능상의 차이는 전혀 없다.**

한 패키지에서 여러 클래스를 사용하는 경우 **패키지명.*** 과 같이 하는 것이 편리하지만, import하는 패키지의 수가 많을 때는 어느 클래스가 어느 패키지에 속하는지 구별하기 어렵다는 단점이 있다.

import문에서 클래스의 이름 대신 ***** 을 사용하는 것이 하위 패키지의 클래스까지 포함하는 것은 아니다.

```java
//ex10
import java.text.SimpleDateFormat;
import java.util.Date;

class ImportTest {
    public static void main(String[] args) {
        Date today = new Date();

        SimpleDateFormat date = new SimpleDateFormat("yyyy/MM/dd");
        SimpleDateFormat time = new SimpleDateFormat("hh:mm::ss a");

        System.out.println("오늘 날짜는 " + date.format(today));
        System.out.println("현재 시간은 " + date.format(today));
    }
}

실행결과
현재 날짜와 시간이 출력된다.
```

import문으로 패키지를 지정하지 않으면 모든 클래스 이름 앞에 패키지명을 반드시 붙여야 하지만, 같은 패키지 내의 클래스들은 import문을 지정하지 않고도 패키지명을 생략할 수 있다.

```java
import java.lang.*;
```

모든 소스파일에는 묵시적으로 위의 import문이 선언되어 있기 때문에, System / String같은 java.lang패키지의 클래스들을 패키지명 없이 사용할 수 있다.

java.lang 패키지는 매우 빈번히 사용되는 중요한 클래스들이 속한 패키지이기 때문에 따로 import문으로 지정하지 않아도 되도록 한 것이다.

## static import문

static import문을 사용하면 static멤버를 호출할 때 클래스 이름을 생략할 수 있다. 

특정 클래스의 static멤버를 자주 사용할 때 편리하고, 코드도 간결해진다.

```java
import static java.lang.Integer.*; // Integer클래스의 모든 static 메서드.
import static java.lang.Math.random; // Math.random()만.
import static java.lang.System.out; // System.out을 out만으로 참조 가능.

System.out.println(Math.random()); --> out.println(random());
```

```java
//ex11
import static java.lang.System.out;
import static java.lang.Math.*;

class StaticImportEx1 {
    public static void main(String[] args) {
        //System.out.println(Math.random());
        out.println(random());

        //System.out.println("Math.PI : " + Math.PI);
        out.println("Math.PI : " + PI);
    }
}

실행결과
0.6372776821515502
Math.PI : 3.141592653589793
```

---

# 제어자(modifier)

## 제어자란?

**제어자** : 클래스, 변수 또는 메서드의 선언부에 함께 사용되어 부가적인 의미를 부여함.

- **접근 제어자** : **pubilc, protected, default, private**
- **그 외 제어자 : static, final, abstract, native, transient, sychronized, volatile, strictfp**

제어자는 하나의 대상에 대해서 여러 제어자를 조합하여 사용하는 것이 가능하지만, 접근 제어자는 한 번에 네 가지 중 하나만 선택해서 사용할 수 있다.

## static - 클래스의, 공통적인

- **static이 사용될 수 있는 곳 - 멤버변수, 메서드, 초기화 블럭**
- 인스턴스변수는 하나의 클래스로부터 생성됐더라도 각기 다른 값을 유지하지만, 클래스변수(static멤버변수)는 인스턴스에 관계없이 같은 값을 갖는다. 하나의 변수를 모든 인스턴스가 공유하기 때문이다.
- static이 붙은 멤버변수와 메서드, 그리고 초기화 블럭은 인스턴스가 아닌 클래스에 관게된 것이기 때문에 인스턴스를 생성하지 않고도 사용할 수 있다.
- 인스턴스메서드와 static메서드의 근본적인 차이는 메서드 내에서 인스턴스 멤버를 사용하는가의 여부에 있다.
- static메서드로 하는 것이 인스턴스를 생성하지 않고도 호출이 가능해서 더 편리하고 속도도 빠르다.

## final - 마지막의, 변경될 수 없는

- **fianl이 사용될 수 있는 곳 - 클래스, 메서드, 멤버변수 지역변수**
- 변수에 사용되면 값을 변경할 수 없는 상수가 되며, 메서드에 사용되면 오버라이딩을 할 수 없게 되고 클래스에 사용되면 자신을 확장하는 자손클래스를 정의하지 못하게 되어, 다른 클래스의 조상이 될 수 없다.

**생성자를 이용한 final멤버 변수의 초기화**

- 클래스 내에 매개변수를 갖는 생성자를 선언하여, 인스턴스를 생성할 때 final이 붙은 멤버변수를 초기화하는데 필요한 값을 생성자의 매개변수로부터 제공받는 것이다.
- 이 기능을 활용하면 각 인스턴스마다 final이 붙은 멤버변수가 다른 값을 갖도록 하는 것이 가능하다.

```java
//ex12
class Card {
    final int NUMBER;
    final String KIND;
    static int width = 100;
    static int height = 200;

    Card(String kind, int num) {
        KIND = kind;
        NUMBER = num;
    }

    Card() {
        this("HEART", 1);
    }

    public String toString() {
        return KIND + " " + NUMBER;
    }
}

class FinalCardTest {
    public static void main(String[] args) {
        Card c = new Card("HEART", 10);
        //c.NUMBER = 5; 에러발생
        System.out.println(c.KIND);
        System.out.println(c.NUMBER);
        System.out.println(c);
    }
}

실행결과
HEART
10
HEART 10
```

## abstract - 추상의, 미완성의

- **abstract가 사용될 수 있는 곳 - 클래스, 메서드**
- 메서드의 선언부만 작성하고 실제 수행내용은 구현하지 않은 추상 메서드를 선언하는데 사용된다.
- 클래스에 사용되어 클래스 내에 추상메서드가 존재한다는 것을 쉽게 알 수 있게 한다.
- 추상 클래스는 아직 완성되지 않은 메서드가 존재하는 미완성 설계도이므로 인스턴스를 생성할 수 없다.

```java
public abstract class WindowAdapter
	implements WindowListener, WindowStateListener, WindowFocusListener {
		public void windowOpend(WindowEvent e) { }
		public void windowClosing(WindowEvent e) { }
		public void windowClosed(WindowEvent e) { }
		public void windowIconified(WindowEvent e) { }
					...
} 
```

java.awt.event.WindowAdapter는 아무런 내용이 없는 메서드들만 정의되어 있다. 이런 클래스는 인스턴스를 생성해봐야 할 수 있는 것이 아무것도 없기 때문에 완성된 클래스지만 인스턴스를 생성하지 못하게 클래스 앞에 제어자 **abstract**를 붙여 놓은 것이다.

이 클래스 자체로는 쓸모 없지만, 다른 클래스가 이 클래스를 상속받아서 일부의 원하는 메서드만 오버라이딩해도 된다는 장점이 있다.

## 접근 제어자(access modifier)

- **접근 제어자가 사용될 수 있는 곳 - 클래스, 멤버변수, 메서드, 생성자**
    
    **private** : 같은 클래스 내에서만 접근 가능
    
    **default** : 같은 패키지 내에서만 접근 가능
    
    **protected** : 같은 패키지 내에서, 그리고 다른 패키지의 자손클래스에서 접근 가능
    
    **public** : 접근 제한이 전혀 없음
    
    **public > protected > (default) > private**
    
- **클래스** : public, (default) 사용 가능
    
    **메서드, 멤버변수** : public, protected, (default), private
    
    **지역변수** : 없음
    

**접근 제어자를 이용한 캡슐화**

접근 제어자를 사용하는 이유

1. 클래스나 멤버, 주로 멤버에 접근 제어자를 사용하는 이유는 클래스의 내부에 선언된 데이터를 보호하기 위해서다.
    
    **데이터 감추기(data hiding)** : 데이터가 유효한 값을 유지하도록, 또는 비밀 번화와 같은 데이터를 외부에서 함부로 변경하지 못하도록 하기 위해서 외부로부터의 접근을 제한하는 것
    
2. 클래스 내에서만 사용되는, 내부 작업을 위해 임시로 사용되는 멤버변수나 부분작업을 처리하기 위한 메서드 등의 멤버들을 클래스 내부에 감추기 위해서다. 
    
    외부에서 접근할 필요가 없는 멤버들을 private으로 지정하여 외부에 노출시키지 않음으로써 복잡성을 줄일 수 있다.
    

```java
public class Time {
    private int hour;
    private int minute;
    private int second;

    public int getHour() { return hour; }
    public void setHour(int hour) {
        if (hour < 0 || hour > 23) return;
            this.hour = hour;
    }
    public int getMinute() { return minute; }
    public void setMinute(int minute) {
        if (minute < 0 || minute > 59) return;
            this.minute = minute;
    }
    public int getSecond() { return second; }
    public void setSecond(int second) {
        if (second < 0 || second > 59) return;
            this.second = second;
    }
}
```

만약 상속을 통해 확장될 것이 예상되는 클래스라면 멤버에 접근 제한을 주되 자손 클래스에서 접근하는 것이 가능하도록 하기 위해 private대신 protected를 사용한다.

보통 멤버변수의 값을 읽는 메서드의 이름을 **get멤버변수이름**으로 하고, 멤버변수의 값을 변경하는 메서드의 이름을 **set멤버변수이름**으로 한다. 

**겟터(getter)** : get으로 시작하는 메서드

**셋터(setter)** : set으로 시작하는 메서드

```java
//ex13
public class TimeTest {
    public static void main(String[] args) {
        Time t = new Time(12, 35, 30);
        System.out.println(t);
        // t.hour = 13;  에러 발생 제어자가 private
        t.setHour(t.getHour() + 1);
        System.out.println(t);
    }
}

class Time {
    private int hour, minute, second;

    Time(int hour, int minute, int second) {
        setHour(hour);
        setMinute(minute);
        setSecond(second);
    }

    public int getHour() { return hour; }
    public void setHour(int Hour) {
        if (hour < 0 || hour > 23) return;
        this.hour = hour;
    }
    public int getMinute() { return minute; }
    public void setMinute(int minute) {
        if (minute < 0 || minute > 59) return;
        this.minute = minute;
    }
    public int getSecond() { return second; }
    public void setSecond(int second) {
        if (second < 0 || second > 59) return;
        this.second = second;
    }
    public String toString() {
        return hour + ":" + minute + ":" + second;
    }
}

실행결과
12:35:30
13:35:30
```

**생성자의 접근 제어자**

생성자에 접근 제어자를 사용함으로써 인스턴스의 생성을 제한할 수 있다.

생성자의 접근 제어자를 private로 지정하면, 외부에서 생성자에 접근할 수 없으므로 인스턴스를 생성할 수 없지만, 클래스 내부에서는 인스턴스를 생성할 수 있다.

```java
class Singleton {
    ...
    private static Singleton s = new Singleton();
    private Singleton() {
        ...
    }

    // 인스턴스를 생성하지 않고도 호출할 수 있어야 하므로 static이어야 한다.
    public static Singleton getInstance() {
        return s;
    }
    ...
}
```

생성자를 통해 직접 인스턴스를 생성하지 못하게 하고 public메서드를 통해 인스턴스에 접근하게 함으로써 사용할 수 있는 인스턴스의 개수를 제한할 수 있다.

자손 클래스의 인스턴스를 생성할 때 조상 클래스의 생성자를 호출해야만 하는데, 생성자의 접근 제어자가 private이면 자손 클래스에서 호출하는 것이 불가능 하기 때문에 생성자가 private인 클래스는 다른 클래스의 조상이 될 수 없다.

그래서 앞에 final을 더 추가해 상속할 수 없는 클래스라는 것을 알리는 것이 좋다.

```java
//ex14
final class Singleton {
    private static Singleton s = new Singleton();

    private Singleton() {
        // ...
    }

    public static Singleton getInstance() {
        if (s == null)
            s = new Singleton();

        return s;
    }
}

class SingletonTest {
    public static void main(String[] args) {
        // Singleton s = new Singleton();  에러 발생 접근 제어자가 private
        Singleton s = Singleton.getInstance();
    }
}
```

## 제어자(modifier)의 조합

클래스 - public, (default), final, abstract

메서드 - 모든 접근 제어자, final, abstract, static

멤버변수 - 모든 접근 제어자, final, static

지역변수 - final

**제어자를 조합해서 사용 시 주의해야 할 사항**

1. **메서드에 static과 abstract를 함께 사용할 수 없다.**
    
    static메서드는 몸통이 있는 메서드에만 사용 가능하다
    
2. **클래스에 abstract와 fianl을 동시에 사용할 수 없다.**
    
    클래스에 사용되는 final은 클래스를 확장할 수 없다는 의미이고, abstract는 상속을 통해서 완성되어야 한다는 의미이므로 서로 모순되기 때문이다.
    

1. **abstract메서드의 접근 제어자가 private일 수 없다.**
    
    abstract메서드는 자손 클래스에서 구현해주어야 하는데 접근 제어자가 private이면, 자손 클래스에서 접근할 수 없기 때문이다.
    

1. **메서드에 private과 final을 같이 사용할 필요는 없다.**
    
    접근 제어자가 private인 메서드는 오버라이딩될 수 없기 때문이다. 이 둘 중 하나만 사용해도 의미가 충분하다.
    

---

# 다형성(polymorphism)

## 다형성이란?

**다형성** : 여러 가지 형태를 가질 수 있는 능력

조상 클래스 타입의 참조변수로 자손 클래스의 인스턴스를 참조할 수 있도록 하여 구현했다.

```java
class Tv {
    boolean power;
    int channel;

    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}

class CaptionTv extends Tv {
    String text;
    void cpation() { /*내용생략*/ }
}
```

클래스 Tv와 CaptionTv는 서로 상속관계에 있다.

```java
Tv t = new Tv();
CaptionTv c = new CaptionTv();
```

지금까지는 생성된 인스턴스를 다루기 위해서, 인스턴스의 타입과 일치하는 타입의 참조변수만을 사용했다.

```java
Tv t = new CaptionTv();
```

인스턴스의 타입과 참조변수의 타입이 일치하는 것이 보통이지만, 클래스가 서로 상속관계에 있을 경우, 조상 클래스 타입의 참조변수로 자손 클래스의 인스턴스를 참조하도록 하는 것이 가능하다.

**인스턴스를 같은 타입의 참조변수로 참조하는 것과 조상 타입의 참조변수로 참조하는 것의 차이점**

```java
CaptionTv c = new CaptionTv();
Tv t = new CaptionTv();
```

실제 인스턴스가 CaptionTv타입이라 할지라도, 참조 변수 t로는 CpationTv인스턴스의 모든 멤버를 사용할 수 없다.

Tv타입의 참조변수로는 CaptionTv인스턴스 중에서 Tv클래스의 멤버들(상속 받은 멤버 포함)만 사용할 수 있다. 따라서, 생성된 CaptionTv인스턴스의 멤버 중 Tv클래스에 정의 되지 않은 멤버, text와 caption()은 참조변수 t로 사용이 불가능하다.

**둘 다 같은 타입의 인스턴스지만 참조변수의 타입에 따라 사용할 수 있는 멤버의 개수가 달라진다.**

```java
CaptionTv c = new Tv(); // 컴파일 에러 발생.
```

실제 인스턴스인 Tv의 맴버 개수보다 참조변수 c가 사용할 수 있는 멤버 개수가 더 많기 때문에 컴파일 에러가 발생한다.

자손타입의 참조변수로 조상타입의 인스턴스를 참조하는 것은 존재하지 않는 멤버를 사용하고자 할 가능성이 있으므로 허용하지 않는다.

**참조변수가 사용할 수 있는 멤버의 개수는 인스턴스의 멤버 개수보다 같거나 적어야 한다.**

**조상타입의 참조변수로 자손타입의 인스턴스를 참조할 수 있다.**

**반대로 자손타입의 참조변수로 조상타입의 인스턴스를 참조할 수는 없다.**

## 참조변수의 형변환

참조변수의 형변환은 서로 상속관계에 있는 클래스 사이에서만 가능하기 때문에 자손타입의 참조변수를 조상타입의 참조변수로, 조상타입의 참조변수를 자손타입의 참조변수로의 형변환만 가능하다.

**자손타입 → 조상타입(Up-casting) : 형변환 생략 가능**

**조상타입 → 자손타입(Down-casting) : 형변환 생략 불가능**

참조변수간의 형변환 역시 캐스트연산자를 사용하며, 괄호( ) 안에 변환하고자 하는 타입의 이름(클래스명)을 적어주면 된다.

```java
class Car {
    String color;
    int door;
    void drive() {
        System.out.println("drive, Brrrr~");
    }
    void stop() {
        System.out.println("stop!!");
    }
}

class FireEngine extends Car {
    void water() {
        System.out.println("water!!");
    }
}

class Ambulance extends Car {
    void siren() {
        System.out.println("siren~~~");
    }
}
```

Car클래스는 FireEngine클래스와 Ambulance클래스의 조상이지만, FireEngine클래스와 Ambulance클래스가 형제관계인건 아니다. 자바에서는 조상과 자식관계만 존재하기 때문에 서로 아무런 관련이 없다.

```java
FireEngine f;
Ambulance a;
a = (Ambulance)f; // 에러. 상속관계가 아닌 클래스간의 형변환 불가
f = (FireEngine)a; // 에러. 상속관계가 아닌 클래스간의 형변환 불가
```

FireEngine타입의 참조변수와 Ambulance타입의 참조변수 간에는 아무런 관계가 없기 때문에 형변환이 불가능하다.

```java
Car car = null;
FireEngine fe = new FireEngine();
FireEngine fe2 = null;

car = fe; // car = (Car)fe;에서 형변환 생략. Up-casting 
fe2 = (FireEngine)car; // 형변환 생략불가. Down-casting
```

**형변환을 생략할 수 있는 경우와 생략할 수 없는 경우에 대한 이유**

Car타입의 참조변수 c가 있다고 가정하면, 참조변수 c가 참조하고 있는 인스턴스는 Car인스턴스이거나 자손인 FireEngine인스턴스일 것이다.

Car타입의 참조변수 c를 Car타입의 조상인 Object타입의 참조변수로 형변환 하는 것은 참조변수가 다룰 수 있는 멤버의 개수가 실제 인스턴스가 갖고 있는 멤버의 개수보다 적을 것이 분명하므로 문제가 되지 않는다. 그래서 형변환을 생략할 수 있도록 한 것이다.

하지만, Car타입의 참조변수 c를 자손인 FireEngine타입으로 변환하는 것은 참조변수가 다룰 수 있는 멤버의 개수를 늘리는 것이므로, 실제 인스턴스의 멤버 개수보다 참조변수가 사용할 수 있는 멤버의 개수가 더 많아지므로 문제가 발생할 가능성이 있다. 그래서 자손타입으로의 형변환은 생략할 수 없다.

- **형변환은 참조변수의 타입을 변환하는 것이지 인스턴스를 변환하는 것은 아니기 때문에 참조변수의 형변환은 인스턴스에 아무런 영향을 미치지 않는다.**
- **단지 참조변수의 형변환을 통해서, 참조하고 있는 인스턴스에서 사용할 수 있는 멤버의 개수를 조절하는 것 뿐이다.**

```java
//ex15
class CastingTest1 {
    public static void main(String[] args) {
        Car car = null;
        FireEngine fe = new FireEngine();
        FireEngine fe2 = null;

        fe.water();
        car = fe;
        // car.water(); 컴파일 에러.
        fe2 = (FireEngine)car;
        fe2.water();
    }
}

class Car {
    String color;
    int door;

    void drive() {
        System.out.println("drive, Brrrr~");
    }

    void stop() {
        System.out.println("stop!!!");
    }
}

class FireEngine extends Car {
    void water() {
        System.out.println("water!!!");
    }
}

실행결과
water!!!
water!!!
```

1. **Car car = null;**
    
    Car타입의 참조변수 car를 선언하고 null로 초기화한다.
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/7-5.png)
    
2. **FireEngine fe = new FrieEngine();**
    
    FireEngine인스턴스를 생성하고 FireEngine타입의 참조변수가 참조하도록 한다.
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/7-6.png)
    
3. **car = fe;**
    
    참조변수 fe가 참조하고 있는 인스턴스를 참조변수 car가 참조하도록 한다. fe의 값(참조하고 있는 인스턴스의 주소)이 car에 저장된다. 자손 → 조상이기 때문에 형변환은 생략된다.
    
    이제 참조변수 car를 통해서도 FireEngine인스턴스를 사용할 수 있지만, fe와는 달리 car는 Car타입이므로 Car클래스의 멤버가 아닌 water()는 사용할 수 없다.
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/7-7.png)
    
4. **fe2 = (FireEngine)car;**
    
    참조변수 car가 참조하고 있는 인스턴스를 참조변수 fe2가 참조하도록 한다. 조상 → 자손이기 때문에 형변환을 생략할 수 없다. fe2에도 FireEngine인스턴스의 주소가 저장된다.
    
    이제 참조변수 fe2를 통해서도 FireEngine인스턴스를 사용할 수 있지만, car와는 달리, fe2는 FireEngine타입이므로 FireEngine인스턴스의 모든 멤버를 사용할 수 있다.
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/7-8.png)
    

```java
//ex16
class CastingTest2 {
    public static void main(String[] args) {
        Car car = new Car();
        Car car2 = null;
        FireEngine fe = null;
			
        car.drive();
        fe = (FireEngine)car; // 컴파일 OK. 실행 시 에러 발생
        fe.drive;
        car2 = fe;
        car2.drive();
    }
}

실행결과
drive, Brrrr~
java.lang.ClassCastException: Car
			at CastingTest2.main(CastingTest2.java:8)
```

컴파일은 성공하지만 fe = (FireEngine)car; 에서 형변환에 오류가 있기 때문에 에러가 발생한다. 캐스트 연산자를 이용해서 조상타입의 참조변수를 자손타입의 참조변수로 형변환한 것이기 때문에 문제가 없어 보이지만, 문제는 참조변수 car가 참조하고 있는 인스턴스가 Car타입의 인스턴스라는 것이다. 조상타입의 인스턴스를 자손타입의 참조변수로 참조하는 것은 혀용되지 않는다.

컴파일 시에는 참조변수간의 타입만 체크하기 때문에 실행 시 생성될 인스턴스의 타입에 대해서는 전혀 알지 못한다.

서로 상속관계에 있는 타입간의 형변환은 양뱡향으로 자유롭게 수행될 수 있으나, **참조변수가 가리키는 인스턴스의 자손타입으로 형변환은 허용되지 않는다.**

**그래서 참조변수가 가리키는 인스턴스의 타입이 무엇인지 확인하는 것이 중요하다.**

## instanceof 연산자

참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 instanceof연산자를 사용한다. 주로 조건문에 사용되며, instanceof의 왼쪽에는 참조변수를 오른쪽에는 타입(클래스명)이 피연산자로 위치한다. 연산의 결과로는 boolean값인 true와 false 중의 하나를 반환한다.

연산 결과가 **true라는 것은 참조변수가 검사한 타입으로 형변환이 가능하다는 것**을 뜻한다.

```java
//ex17
class IntanceofTest {
    public static void main(String[] args) {
        FireEngine fe = new FireEngine();

        if (fe instanceof FireEngine) 
            System.out.println("This is a FireEngine instance.");

        if (fe instanceof Car) 
            System.out.println("This is a Car instance.");

        if (fe instance of Object) 
            System.out.println("This is an Object instance.");

        System.out.println(fe.getClass().getName());
    }
}
class Car { }
class FireEngine extends Car { }

실행결과
This is a FireEngine instance.
This is a Car instance.
This is an Object instance.
FireEngine
```

생성된 인스턴스는 FireEngine타입이지만 FireEngine클래스는 Object클래스와 Car클래스의 자손 클래스이므로 조상의 멤버들을 상속받았기 때문에, FireEngine인스턴스는 Object인스턴스와 Car인스턴스를 포함하고 있는 셈이기 때문에, Object타입과 Car타입의 instanceof연산에서도 true를 결과로 얻는다.

실제 인스턴스와 같은 타입의 instancof연산 이외에 조상타입의 instanceof연산에도 true를 결과로 얻으며, 형변환을 해도 아무런 문제가 없다는 뜻이다.

**참조변수.getClass().getName()** : 참조변수가 가리키는 인스턴스의 클래스 이름을 문자열로 반환

**어떤 타입에 대한 instanceof연산의 결과가 true라는 것은 검사한 타입으로 형변환이 가능하다는 것**

## 참조변수와 인스턴스의 연결

멤버변수가 조상 클래스와 자손 클래스에 중복으로 정의된 경우, 조상타입의 참조변수를 사용했을 때는 조상 클래스에 선언된 멤버변수가 사용되고, 자손타입의 참조변수를 사용했을 때는 자손 클래스에 선언된 멤버변수가 사용된다.

중복 정의되지 않은 경우, 조상타입의 참조변수를 사용했을 때와 자손타입의 참조변수를 사용했을 때의 사용했을 때의 차이는 없다. 중복되지 않은 경우 하나뿐이므로 선택의 여지가 없기 때문이다.

```java
//ex18
class BindingTest {
    public static void main(String[] args) {
        Parent p = new Child();
        Child c = new Child();

        System.out.println("p.x = " + p.x);
        p.method();

        System.out.println("c.x = " + c.x);
        c.method();
    }
}

class Parent {
    int x = 100;

    void method() {
        System.out.println("Parent Method");
    }
}

class Child {
    int x = 200;

    void method() {
        System.out.println("Child Method");
    }
}

실행결과
p.x = 100
Child Method
c.x = 200
Child Method
```

메서드인 method()의 경우 참조변수의 타입에 관계없이 항상 실제 인스턴스의 타입인 Child클래스에 정의된 메서드가 호출되지만, 인스턴스변수인 x는 참조변수의 타입에 따라서 달라진다.

```java
//ex19
class BindingTest2 {
    public static void main(String[] args) {
        Parent p = new Child();
        Child c = new Child();
        
        System.out.println("p.x = " + p.x);
        p.method();
        
        System.out.println("c.x = " + c.x);
        c.method();
    }
}

class Parent {
    int x = 100;
    
    void method() {
        System.out.println("Parent Method");
    }
}

class Child extends Parent { }

실행결과
p.x = 100
Parent Method
c.x = 100
Parent Method
```

Child클래스에는 아무런 멤버도 정의되어 있지 않고 단순히 조상으로부터 멤버들을 상속받는다. 그렇기 때문에 참조변수의 타입에 관계없이 조상의 멤버들을 사용하게 된다.

자손 클래스에서 조상 클래스의 멤버를 중복으로 정의하지 않았을 때는 참조변수의 타입에 따른 변화는 없다. 어느 클래스의 멤버가 호출되어야 할지에 대해 선택의 여지가 없기 때문이다.

참조변수의 타입에 따라 결과가 달라지는 경우는 조상 클래스의 멤버변수와 같은 이름의 멤버변수를 자손 클래스에 중복해서 정의한 경우뿐이다.

```java
//ex20
class BindingTest3 {
    public static void main(String[] args) {
        Parent p = new Child();
        Child c = new Child();

        System.out.println("p.x = " + p.x);
        p.method();

        System.out.println("c.x = " + c.x);
        c.method();
    }
}

class Parent {
    int x = 100;

    void method() {
        System.out.println("Parent Method");
    }
}

class Child extends Parent {
    int x = 200;
    
    void method() {
        System.out.println("x = " + x);
        System.out.println("super.x = " + super.x);
        System.out.println("this.x = " + this.x);
    }
}

실행결과
p.x = 100
x = 200
super.x = 100
this.x = 200

c.x = 200
x = 200
super.x = 100
this.x = 200

```

자손인 Child클래스에서 super.x는 조상 클래스인 Parent에 선언된 인스턴스변수 x를 뜻하며, this.x 또는 x는 Child클래스의 인스턴스변수 x를 뜻한다.

## 매개변수의 다형성

메서드의 매개변수에도 참조변수의 다형적인 특징이 적용된다.

```java
//ex21
class Product {
    int price;
    int bonusPoint;

    Product(int price) {
        this.price = price;
        bonusPoint = (int)(price/10.0);
    }
}

class Tv extends Product {
    Tv() {
        super(100);
    }
    public String toString() { return "Tv"; }
}

class Computer extends Product {
    Computer() { super(200); }
    public String toSrting() { return "Computer"; }
}

class Buyer {
    int money = 1000;
    int bonusPoint = 0;

    void buy(Product p) {
        if (money < p.price)
        {
            System.out.println("잔액이 부족하여 물건을 살 수 없습니다.");
            return;
        }

        money -= p.price;
        bonusPoint += p.bonusPoint;
        System.out.println(p + "을/를 구입하셨습니다.");
    }
}

class PolyArgumentTest {
    public static void main(String[] args) {
        Buyer b = new Buyer();

        b.buy(new Tv());
        b.buy(new Computer());

        System.out.println("현재 남은 돈은 + " + b.money + "만원입니다.");
        System.out.println("현재 보너스 점수는 " + b.bonusPoint + "점입니다.");
    }
}

실행결과
Tv을/를 구입하셨습니다.
Computer을/를 구입하셨습니다.
현재 남은 돈은 700만원입니다.
현재 보너스 점수는 30점입니다.
```

void buy(Product p) {
        money -= p.price;
        bonusPoint += p.bonusPoint;

}

매개변수가 Product타입의 참조변수라는 것은, 메서드의 매개변수로 Product클래스의 자손타입의 참조변수라면 어느 것이나 매개변수로 받아들일 수 있다는 것이다.

PrintStream클래스에 정의되어있는 print(Object)는 매개변수로 Object타입의 변수가 선언되어 있는데 Object는 모든 클래스의 조상이므로 이 메서드의 매개변수로 어떤 타입의 인스턴스도 가능하므로, 이 하나의 메서드로 모든 타입의 인스턴스를 처리할 수 있는 것이다.

## 여러 종류의 객체를 배열로 다루기

조상타입의 참조변수 배열을 사용하면, 공통의 조상을 가진 서로 다른 종류의 객체를 배열로 묶어서 다룰 수 있다. 

또는 묶어서 다루고 싶은 객체들의 상속 관계를 따져서 가장 가까운 공통 조상 클래스 타입의 참조변수 배열을 생성해서 객체들을 저장하면 된다.

```java
//ex22
class Product {
    int price;
    int bonusPoint;

    Product(int price) {
        this.price = price;
        bonusPoint = (int)(price/10.0);
    }

    Product() { }
}

class Tv extends Product {
    Tv() { super(100); }
    public String toString() { return "Tv"; }
}

class Computer extends Product {
    Computer() { super(200); }
    public String toString() { return "Computer"; }
}

class Audio extends Product {
    Audio() { super(50); }
    public String toString() { return "Audio"; }

class Buyer {
    int money = 1000;
    int bonusPoint = 0;
    Product item[] = new Product[10];
    int i = 0;

    void buy(Product p) {
        if (money < p.price)
        {
            System.out.println("잔액이 부족하여 물건을 살 수 없습니다.");
            return;
        }

        money -= p.price;
        bonusPoint += p.bonusPoint;
				item[i++] = p;
        System.out.println(p + "을/를 구입하셨습니다.");
    }

    void summary() {
    int sum = 0;
    String itemList = "";

    for (int i = 0; i < item.lenght; i++) 
    {
        if (item[i] == null) break;
        sum += item[i].price;
        itemList += item[i] + ", ";
    }
    System.out.println("구입하신 물품의 총 금액은 " + sum + "만원입니다.");
    System.out.println("구입하신 제품은 " + itemList + "입니다.");
    }
}

class PolyArgumentTest2 {
    public static void main(String[] args) {
        Buyer b = new Buyer();

        b.buy(new Tv());
        b.buy(new Computer());
				b.buy(new Audio());
				b.summary();
    }
}

실행결과
Tv을/를 구입하셨습니다.
Computer을/를 구입하셨습니다.
Audio을/를 구입하셨습니다.
구입하신 물품의 총 금액은 350만원입니다.
구입하신 제품은 Tv, Computer, Audio, 입니다.
```

Product배열로 구입한 제품들을 저장할 수 있도록 했지만, 배열의 크기가 정해져 있어 정해진 크기 이상의 제품을 구입할 수 없다. 그렇다고 배열의 크기를 무조건 크게 설정할 수도 없는 일이다.

이런 경우, Vector클래스를 사용하면 된다. Vector클래스는 내부적으로 Object타입의 배열을 가지고 있어서, 이 배열에 객체를 추가하거나 제거할 수 있게 작성되어 있고, 배열을 크기를 알아서 관리해 주기 때문에 저장할 인스턴스의 개수에 신경 쓰지 않아도 된다.

```java
public class Vector extends AbstractList
    implements List, Cloneable, java.io.Serializable {
        protected Object elementData[];
        ...
}
```

Vector클래스는 단지 동적으로 크기가 관리되는 객체배열일 뿐이다.

**Vector클래스의 주요 메서드**

- **Vector()**
    
    10개의 객체를 저장할 수 있는 Vector인스턴스를 생성한다.
    
    10개 이상의 인스턴스가 저장되면, 자동으로 크기가 증가된다.
    
- **boolean add(Object o)**
    
    Vector에 객체를 추가한다.
    
    추가에 성공하면 결과값으로 true, 실패하면 false를 반환한다.
    
- **boolean remove(Object o)**
    
    Vector에 저장되어 있는 객체를 제거한다.
    
    제거에 성공하면 결과값으로 true, 실패하면 false를 반환한다.
    
- **boolean isEmpty()**
    
    Vector가 비어있는지 검사한다.
    
    비어있으면 true, 비어있지 않으면 false를 반환한다.
    
- **Object get(int index)**
    
    저장된 위치(index)의 객체를 반환한다.
    
    반환타입이 Object타입이므로 적절한 타입으로의 형변환이 필요하다.
    
- **int size()**
    
    Vector에 저장된 객체의 개수를 반환한다.
    

```java
//ex23
import java.util.*;  // Vector클래스를 사용하기 위함.

class Product {
    int price;
    int bonusPoint;

    Product(int price) {
        this.price = price;
        bonusPoint = (int)(price/10.0);
    }

    Product() {
        price = 0;
        bonusPoint = 0;
    }
}

class Tv extends Product {
    Tv() { super(100); }
    public String toString() { return "Tv"; }
}

class Computer extends Product {
    Computer() { super(200); }
    public String toString() { return "Computer"; }
}

class Audio extends Product {
    Audio() { super(50); }
    public String toString() { return "Audio"; }

class Buyer {
    int money = 1000;
    int bonusPoint = 0;
    Vector item = new Vector();

    void buy(Product p) {
        if (money < p.price)
        {
            System.out.println("잔액이 부족하여 물건을 살 수 없습니다.");
            return;
        }

        money -= p.price;
        bonusPoint += p.bonusPoint;
				item.add(p);
        System.out.println(p + "을/를 구입하셨습니다.");
    }

    void refund(Product p) {
    if (item.remove(p)) {
        money += p.price;
        bounsPoint -= p.bonusPoint;
        System.out.println(p + "을/를 반품하셨습니다.");
    }
    else
        System.out.println("구입하신 제품 중 해당 제품이 없습니다.");
    }

    void summary() {
        int sum = 0;
        String itemList = "";

        if (item.isEmpty()) {
            System.out.println("구입하신 제품이 없습니다.");
            return;
        }

        for (int i = 0; i < item.size(); i++) 
        {
            Product p = (Product)item.get(i);
            sum += p.price;
            itemList += (i == 0) ? "" + p : ", " + p;
        }
        System.out.println("구입하신 물품의 총 금액은 " + sum + "만원입니다.");
        System.out.println("구입하신 제품은 " + itemList + "입니다.");
    }
}

class PolyArgumentTest3 {
    public static void main(String[] args) {
        Buyer b = new Buyer();
        Tv tv = new Tv();
        Computer com = new Computer();
        Audio audio = new Audio();

        b.buy(tv);
        b.buy(com);
        b.buy(audio);
        b.summary();
        System.out.println();
        b.refund(com);
        b.summary();
    }
}

실행결과
Tv을/를 구입하셨습니다.
Computer을/를 구입하셨습니다.
Audio을/를 구입하셨습니다.
구입하신 물품의 총 금액은 350만원입니다.
구입하신 제품은 Tv, Computer, Audio, 입니다.

Computer을/를 반품하셨습니다.
구입하신 물품의 총금액은 150만원입니다.
구입하신 제품은 Tv, Audio입니다.
```

---

# 추상클래스(abstract class)

## 추상클래스란?

추상클래스는 미완성 설계도다.

클래스가 미완성이라는 것은 멤버의 개수에 관계된 것이 아니라, 단지 미완성 메서드(추상메서드)를 포함하고 있다는 의미다.

추상클래스로는 인스턴스를 생성할 수 없고, 상속을 통해서 자손클래스에 의해서만 완성될 수 있다.

추상클래스 자체로는 클래스로서의 역할을 다 못하지만, 새로운 클래스를 작성하는데 있어서 바탕이 되는 조상클래스로서 중요한 의미를 갖는다.

```java
abstract class 클래스이름 {
    ...
}
```

추상클래스는 키워드 abstract만 붙이면 된다. 이 클래스를 사용할 때, 클래스 선언부의 abstract를 보고 이 클래스에는 추상메서드가 있으니 상속을 통해서 구현해주어야 한다는 것을 쉽게 알 수 있다.

추상클래스에도 생성자가 있으며, 멤버변수와 메서드도 가질 수 있다.

## 추상메서드(abstract method)

**추상메서드** : 선언부만 작성하고 구현부는 작성하지 않은 채로 남겨 둔 것. 설계만 해 놓고 실제 수행될 내용을 작성하지 않은 미완성 메서드.

메서드의 내용이 상속받는 클래스에 따라 달라질 수 있기 때문에 조상 클래스에서는 선언부만을 작성하고, 주석을 덧붙여 어떤 기능을 수행할 목적으로 작성됐는지 알려 주고, 실제 내용은 상속받는 클래스에서 구현하도록 비워 두는 것이다.

```java
/* 주석을 통해 어떤 기능을 수행할 목적으로 작성하였는지 설명한다. */
abstract 리턴타입 메서드이름();
```

추상메서드도 키워드 abstract를 앞에 붙여 주고, 구현부가 없으므로 괄호{ }대신 문장의 끝을 알리는 ; 을 적는다.

```java
abstract class Player {
    abstract void play(int pos); // 추상메서드
    abstract void stop(); // 추상메서드
}

class AudioPlayer extends Player {
    void play(int pos) { /* 내용 생략 */ } // 추상메서드 구현
    void stop() { /* 내용 생략 */ } // 추상메서드 구현
}

abstract calss AbstractPlayer extends Player {
    void play(int pos) { /* 내용 생략 */ } // 추상메서드 구현
}
```

추상 클래스로부터 상속 받는 자손 클래스는 오버라이딩을 통해 조상인 추상 클래스의 추상 메서드를 모두 구현해주어야 한다. 만일 조상으로부터 상속 받은 추상메서드 중 하나라도 구현하지 않는다면, 자손 클래스 역시 추상클래스로 지정해 주어야 한다.

메서드를 사용하는 쪽에서는 메서드가 실제로 어떻게 구현됐는지 몰라도 메서드의 선언부만 알고 있으면 되므로 내용이 없을 지라도 추상메서드를 사용하는 코드를 작성하는 것이 가능하며, 실제로는 자손 클래스에 구현된 완성된 메서드가 호출되도록 할 수 있다.

## 추상클래스의 작성

여러 클래스에 공통적으로 사용될 수 있는 클래스를 바로 작성하기도 하고, 기존의 클래스의 공통적인 부분을 뽑아서 추상클래스로 만들어 상속하도록 하는 경우도 있다.

**추상** : 낱낱의 구체적 표상이나 개념에서 공통된 성질을 뽑아 이를 일반적인 개념으로 파악하는 정신용

**추상화** : 클래스간의 공통점을 찾아내서 공통의 조상을 만드는 작업

**구체화** : 상속을 통해 클래스를 구현, 확장하는 작업

```java
abstract class Player {
    boolean pause;
    int currentPos;

    Player() {
        pause = false;
        currentPos = 0;
    }
  
    abstract void play(int pos) {
    abstract void stop();
 
    void play() {
        play(currentPos);
    }

    void pause() {
        if (pause) {
            pause = false;
            play(currentPos);
        } else {
            pause = true;
            stop();
        }
    }
}

class CDPlayer extends Player {
    void play(int currentPos) {
        /* 조상의 추상메서드를 구현. 내용 생략 */
    }
    void stop() {
        /* 조상의 추상메서드를 구현. 내용 생략 */
    }

    int currentTrack;
  
    void nextTrack() {
        currentTrack++;
            ...
    }

    void preTrack() {
        if (surrentTrack > 1) {
            currnetTrack--;
        }
            ...
    }
}
```

Player클래스의 play(int pos)와 stop()을 추상메서드로 하는 대신, 아무 내용도 없는 메서드로 작성할 수도 있다. 아무런 내용 없이 단지 괄호{ }만 있어도 일반 메서드로 간주되기 때문이다.

어차피 자손 클래스에서 오버라이딩하여 자신의 클래스에 맞게 구현할 테니 추상메서드로 선언하는 것과 내용없는 빈 몸통만 만들어 놓는 것은 별 차이가 없어 보이지만, 추상메서드로 선언하는 이유는 자손 클래스에서 추상메서드를 반드시 구현하도록 강요하기 위해서다.

---

# 인터페이스(interface)

## 인터페이스란?

**인터페이스** : 일종의 추상클래스. 밑그림만 그려져 있는 기본 설계도.

추상클래스처럼 추상메서드를 갖지만 추상클래스보다 추상화 정도가 높아서 추상클래스와 달리 몸통을 갖춘 일반 메서드 또는 멤버변수를 구성원으로 가질 수 없다.

오직 추상메서드와 상수만을 멤버로 가질 수 있다.

그 자체만으로 사용되기 보다는 다른 클래스를 작성하는데 도움 줄 목적으로 작성된다.

## 인터페이스의 작성

```java
// 인터페이스 작성법
interface 인터페이스이름 {
    public static final 타입 상수이름 = 값;
    public abstract 메서드이름(매개변수목록);
}
```

인터페이스를 작성하는 것은 키워드로 class대신 interface를 사용한다는 것만 다르고 나머지는  클래스를 작성하는 것과 같다.

클래스와 같이 접근 제어자는 public / defalut를 사용할 수 있다.

**인터페이스 멤버들의 제약사항**

- 모든 멤버변수는 public static final이어야 하며, 이를 생략할 수 있다.
- 모든 메서드는 public abstract이어야 하며, 이를 생략할 수 있다.
    
    단, static메서드와 디폴드 메서드는 예외(JDK1.8부터)
    

```java
interface PlayingCard {
    public static final int SPADE = 4;
    final int DIAMOND = 3; // public static final int DIAMOND = 3;
    static int HEART = 2; // public static final int HEART = 2;
    int CLOVER = 1; // public static final int CLOVER = 1;

    public abstract String getCardNumber();
    String getCardKind(); // public abstract String getCardKind();
}
```

인터페이스에 정의된 모든 멤버에 예외없이 적용되는 사항이기 때문에 제어자를 생략할 수 있고, 편의상 생략하는 경우가 많다. 생략된 제어자는 컴파일 시에 컴파일러가 자동적으로 추가해준다.

## 인터페이스의 상속

인터페이스는 인터페이스로부터만 상속 받을 수 있으며, 클래스와는 달리 다중상속이 가능하다.

```java
interface Movable {
    /* 지정된 위치(x, y)로 이동하는 기능의 메서드 */
    void move(int x, int y);
}

interface Attackable {
    /* 지정된 대상(u)를 공격하는 기능의 메서드 */
    void attack(Unit u);
}

interface Fightable extends Movable, Attackable { }
```

자손 인터페이스(Fightable)은 조상 인터페이스(Movable, Attackable)에 정의된 멤버를 모두 상속받으므로, Fightable자체에는 정의된 멤버가 하나도 없지만 조상 인터페이스로부터 상속 받은 두 개의 추상메서드 move(int x, int y)와 attack(Unit u)을 멤버로 갖게 된다.

## 인터페이스의 구현

인터페이스도 추상클래스처럼 그 자체로는 인스턴스를 생성할 수 없으며, 자신에 정의된 추상메서드의 몸통을 만들어주는 클래스를 작성해야 하는데, 방법은 추상클래스가 자신을 상속 받는 클래스를 정의하는 것과 다르지 않다. 다른 점은 인터페이스는 구현하다는 의미의 키워드 **implements**를 사용할 뿐이다.

```java
class 클래스이름 implements 인터페이스이름 {
    // 인터페이스에 정의된 추상메서드를 구현해야 한다.
}

class Fighter implements Fightable {
    public void move(int x, int y) { /* 내용 생략 */ }
    public void attack(Unit u) { /* 내용 생략 */ }
}
```

```java
abstract clss Fighter implements Fightable {
    public void move(int x, int y) { /* 내용 생략 */ }
}
```

만약 구현하는 인터페이스의 메서드 중 일부만 구현한다면, abstract를 붙여서 추상클래스로 선언해야 한다.

```java
class Fighter extends Unit implements Fightable {
    public void move(int x, int y) { /* 내용 생략 */ }
    public void attack(Unit u) { /* 내용 생략 */ }
}
```

상속과 구현을 동시에 할 수 있다.

```java
//ex24
class FighterTest {
    private static void main(String[] args) {
        Fighter f = new Fighter;
        
        if (f instanceof Unit) 
            System.out.println("f는 Unit클래스의 자손입니다.");
        
        if (f instanceof Fightable)
            System.out.println("f는 Fightable인터페이스를 구현했습니다.");
        
        if (f instanceof Movable)
            System.out.println("f는 Movable인터페이스를 구현했습니다.");
        
        if (f instanceof Attackable)
            System.out.println("f는 Attackable인터페이스를 구현했습니다.");
        
        if (f instanceof Object)
            System.out.println("f는 Object클래스의 자손입니다.");
    }
}

class Fighter extends Unit implements Fightable {
    public void move(int x, int y) { /* 내용 생략 */ }
    public void attack(Unit u) { /* 내용 생략 */ }
}

class Unit {
    int currentHp;
    int x;
    int y;
}

interface Fightable extends Movable, Attackable { }
interface Movable { void move(int x, int y); }
interface Attackable { void attack(Unit u); }

실행결과
f는 Unit클래스의 자손입니다.
f는 Fightable인터페이스를 구현했습니다.
f는 Movable인터페이스를 구현했습니다.
f는 Attackable인터페이스를 구현했습니다.
f는 Object클래스의 자손입니다.
```

Fighter클래스는 Unit클래스로부터 상속 받고 Fightable인터페이스만을 구현했지만, Unit클래스는 Object클래스의 자손이고, Fightable인터페이스는 Attackable과 Movable인터페이스의 자손이므로 Fighter클래스는 이 모든 클래스와 인터페이스의 자손이 되는 셈이다.

Movable인터페이스에 void move(int x, int y)와 같이 정의되어 있지만 사실 public abstract가 생략된 것이기 때문에 실제로는 public abstract void move(int x, int y)이다. 그래서 이를 구현하는 Fighter클래스에서는 void move(int x, int y)의 접근 제어자를 반드시 public으로 해야 하는 것이다.

## 인터페이스를 이용한 다중상속

인터페이스는 static상수만 정의할 수 있으므로 조상 클래스의 멤버변수와 충돌하는 경우는 거의 없고 충돌된다 하더라도 클래스 이름을 붙여서 구분이 가능하다.

추상메서드는 구현 내용이 전혀 없으므로 조상 클래스의 메서드와 선언부가 일치하는 경우에는 당연히 조상 클래스 쪽의 메서드를 상속 받으면 되므로 문제되지 않는다.

하지만, 이렇게 하면 멤버의 충돌은 피할 수 있지만, 다중상속의 장점을 잃어버리게 된다.

만약 두 개의 클래스로부터 상속을 받아야 할 상황이라면, 두 조상 클래스 중에서 비중이 높은 쪽을 선택하고 다른 한쪽은 클래스 내부에 멤버로 포함시키는 방식으로 처리하거나 어느 한쪽의 필요한 부분을 뽑아서 인터페이스로 만든 다음 구현 하도록 한다.

```java
public class Tv {
    protected boolean power;
    protected int channel;
    protected int volume;
    
    public void power() { power = !power; }
    public void channelUp() { channel++; }
    public void channelDown() { channel--; }
    public void volumeUp() { volume++; }
    public void volumeDown() { volume--; }
}

public class VCR {
    protected int counter;
    
    public void play() {
        // Tape 재생
    }
    
    public void stop() {
        // 재생 멈춤.
    }
    
    public void reset() {
        counter = 0;
    }
    
    public int getCounter() {
        return counter;
    }
    
    public void setCounter(int c) {
        counter = c;
    }
}
```

TVCR클래스를 작성하기 위해 두 클래스로부터 상속을 받을 수만 있으면 좋겠지만 다중상속을 허용하지 않으므로, 한 쪽만 선택하여 상속 받고 나머지 한 쪽은 클래스 내에 포함시켜서 내부적으로 인스턴스를 생성해서 사용하도록 한다.

```java
public interface IVCR {
    public void play();
    public void stop();
    public void reset();
    public int getCounter();
    public void setCounter(int c);
}
```

VCR클래스에 정의된 메서드와 일치하는 추상 메서드 작성.

```java
public class TVCR extends Tv implements IVCR {
    VCR vcr = new VCR();
    
    public void play() {
        vcr.play();
    }
    
    public void stop() {
        vcr.stop();
    }
    
    public void reset() {
        vcr.reset();
    }
    
    public int getCounter() {
        return vcr.getCounter();
    }
    
    public void setCounter(int c) {
        vcr.setCounter(c);
    }
}
```

IVCR인터페이스를 구현하기 위해서는 새로 메서드를 작성해야하는 부담이 있지만 이처럼 VCR클래스의 인스턴스를 사용하면 손쉽게 다중상속을 구현할 수 있다. 또한 VCR클래스의 내용이 변경되어도 변경된 내용이 TVCR클래스에도 자동적으로 반영되는 효과도 얻을 수 있다.

## 인터페이스를 이용한 다형성

인터페이스 역시 이를 구현한 클래스의 조상이라 할 수 있으므로 해당 인터페이스 타입의 참조변수로 이를 구현한 클래스의 인스턴스를 참조할 수 있으며, 인터페이스 타입으로 형변환도 가능하다.

```java
Fighter f = (Fightable)new Fighter();
또는
FIghtable f = new Fighter;
```

인터페이스 Fightable을 클래스 Fighter가 구현했을 때, 다음과 같이 Fighter인스턴스를 Fightable타입의 참조변수로 참조하는 것이 가능하다.

```java
void attack(Fightable f) {
    // ...
}
```

인터페이스는 메서드의 매개변수의 타입으로 사용될 수 있다.

인터페이스 타입의 매개변수가 갖는 의미는 메서드 호출 시 해당 인터페이스를 구현한 클래스의 인스턴스를 매개변수로 제공해야한다는 것이다.

```java
class Fighter extends Unit implements Fightable {
    public void move(int x, int y) { /* 내용 생략 */ }
    public void attack(Fightable f) { /* 내용 생략 */ }
} 
```

attack메서드를 호출할 때는 매개변수로 Fightable인터페이스를 구현한 클래스의 인스턴스를 넘겨줘야 한다.

attack메서드의 매개변수로 Fighter인스턴스를 넘겨줄 수 있다. 즉, **attack(new Fighter( ))**와 같이 할 수 있다.

```java
Fightable method() {
    ...
    Fighter f = new Fighter();
    return f;
}
```

메서드의 리턴타입으로 인터페이스의 타입을 지정하는 것도 가능하다.

**리턴타입이 인터페이스라는 것은 메서드가 해당 인터페이스를 구현한 클래스의 인스턴스를 반환한다는 것을 의미한다.**

```java
//ex25
interface Parseable {
    // 구문 분석작업 실행
    public abstract void parse(String fileName);
}

class ParserManager {
    // 리턴 타입이 Parseable인터페이스
    public static Parseable getParser(String type) {
        if (type.equals("XML")) 
            return new XMLParser();
        else
        {
            Parseable p = new HTMLParser();
            return p;
        }
    }
}

class XMLParser implements Parseable {
    public void parse(String fileName) {
        /* 구문 분석작업 수행 코드 작성 */
        System.out.println(fileName + "- XML parsing completed.");
    }
}

class HTMLParser implements Parseable {
    public void parse(String fileName) {
        /* 구문 분석작업 수행 코드 작성 */
        System.out.println(fileName + "- HTML parsing completed.");
    }
}

class ParserTest {
    public static void main(String[] args) {
        Parseable parser = ParserManager.getParser("XML");
        parser.parse("document.xml");
        parser = ParserManager.getParser("HTML");
        parser.parse("document2.html");
    }
}

실행결과
document.xml - XML parsing completed.
document2.html - HTML parsing completed.
```

ParserManager클래스의 getParser메서드는 매개변수로 넘겨받는 type의 값에 따라 XMLParser인스턴스 또는 HTMLParser인스턴스를 반환한다.

## 인터페이스의 장점

1. **개발시간을 단축시킬 수 있다.**
    
    일단 인터페이스가 작성되면, 이를 사용해서 프로그램을 작성하는 것이 가능하다. 메서드를 호출하는 쪽에서는 메서드의 내용에 관계없이 선언부만 알면 되기 때문이다.
    
    동시에 다른 한 쪽에서는 인터페이스를 구현하는 클래스를 작성하게 되면, 인터페이스를 구현하는 클래스가 작성될 때까지 기다리지 않고도 양쪽에서 동시에 개발을 진행할 수 있다.
    
2. **표준화가 가능하다.**
    
    프로젝트에 사용되는 기본 틀을 인터페이스로 작성한 다음, 개발자들에게 인터페이스를 구현하여 프로그램을 작성하도록 함으로써 보다 일관되고 정형화된 프로그램의 개발이 가능하다.
    
3. **서로 관계없는 클래스들에게 관계를 맺어 줄 수 있다.**
    
    서로 상속관계에 있지도 않고, 같은 조상클래스를 가지고 있지 않은 서로 아무런 관계도 없는 클래스들에게 하나의 인터페이스를 공통적으로 구현하도록 함으로써 관계를 맺어 줄 수 있다.
    
4. **독립적인 프로그래밍이 가능하다.**
    
    인터페이스를 이용하면 클래스의 선언과 구현을 분리시킬 수 있기 때문에 실제구현에 독립적인 프로그램을 작성하는 것이 가능하다. 클래스와 클래스간의 직접적인 관계를 인터페이스를 이용해서 간접적인 관계로 변경하면, 한 클래스의 변경이 관련된 다른 클래스에 영향을 미치지 않는 독립적인 프로그래밍이 가능하다.
    

```java
//ex26
class RepairableTest {
    public static void main(String[] args) {
        Tank tank = new Tank();
        Dropship dropship = new Dropship();

        Marine marine = new Marine();
        SCV scv = new SCV();
        scv.repair(tank);
        scv.repair(dropship);
        //scv.repair(marine);  에러발생
    }
}

interface Repairable {}

class Unit {
    int hitPoint;
    final int MAX_HP;
    Unit(int hp) {
        MAX_HP = hp;
    }
    //....
}

class GroundUnit extends Unit {
    GroundUnit(int hp) {
        super(hp);
    }
}

class AirUnit extends Unit {
    AirUnit(int hp) {
        super(hp);
    }
}

class Tank extends GroundUnit implements Repairable {
    Tank() {
        super(150);
        hitPoint = MAX_HP;
    }

    public String toString() {
        return "Tank";
    }
    //...
}

class Dropship extends AirUnit implements Repairable {
    Dropship() {
        super(125);
        hitPoint = MAX_HP;
    }

    public String toString() {
        return "Dropship";
    }
    //...
}

class Marine extends GroundUnit {
    Marine() {
        super(40);
        hitPoint = MAX_HP;
    }
    //...
}

class SCV extends GroundUnit implements Repairable {
    SCV() {
        super(60);
        hitPoint = MAX_HP;
    }

    void repair(Repairable r) {
        if (r instanceof Unit) {
            Unit u = (Unit)r;
            while (u.hitPoint != u.MAX_HP) {
                /* Unit의 HP를 증가시킨다. */
                u.hitPoint++;
            }
            System.out.println(u.toString() + "의 수리가 끝났습니다.");
        }
    }
    //...
}

실행결과
Tank의 수리가 끝났습니다.
Dropship의 수리가 끝났습니다.
```

게임에 나오는 모든 유닛들의 최고 조상은 Unit클래스고 유닛의 종류는 지상유닛(GroundUnit)과 공중유닛(AirUnit)으로 나누어진다. 

수리가 가능한 유닛의 개수만큼 다른 버전의 오버로딩된 메서드를 정의하는 것을 피하기 위해 매개변수의 타입을 이 들의 공통 조상으로 하면 좋겠지만 Dropship은 공통조상이 다르기 때문에 공통조상의 타입으로 메서드를 정의한다고 해도 최소한 2개의 메서드가 필요할 것이다.

인터페이스를 이용하면 기존의 상속체계를 유지하면서 공통점을 부여할 수 있다.

Repairable이라는 인터페이스를 정의하고 수리가 가능한 기계화 유닛에게 이 인터페이스를 구현하도록 하면 된다.

## 인터페이스의 이해

**인터페이스를 이해하기 위한 두 가지 사항**

- 클래스를 사용하는 쪽(User)과 클래스를 제공하는 쪽(Provider)이 있다.
- 메서드를 사용(호출)하는 쪽(User)에서는 사용하려는 메서드(Provider)의 선언부만 알면 된다. (내용은 몰라도 된다.)

```java
//ex27
class A {
    public void methodA(B b) {
        b.method();
    }
}

class B {
    public void methodB() {
        System.out.println("methodB()");
    }
}

class InterfaceTest {
    public static void main(String[] args) {
        A a = new A();
        a.methodA(new B());
    }
}

실행결과
methodB()
```

클래스 A(User)는 클래스 B(Provider)의 인스턴스를 생성하고 메서드를 호출한다. 이 두 클래스는 서로 직접적인 관계다.

이 경우 클래스 A를 작성하려면 클래스 B가 이미 작성되어 있어야 하고, 클래스 B의 methodB()의 선언부가 변경되면, 클래스 A도 변경되어야 한다.

이렇게 직접적인 관계의 두 클래스는 한 쪽(Provider)가 변경되면 다른 한 쪽(User)도 변경되어야 한다는 단점이 있다.

그러나 클래스 A가 클래스 B를 직접 호출하지 않고 인터페이스를 매개체로 해서 클래스 A가 인터페이스를 통해서 클래스 B의 메서드에 접근하도록 하면, 클래스 B에 변경 사항이 생기거나 클래스 B와 같은 기능의 다른 클래스로 대체 되어도 클래스 A는 전혀 영향을 받지 않도록 하는 것이 가능하다.

```java
interface I {
    public abstract void methodB();
}
```

클래스 B에 정의된 메서드를 추상메서드로 정의하는 인터페이스 I를 정의

```java
class B implements I {
    public void methodB() {
        System.out.println("methodB in B class");
    }
}
```

클래스 B가 인터페이스 I를 구현

```java
class A {
    public void methodA(I i) {
        i.methodB();
    }
}
```

클래스 A는 클래스 B 대신 인터페이스 I를 사용해서 작성 가능

이제 클래스 A와 클래스 B는 간접적인 관계로 바뀐 것이다.

클래스 A는 여전히 클래스 B의 메서드를 호출하지만 클래스 A는 인터페이스 I하고만 직접적인 관계에 있기 때문에 클래스 B의 변경에 영향을 받지 않는다.

클래스 A는 인터페이스를 통해 실제로 사용하는 클래스의 이름을 몰라도 되고 심지어는 실제로 구현된 클래스가 존재하지 않아도 문제되지 않는다. 클래스 A는 오직 직접적인 관계에 있는 인터페이스 I의 영향만 받는다.

```java
//ex28
class A {
    void autoPlay(I i) {
        i.play();
    }
}

interface I {
    public abstract void play();
}

class B implements I {
    public void play() {
        System.out.println("play in B class");
    }
}

class C implements I {
    public void play() {
        System.out.println("play in C class");
    }
}

class InterfaceTest2 {
    public static void main(String[] args) {
        A a = new A();
        a.autoPlay(new B());
        a.autoPlay(new C());
    }
}

실행결과
play in B class
play in C class
```

클래스 A가 인터페이스 I를 사용해서 작성되긴 했지만, 이처럼 매개변수를 통해서 인터페이스 I를 구현한 클래스의 인스턴스를 동적으로 제공 받아야 한다.

```java
//ex29
class InterfaceTest3 {
    public static void main(String[] args) {
        A a = new A();
        a.methodA();
    }
}

class A {
    void methodA() {
        I i = InstanceManager.getInstance();
        i.methodB();
        System.out.println(i.toString());
    }
}

interface I {
    public abstract void methodB();
}

class B implements I {
    public void methodB() {
        System.out.println("methodB in B class");
    }
    
    public String toString() { return "class B"; }
}

class InstanceManager {
    public static I getInstance() {
        return new B(); // 다른 인스턴스로 바꾸려면 여기만 변경하면 됨.
    }
}

실행결과
methodB in B class
class B
```

인스턴스를 직접 생성하지 않고, getInstance( )라는 메서드를 통해 제공받는다. 이렇게 하면, 나중에 다른 클래스의 인스턴스로 변경되어도 A클래스의 변경없이 getInstance( )만 변경하면 된다는 장점이 생긴다.

## 디폴트 메서드와 static메서드

**static메서드**

- static메서드는 인스턴스와 관계가 없는 독립적인 메서드이기 때문에 예전부터 추가하지 못할 이유가 없었지만, 자바를 보다 쉽게 배울 수 있도록 규칙을 단순히 할 필요가 있어서 인터페이스의 모든 메서드는 추상 메서드이어야 한다는 규칙에 예외를 두지 않았다.
- 그래서 인터페이스와 관련된 static메서드는 별도의 클래스에 따로 두어야 했다.
- 인터페이스의 static메서드 역시 접근 제어자가 항상 public이며, 생략할 수 있다.

**디폴트 메서드(default method)** : 추상 메서드의 기본적인 구현을 제공하는 메서드

- 추상 메서드가 아니기 때문에 디폴트 메서드가 새로 추가되어도 해당 인터페이스를 구현한 클래스를 변경하지 않아도 된다.
- 디폴트 메서드는 앞에 키워드 default를 붙이며, 추상 메서드와 달리 일반 메서드처럼 몸통{ }이 있어야 한다.
- 디폴트 메서드 역시 접근 제어자가 public이며, 생략 가능하다.
- 추상 메서드를 추가하는 대신, 디폴트 메서드를 추가하면, 기존의 MyInterface를 구현 클래스를 변경하지 않아도 된다.

```java
interface MyInterface {
    void method();
    default void newMethod() {}
}
```

**새로 추가된 디폴트 메서드가 기존의 메서드와 이름이 중복되어 충돌하는 경우 해결하는 규칙**

1. **여러 인터페이스의 디폴트 메서드 간의 충돌**
    
    인터페이스를 구현한 클래스에서 디폴트 메서드를 오버라이딩해야 한다.
    
2. **디폴트 메서드와 조상 클래스 메서드 간의 충돌**
    
    조상 클래스의 메서드가 상속되고, 디폴트 메서드는 무시된다.
    

```java
//ex30
class DefaultMethodTest {
    public static void main(String[] args) {
        Child c = new Child();
        c.method1();
        c.method2();
        MyInterface.staticMethod();
        MyInterface2.staticMethod();
    }
}

class Child extends Parent implements MyInterface, MyInterface2 {
    public void method1() {
        System.out.println("method() in Child");
    }
}

class Parent {
    public void method2() {
        System.out.println("method2() in Parent");
    }
}

interface MyInterface {
    default void method1() {
        System.out.println("method1() in MyInterface");
    }

    default void method2() {
        System.out.println("method2() in MyInterfcae");
    }

    static void staticMethod() {
        System.out.println("staticMethod() in MyInterface");
    }
}

interface MyInterface2 {
    default void method1() {
        System.out.println("method1() in MyInterface2");
    }

    static void staticMethod() {
        System.out.println("staticMethod() in MyInterface2");
    }
}

실행결과
method1() in Child
method2() in Parent
staticMethod() in MyInterface
staticMethod() in MyInterface2
```

---

# 내부 클래스(inner class)

## 내부 클래스란?

**내부 클래스** : 클래스 내에 선언된 클래스

두 클래스가 서로 긴밀한 관계에 있기 때문에 클래스에 다른 클래스를 선언한다.

**내부 클래스 장점**

1. 내부 클래스에서 외부 클래스의 멤버들을 쉽게 접근할 수 있다.
2. 코드의 복잡성을 줄일 수 있다(캡슐화).

```java
class A { // 외부 클래스
    ...
    class B { // 내부 클래스
        ...
    }
    ...
}
```

B는 A의 내부 클래스(inner class)가 되고 A는 B를 감싸고 있는 외부 클래스(outer class)가 된다.

내부 클래스인 B는 외부 클래스 A를 제외하고는 다른 클래스에서 잘 사용되지 않는 것이어야 한다.

## 내부 클래스의 종류와 특징

내부 클래스의 종류는 변수의 선언위치에 따른 종류와 같다.

- **인스턴스 클래스(instance class)** : 외부 클래스의 멤버변수 선언위치에 선언하며, 외부 클래스의 인스턴스멤버처럼 다루어진다. 주로 외부 클래스의 인스턴스멤버들과 관련된 작업에 사용될 목적으로 선언된다.

- **스태틱 클래스(static class)** : 외부 클래스의 멤버변수 선언위치에 선언하며, 외부 클래스의 static멤버처럼 다루어진다. 주로 외부 클래스의 static멤버, 특히 static메서드에서 사용될 목적으로 선언된다.

- **지역 클래스(local class)** : 외부 클래스의 메서드나 초기화블럭 안에 선언하며, 선언된 영역 내부에서만 사용될 수 있다.

- **익명 클래스(anonymous class)** : 클래스의 선언과 객체의 생성을 동시에 하는 이름없는 클래스(일회용)

## 내부 클래스의 선언

```java
class Outer {
    class InstanceInner {}
    static class StaticInner {}

    void myMethod() {
        class LocalInner {}
    }
}
```

외부 클래스(Outer)에 3개의 서로 다른 종류의 내부 클래스를 선언했다. 내부 클래스의 선언위치가 변수의 선언위치와 동일하다.

각 내부 클래스의 선언위치에 따라 같은 선언위치의 변수와 동일한 유효범위(scope)와 접근성(accessibility)을 갖는다.

## 내부 클래스의 제어자와 접근성

```java
class Outer {
    private class InstanceInner {}
    protected static class StaticInner {}

    void myMethod() {
        class LocalInner {}
    }
}
```

인스턴스클래스(InstanceInner)와 스태틱 클래스(StaticInner)는 외부 클래스(Outer)의 멤버변수와 같은 위치에 선언되며, 또한 멤버변수와 같은 성질을 갖는다. 따라서 내부 클래스가 외부 클래스의 멤버와 같이 간주되고, 인스턴스멤버와 static멤버 간의 규칙이 내부 클래스에도 똑같이 적용된다.

내부 클래스도 클래스이기 때문에 abstract나 final과 같은 제어자를 사용할 수 있을 뿐만 아니라, 멤버변수들처럼 private, protected과 접근제어자도 사용이 가능하다.

```java
//ex31
class InnerEx1 {
    class InstanceInner {
        int iv = 100;
        //static int cv = 100;    에러. static변수 선언 불가
        final static int CONST = 100;  // final static은 상수이므로 허용
    }

    static class StaticInner {
        int iv = 200;
        static int cv = 200; // static클래스만 static멤버 정의 가능
    }

    void myMethod() {
        class LocalInner {
            int iv = 300;
            //static int cv = 300;  에러. static변수 선언 불가
            final static int CONST = 300;  // final static은 상수이므로 허용
        }
    }

    public static void main(String[] args) {
        System.out.println(InstanceInner.CONST);
        System.out.println(StaticInner.cv);
    }
}

실행결과
100
200
```

내부 클래스 중에서 스태틱 클래스(StaticInner)만 static멤버를 가질 수 있다. 내부 클래스에 static변수를 선언해야 한다면 스태틱 클래스로 선언해야한다.

다만 final과 static이 동시에 붙은 변수는 상수(constant)이므로 모든 내부 클래스에서 정의가 가능하다.

```java
//ex32
class InnerEx2 {
    class InstanceInner {}
    static class StaticInner {}

    // 인스턴스멤버 간에는 서로 직접 접근이 가능하다.
    InstanceInner iv = new InstanceInner();
    // static멤버 간에는 서로 직접 접근이 가능하다.
    static StaticInner cv = new StaticInner();

    static void staticMethod() {
        // static멤버는 인스턴스멤버에 직접 접근할 수 없다.
        //InstanceInner obj1 = new InstanceInner();
        StaticInner obj2 = new StaticInner();

        // 굳이 접근하려면 아래와 같이 객체를 생성해야 한다.
        // 인스턴스클래스는 외부 클래스를 먼저 생성해야만 생성할 수 있다.
        InnerEx2 outer = new InnerEx2();
        InstanceInner obj1 = outer.new InstanceInner();
    }

    void instanceMethod() {
        // 인스턴스메서드에서는 인스턴스멤버와 static멤버 모두 접근 가능하다.
        InstanceInner obj1 = new InstanceInner();
        StaticInner obj2 = new StaticInner();
        // 메서드 내에 지역적으로 선언된 내부 클래스는 외부에서 접근할 수 없다.
        //LocalInner lv = new LocalInner();
    }

    void myMethod() {
        class LocalInner {}
        LocalInner lv = new LocalInner();
    }
}
```

인스턴스클래스는 외부 클래스의 인스턴스멤버를 객체생성 없이 바로 사용할 수 있지만, 스태틱 클래스는 외부 클래스의 인스턴스멤버를 개체생성 없이 사용할 수 없다.

마찬가지로 인스턴스클래스는 스태틱 클래스의 멤버들을 객체생성 없이 사용할 수 있지만, 스태틱 클래스에서는 인스턴스클래스의 멤버들을 객체생성 없이 사용할 수 없다.

```java
//ex33
class InnerEx3 {
    private int outerIv = 0;
    static int outerCv = 0;
    
    class InstanceInner {
        int iiv = outerIv;
        int iiv2 = outerCv;
    }
    
    static class StaticInner {
        // 스태틱 클래스는 외부 클래스의 인스턴스멤버에 접근할 수 없다.
        // int siv = outerIv;
        static int scv = outerCv;
    }
    
    void myMethod() {
        int lv = 0;
        final int LV = 0; // JDK1.8부터 final 생략 가능
        
        class LocalInner {
            int liv = outerIv;
            int liv2 = outerCv;
            // 외부 클래스의 지역변수는 final이 붙은 변수(상수)만 접근가능하다.
            // int liv3 = lv; 에러. JDK1.8부터 에러 아님
            int liv4 = LV;
        }
    }
}
```

인스턴스클래스(InstanceInner)는 외부 클래스(InnerEx3)의 인스턴스멤버이기 때문에 인스턴스변수 outerIv와 static변수 outerCv를 모두 사용할 수 있다. outerIv의 접근 제어자가 private일지라도 사용가능하다.

스태틱 클래스(StaticInner)는 외부 클래스(InnerEx3)의 static멤버이기 때문에 외부 클래스의 인스턴스멤버인 outerIv와 InstanceInner을 사용할 수 없다. 단지 static멤버인 outerCv만 사용할 수 있다.

지역 클래스(LocalInner)는 외부 클래스의 인스턴스멤버와 static멤버를 모두 사용할 수 있으며, 지역 클래스가 포함된 메서드에 정의된 지역변수도 사용할 수 있다. 단, final이 붙은 지역변수만 접근 가능한데 그 이유는 메서드가 수행을 마쳐서 지역변수가 소멸된 시점에도, 지역 클래스의 인스턴스가 소멸된 지역변수를 참조하려는 경우가 발생할 수 있기 때문인다.

```java
//ex 34
class Outer {
    class InstanceInner {
        int iv = 100;
    }
    
    static class StaticInner {
        int iv = 200;
        static int cv = 300;
    }
    
    void myMethod() {
        class LocalInner {
            int iv = 400;
        }
    }
}

class InnerEx4 {
    public static void main(String[] args) {
        /* 인스턴스클래스의 인스턴스를 생성하려면
        외부 클래스의 인스턴스를 먼저 생성해야 한다. */
        Outer oc = new Outer();
        Outer.InstanceInner ii = oc.new InstanceInner();
        
        System.out.println("ii.iv : " + ii.iv);
        System.out.println("Outer.StaticInner.cv : " + Outer.StaticInner.cv);
        
        // 스태틱 내부 클래스의 인스턴스는 외부 클래스를 먼저 생성하지 않아도 된다.
        Outer.StaticInner si = new Outer.StaticInner();
        System.out.println("si.iv : " + si.iv);
    }
}

실행결과
ii.iv : 100
Outer.StaticInner.cv : 300
si.iv : 200
```

```java
//ex35
class Outer {
    int value = 10; // Outer.this.value
    
    class Inner {
        int value = 20; // this.value
        
        void method1() {
            int value = 30;
            System.out.println("           value : " + value);
            System.out.println("      this.value : " + this.value);
            System.out.println("Outer.this.value : " + Outer.this.value);
        }
    }
}

class InnerEx5 {
    public static void main(String[] args) {
        Outer outer = new Outer();
        Outer.Inner inner = outer.new Inner();
        inner.method1();
    }
}

실행결과
           value : 30
      this.value : 20
Outer.this.value : 10
```

내부 클래스와 외부 클래스에 선언된 변수의 이름이 같을 때 변수 앞에 **this** 또는 **외부 클래스명.this**를 붙여서 서로 구별할 수 있다.

## 익명 클래스(anonymous class)

클래스의 선언과 객체의 생성을 동시에 하기 때문에 단 한번만 사용될 수 있고 오직 하나의 객체만을 생성할 수 있는 일회용 클래스이다.

```java
new 조상클래스이름() {
    // 멤버 선언
}

    또는

new 구현인터페이스이름() {
    // 멤버 선언
}
```

이름이 없기 때문에 생성자도 가질 수 없으며, 조상클래스의 이름이나 구현하고자 하는 인터페이스의 이름을 사용해서 정의하기 때문에 하나의 클래스로 상속받는 동시에 인터페이스를 구현하거나 둘 이상의 인터페이스를 구현할 수 없다. 오로지 단 하나의 클래스를 상속받거나 단 하나의 인터페이스만을 구현할 수 있다.

```java
//ex36
class InnerEx6 {
    Object iv = new Object() { void method() {} }; // 익명 클래스
    static Object cv = new Object() { void method() {} }; // 익명 클래스

    void myMethod() {
        Object lv = new Object() { void method() {} }; // 익명 클래스
    }
}
```

익명 클래스는 이름이 없기 때문에 **외부 클래스명$숫자.class**의 형식으로 클래스파일명이 결정된다.

```java
//ex37
import java.awt.*;
import java.awt.event.*;

class InnerEx7 {
    public static void main(String[] args) {
        Button b = new Button("Start");
        b.addActionListener(new EventHandler());
    }
}

class EventHandler implements ActionListener {
    public void actionPerformed(ActionEvent e) {
        System.out.println("ActionEvent occurred!!!");
    }
}
```

```java
//ex38
import java.awt.*;
import java.awt.event.*;

class InnerEx8 {
    public static void main(String[] args) {
        Button b = new Button("Start");
        b.addActionListener(new ActionListener() {
                public void actionPerformed(ActionEvent e) {
                    System.out.println("ActionEvent occurred!!!");
                }
            }
        );
    }
}
```

먼저 두 개의 독립된 클래스를 작성한 다음에, 다시 익명클래스를 이용하여 변경하면 보다 쉽게 코드를 작성할 수 있다.
