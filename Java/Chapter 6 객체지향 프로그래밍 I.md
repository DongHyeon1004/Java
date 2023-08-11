# 객체지향 프로그래밍 I

# 객체지향언어

## 객체지향언어의 역사

- 모의실험을 위해 실제 세계와 유사한 가상 세계를 컴퓨터 속에 구현하고자 한 과학자들의 노력이 객체지향이론을 탄생시킴.
- **객체지향이론의 기본 개념** : 실제 세계는 사물(객체)로 이루어져 있으며, 발생하는 모든 사건들은 사물간의 상호작용이다
- 실제 사물의 속성과 기능을 분석한 다음, 데이터(변수)와 함수로 정의함으로써 실제 세계를 컴퓨터 속에 옮겨 놓은 것과 같은 가상 세계를 구현하고 모의실험을 함으로써 많은 시간과 비용을 절약할 수 있었음.
- 객체지향이론은 상속, 캡슐화, 추상화 개념을 중심으로 점차 구체적으로 발전되었고, 1960년대 중반에 객체 지향 이론을 프로그래밍 언어에 적용한 시뮬라라는 최초의 객체지향언어가 탄생함.
- 객체지향언어는 널리 사용되지 못하고 있었음. 1980년대 중반에 여러 객체지향언어가 발표되면서 본격적으로 개발자들의 관심을 끌기 시작하였지만, 여전히 사용자층이 넓지 못함.
- 프로그램의 규모가 커지고 사용자들의 요구가 빠르게 변화해가는 상황을 절차적 언어로는 극복하기 어려워 객체지향언어를 이용한 개발방법론이 대안으로 떠오르게 되면서 조금씩 입지를 넓힘.
- 자바가 1995년에 발표되고 1990년대 말에 인터넷의 발전과 함께 크게 유행하면서 객체지향언어가 프로그래밍 언어의 주류가 됨.

## 객체지향언어

- **객체지향언어** : 기존의 프로그래밍 언어에 몇 가지 새로운 규칙을 추가한 보다 발전된 형태의 것
- 규칙들을 이용해 코드 간에 서로 관계를 맺어 줌으로써 보다 유기적으로 프로그램을 구성하는 것이 가능해짐.

**객체지향언어의 주요특징**

1. **코드의 재사용성이 높다**
    
    새로운 코드를 작성할 때 기존의 코드를 이용하여 쉽게 작성할 수 있다.
    
2. **코드의 관리가 용이하다.**
    
    코드간의 관계를 이용해서 적은 노력으로 쉽게 코드를 변경할 수 있다. 
    

1. **신뢰성이 높은 프로그래밍을 가능하게 한다.**
    
    제어자와 메서드를 이용해서 데이터를 보호하고 올바른 값을 유지하도록 하며, 코드의 중복을제거하여 코드의 불일치로 인한 오동작을 방지할 수 있다. 
    

---

# 클래스와 객체

## 클래스와 객체의 정의와 용도

**클래스** : 객체를 정의해 놓은 것. 객체의 설계도 또는 틀

**클래스의 용도** : 객체를 생성하는데 사용

**객체** : 실제로 존재하는 것. 사물 또는 개념. 클래스에 정의된 내용대로 메모리에 생성된 것.

**객체의 용도** : 객체가 가지고 있는 기능과 속성에 따라 다름.

**유형의 객체** : 책상, 의자, 자동차, TV와 같은 사물

**무형의 객체** : 수학공식, 프로그램 에러와 같은 논리나 개념

- 클래스는 단지 객체를 생성하는데 사용될 뿐, 객체 그 자체가 아니다.
- 원하는 기능의 객체를 사용하기 위해서는 먼저 클래스로부터 객체를 생성하는 과정이 선행되어야 한다.
- 클래스를 한 번만 잘 만들어 놓으면, 매번 객체를 생성할 때마다 어떻게 객체를 만들어야 할 지 고민하지 않고, 클래스로부터 객체를 생성해서 사용하기만 하면 된다.
- JDK에서는 프로그래밍을 위해 많은 수의 유용한 클래스를 기본적으로 제공한다.

## 객체와 인스턴스

**인스턴스** : 어떤 클래스로부터 만들어진 객체

**인스턴스화** : 클래스로부터 객체를 만드는 과정

- 인스턴스는 객체와 같은 의미지만, 객체는 모든 인스턴스를 대표하는 포괄적인 의미, 인스턴스는 어떤 클래스로부터 만들어진 것인지를 강조하는 보다 구체적인 의미를 갖는다.

## 객체의 구성요소 - 속성과 기능

**객체 = 속성 + 기능**

- 객체는 다수의 속성과 다수의 기능을 가짐.
- **멤버** : 객체가 가지고 있는 속성과 기능
- 클래스로부터 객체를 생성하면, 클레스에 정의된 속성과 기능을 가진 객체가 만들어지는 것.
- **속성(property)** : **멤버변수(member variable)**, 특성(attribute), 필드(field), 상태(state)
- **기능(function)** : **메서드(method)**, 함수(function), 행위(behavior)

```java
class Tv {
	//변수(속성)
	String color;
	boolean power;
	int channel;

	//메서드(기능)
	void power() { power = !power; }
	void channelUp() { channel++; }
	void channelDown() { channel--; }
}
```

## 인스턴스의 생성과 사용

```java
**인스턴스 생성 방법**

클래스명 변수명;
변수명 = new 클래스명();

Tv t;
t = new Tv();
```

```java
//ex1
class Tv {
    String color;
    boolean power;
    int channel;

    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}

class TvTest {
    public static void main(String[] args) {
        Tv t;
        t = new Tv();
        t.channel = 7;
        t.channelDown();
        System.out.println("현재 채널은 " + t.channel + " 입니다."); // 현재 채널은 6 입니다.
    }
}
```

1. **Tv t;**
    
    Tv클래스 타입의 참조변수 t선언. 
    
    메모리에 참조변수 t를 위한 공간 마련. 
    
    인스턴스가 생성되지 않았으므로 아무것도 할 수 없음.
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/6-1.png)
    
2. **t = new Tv();**
    
    연산자 new에 의해 Tv클래스의 인스턴스가 메모리 빈 공간에 생성. 
    
    주소가 0x100인 곳에 생성되었다 가정.
    
    멤버변수는 각 자료형에 해당하는 기본값으로 초기화.
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/6-2.png)
    
    대입연산자 = 에 의해서 생성된 객체의 주소 값이 참조변수 t에 저장.
    
    참조변수 t를 통해 Tv인스턴스 접근 가능.
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/6-3.png)
    
3. **t.channel = 7 ;**
    
    참조변수 t에 저장된 주소에 있는 인스턴스의 멤버변수 channel에 7 저장.
    
    인스턴스의 멤버 변수(속성)를 사용하려면 **참조변수.멤버변수**
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/6-4.png)
    
4. **t.channelDown();**
    
    참조변수 t가 참조하고 있는 Tv인스턴스의 channelDown메서드 호출.
    
    channel 값 7 → 6
    
    ![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/6-5.png)
    
5. **System.out.println(”현재 채널은 “ + t.channel + “ 입니다.”);**
    
    참조변수 t가 참조하고 있는 Tv인스턴스의 멤버변수 channel에 저장된 값 출력.
    

**인스턴스는 참조변수를 통해서만 다룰 수 있으며, 참조변수의 타입은 인스턴스의 타입과 일치해야 한다.**

```java
//ex2
class Tv {
    String color;
    boolean power;
    int channel;

    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}

class TvTest2 {
    public static void main(String[] args) {
       Tv t1 = new Tv();
       Tv t2 = new Tv();
       System.out.println("t1의 channel값은 " + t1.channel + "입니다.");
       System.out.println("t2의 channel값은 " + t2.channel + "입니다.");

       t1.channel = 7;
       System.out.println("t1의 channel값을 7로 변경하였습니다.");

       System.out.println("t1의 channel값은 " + t1.channel + "입니다.");
       System.out.println("t2의 channel값은 " + t2.channel + "입니다.");
    }
}

실행결과
t1의 channel값은 0입니다.
t2의 channel값은 0입니다.
t1의 channel값을 7로 변경하였습니다.
t1의 channel값은 7입니다.
t1의 channel값은 0입니다.
```

같은 클래스로부터 생성됐을지라도 각 인스턴스의 속성(멤버변수)은 서로 다른 값을 유지 할 수 있으며, 메서드의 내용은 모든 인스턴스에 대해 동일하다.

```java
//ex3
class Tv {
    String color;
    boolean power;
    int channel;

    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}

class TvTest3 {
    public static void main(String[] args) {
        Tv t1 = new Tv();
        Tv t2 = new Tv();
        System.out.println("t1의 channel값은 " + t1.channel + "입니다.");
        System.out.println("t2의 channel값은 " + t2.channel + "입니다.");

        t2 = t1;
        t1.channel = 7;
        System.out.println("t1의 channel값을 7로 변경하였습니다.");

        System.out.println("t1의 channel값은 " + t1.channel + "입니다.");
        System.out.println("t2의 channel값은 " + t2.channel + "입니다.");
    }
}

실행결과
t1의 channel값은 0입니다.
t2의 channel값은 0입니다.
t1의 channel값을 7로 변경하였습니다.
t1의 channel값은 7입니다.
t1의 channel값은 7입니다.
```

참조변수에는 하나의 값(주소)만이 저장될 수 있으므로 둘 이상의 참조변수가 하나의 인스턴스를 가리키는 것은 가능하지만 **하나의 참조변수가 여러 개의 인스턴스를 가리키는 것은 불가능.**

## 객체 배열

**객체 배열** : 객체를 배열처럼 다루는 것

- 객체 배열 안에 객체가 저장되는 것이 아니라 객체의 주소 저장.
- 참조변수들을 하나로 묶은 참조 변수 배열인 것.

```java
Tv tvArr = new Tv[3];

tvArr[0] = new Tv();
tvArr[1] = new Tv();
tvArr[2] = new Tv();
```

**Tv tvArr = new Tv[3];**

객체를 다루기 위한 참조 변수들이 만들어진 것이고, 아직 객체가 저장되지 않았다.

```java
Tv tvArr[] = { new Tv(), new Tv(), new Tv() } 
```

초기화 블럭을 사용해서 한 줄로 표현 가능

다뤄야 할 객체의 수가 많으면 for문을 사용

```java
//ex4
class Tvtest4 {
    public static void main(String[] args) {
        Tv tvArr[] = new Tv[3];

        for (int i = 0; i < tvArr.length; i++)
        {
            tvArr[i] = new Tv();
            tvArr[i].channel = i + 10;
        }

        for (int i = 0; i < tvArr.length; i++)
        {
            tvArr[i].channelUp();
            System.out.printf("tvArr[%d].channel = %d%n", i, tvArr[i].channel);
        }
    }
}

class Tv {
    String color;
    boolean power;
    int channel;

    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}

실행결과
tvArr[0].channel = 11
tvArr[1].channel = 12
tvArr[2].channel = 13
```

## 클래스의 또 다른 정의

1. **클래스 - 데이터와 함수의 결합**
    
    데이터 저장 형태의 발전 과정
    
    1. **변수** : 하나의 데이터를 저장할 수 있는 공간
    2. **배열** : 같은 종류의 여러 데이터를 하나의 집합으로 저장할 수 있는 공간
    3. **구조체** : 서로 관련된 여러 데이터를 종류에 관계없이 하나의 집합으로 저장할 수 있는 공간
    4. **클래스** : 데이터와 함수의 결합(구조체 + 함수)
    
- 함수는 주로 데이터를 가지고 작업을 하기 때문에 많은 경우에 있어서 데이터와 함수는 관계가 깊음.
- 객체지향언어에서는 변수(데이터)와 함수를 하나의 클래스에 정의하여 서로 관계가 깊은 변수와 함수들을 함께 다룰 수 있게 함.
- **서로 관련된 변수들을 정의하고 이들에 대한 작업을 수행하는 함수들을 함께 정의한 것.**
- 깊은 관계에 있는 변수와 함수를 하나의 클래스에 정의하면 변수와 함수가 서로 유기적으로 연결되어 작업이 간단하고 명료해진다.

1. **클래스 - 사용자정의 타입(user-defined type)**
    
    **사용자정의 타입** : 프로그래밍 언어에서 제공하는 자료형 외에 프로그래머가 서로 관련된 변수들을 묶어서 하나의 타입으로 새로 추가하는 것.
    
    - 객체지향언어에서는 클래스가 사용자 정의 타입.
    - 기본형의 개수는 8개로 정해져 있지만, 참조형의 경우 프로그래머가 새로운 타입을 추가할 수 있기 때문에 개수가 정해져 있지 않다.
    - 객체지향언어에서는 제어자와 메서드를 이용해서 추가적인 조건들을 코드에 쉽게 반영할 수 있음.

---

# 변수와 메서드

## 선언위치에 따른 변수의 종류

**변수의 종류**

- 클래스변수
- 인스턴스변수
- 지역변수

변수의 종류는 변수의 선언된 위치가 결정짓는다.

1. **인스턴스변수(instance variable)**
    - 멤버변수 중 static이 붙지 않은 것
    - 클래스 영역에서 선언, 클래스의 인스턴스를 생성할 때 만들어짐.
    - 독립적인 공간을 가지므로 서로 다른 값을 가질 수 있음.
    - 인스턴스마다 고유한 상태를 유지해야 하는 속성의 경우 인스턴스변수로 선언.

1. **클래스변수(class variable)**
    - 인스턴스변수 앞에 static을 붙여 선언.
    - 모든 인스턴스가 공통된 저장 공간(변수)을 공유함.
    - 한 클래스의 모든 인스턴스들이 공통적인 값을 유지해야 하는 경우 클래스변수로 선언.
    - 인스턴스를 생성하지 않고도 언제라도 바로 사용 가능. **(클래스이름.클래스변수)**
    - 클래스가 메모리에 로딩될 때 생성되어 프로그램이 종료될 때까지 유지
    - public을 앞에 붙이면 전역변수의 성격을 가짐.
    
2. **지역변수(local variable)**
    - 매서드 내에 선언되어 메서드 내에서만 사용 가능.
    - 메서드가 종료되면 소멸되어 사용 불가능.
    - 반복문의 블럭 내에 선언된 지역변수는 선언된 블럭{} 내에서만 사용 가능하며, 블럭{}을 벗어나면 소멸되어 사용 불가능.

## 클래스변수와 인스턴스변수

```java
//ex5
class CardTest {
    public static void main(String[] args) {
        System.out.println("Card.width = " + Card.width);
        System.out.println("Card.height = " + Card.height);

        Card c1 = new Card();
        c1.kind = "Heart";
        c1.number = 7;

        Card c2 = new Card();
        c2.kind = "Spade";
        c2.number = 4;

        System.out.println("c1은 " + c1.kind + ", " + c1.number + "이며, 크기는 (" + c1.width + ", " + c1.height + ")" );
        System.out.println("c2은 " + c2.kind + ", " + c2.number + "이며, 크기는 (" + c2.width + ", " + c2.height + ")" );
        System.out.println("c1의 width와 height를 각각 50, 80으로 변경합니다.");
        c1.width = 50;
        c1.height = 80;

        System.out.println("c1은 " + c1.kind + ", " + c1.number + "이며, 크기는 (" + c1.width + ", " + c1.height + ")" );
        System.out.println("c2은 " + c2.kind + ", " + c2.number + "이며, 크기는 (" + c2.width + ", " + c2.height + ")" );
    }
}

class Card {
    String kind;
    int number;
    static int width = 100;
    static int height = 250;
}
```

- Card클래스의 클래스변수인 width, height는 인스턴스를 생성하지 않고도 **클래스이름.클래스변수**와 같은 방식으로 사용 가능.
- Card인스턴스인 c1, c2는 클래스변수인 width, height를 공유하기 때문에, c1의 width, height값을 변경하면 c2도 변경된다.
- Card.width, c1.width, c2.width는 같은 저장공간을 참조해 항상 같은 값을 갖는다.

**인스턴스변수는 인스턴스가 생성될 때 마다 생성되므로 인스턴스마다 각기 다른 값을 유지할 수 있지만, 클래스 변수는 모든 인스턴스가 하나의 저장공간을 공유하므로, 항상 공통된 값을 갖는다.**

## 메서드

**메서드** : 특정 작업을 수행하는 일련의 문장들을 하나로 묶은 것

- 기본적으로 수학의 함수와 유사하며, 어떤 값을 입력하면 이 값으로 작업을 수행해 결과를 반환.
- 입력값 또는 출력값이 없을 수도 있으며, 둘 다 없을 수도 있음.
- 메서드에 넣을 값과 반환하는 결과만 알면 될 뿐, 메서드가 내부적으로 어떤 과정을 거쳐 결과를 만들어내는지 몰라도 됨. 그래서 메서드 내부를 보이지 않는 **블랙박스**라고도 함.

### 메서드를 사용하는 이유

1. **높은 재사용성(resuability)**
    - 한번 만들어 놓은 메서드는 몇 번이고 호출 가능하며, 다른 프로그램에서도 사용 가능.
    
2. **중복된 코드의 제거**
    - 반복되는 문장들을 묶어서 하나의 메서드로 작성 시, 반복되는 문장들 대신 메서드를 호출하는 한 문장으로 대체할 수 있음.
    - 전체 소스 코드의 길이가 짧아지고, 변경 사항이 발생했을 때 수정해야할 코드의 양이 줄어들어 오류 발생 가능성도 줄어듦.
    
3. **프로그램의 구조화**
    - 큰 규모의 프로그램에서는 문장들을 작업 단위로 나눠서 여러 개의 메서드에 담아 프로그램의 구조를 단순화시키는 것이 필수적임.
    - 프로그램의 전체 흐름이 한눈에 들어올 정도로 단순하게 구조화하는 것이 문제 발생 시 해당 부분을 쉽게 찾을 수 있음.
    

## 메서드의 선언과 구현

### 메서드 선언부(method declaration, method header)

**메서드 선언부** : 메서드가 작업을 수행하기 위해 어떤 값들을 필요로 하고 작업의 결과로 어떤 타입의 값을 반환하는지에 대한 정보 제공

**메서드 선언부 구성**

- 메서드의 이름
- 매개변수 선언
- 반환타입

**메서드의 이름**

- 변수의 명명규칙대로 작성하면 됨.
- 메서드의 이름은 동사인 경우가 많고, 이름만으로도 메서드의 기능을 쉽게 알 수 있도록 함축적이면서도 의미있는 이름을 짓도록 해야 함.

**매개변수 선언**

- **매개변수** : 메서드가 작업을 수행하는데 필요한 값들(입력)을 제공 받기 위한 것
- 필요한 값의 개수만큼 변수를 선언하고, 변수 간의 구분은 쉼표 사용.
- 일반적인 변수 선언과 달리 두 변수의 타입이 같아도 변수의 타입을 생략할 수 없음.
    
    ```java
    int add(int x, int y) // OK.
    int add(int x, y) // 에러발생. 매개변수 y의 타입이 없음.
    ```
    
    입력해야 할 값의 개수가 많은 경우 배열이나 참조변수 사용하고, 입력 받을 필요가 없다면 괄호 안에 아무 것도 적지 않음.
    

**반환타입(return type)**

- 메서드의 작업 수행 결과인 반환값의 타입을 적음.
- 반환값이 없는 경우 반환 타입으로 void 작성.

### 메서드의 구현부(method body, 메서드 몸통)

**메서드의 구현부** : 메서드의 선언부 다음에 오는 괄호{}

- 메서드를 호출했을 때 수행될 문장들을 작성.

**return문**

- 메서드의 반환 타입이 void가 아닐 경우, 구현부{} 안에 **return 반환값;** 이 반드시 포함.
- 작업을 수행한 결과인 반환값을 호출한 메서드로 전달하는데, 값의 타입은 **반환 타입과 일치하거나 적어도 자동 형변환이 가능**해야 함.
- return문은 단 하나의 값만 반환 가능. (입력은 여러 개일 수 있지만, 출력은 최대 하나만 허용.)

**지역변수**

- **지역변수** : 메서드 내에 선언된 변수
- 지역변수는 그 메서드 내에서만 사용할 수 있으므로 서로 다른 메서드라면 같은 이름의 변수 선언이 가능.

## 메서드의 호출

```java
메서드를 호출하는 방법

**메서드이름(값1, 값2, ...)**
```

**인자(argument)와 매개변수(parameter)**

**인자(인수)** : 메서드를 호출할 때 괄호()안에 지정해준 값들

- 인자의 개수와 순서는 호출된 메서드에 선언된 매개변수와 일치해야 함.
- 인자는 메서드가 호출되면서 매개변수에 대입되므로, 인자의 타입은 매개변수의 타입과 일치하거나 자동 형변환이 가능한 것이어야 함.

**메서드의 실행흐름**

같은 클래스 내의 메서드끼리는 참조변수를 사용하지 않고도 서로 호출이 가능하지만 static메서드는 같은 클래스 내의 인스턴스 메서드를 호출할 수 없다.

```java
class MyMathTest {
    public static void main(String[] args) {
        MyMath mm = new MyMath();
        long result1 = mm.add(5L, 3L);

        System.out.println("add(5L, 3L) = " + result1);
}

class MyMath {
    long add(long a, long b)
    {
        long result = a + b;
        return result;
				//return a + b; 로 표현 가능.
    }

    long subtract(long a, long b) { return a - b; }
    long multiply(long a, long b) { return a * b; }
    double divide(double a, double b) { return a / b; }
}
```

1. main메서드에서 메서드 add를 호출. 
    
    호출 시 지정한 5L, 3L이 메서드 add의 매개변수 a, b에 각각 복사.
    
2. 메서드 add의 괄호{} 안에 있는 문장들이 순서대로 수행.
    
    
3. 메서드 add의 모든 문장이 실행되거나 return문을 만나면, 호출한 메서드로 되돌아와서 이후 문장 실행.

```java
//ex6
class MyMathTest {
    public static void main(String[] args) {
        MyMath mm = new MyMath();
        long result1 = mm.add(5L, 3L);
        long result2 = mm.subtract(5L, 3L);
        long result3 = mm.multiply(5L, 3L);
        double result4 = mm.divide(5L, 3L);

        System.out.println("add(5L, 3L) = " + result1);
        System.out.println("subtract(5L, 3L) = " + result2);
        System.out.println("multiply(5L, 3L) = " + result3);
        System.out.println("divide(5L, 3L) = " + result4);
    }
}

class MyMath {
    long add(long a, long b)
    {
        long result = a + b;
        return result;
    }

    long subtract(long a, long b) { return a - b; }
    long multiply(long a, long b) { return a * b; }
    double divide(double a, double b) { return a / b; }
}

실행결과
add(5L, 3L) = 8
subtract(5L, 3L) = 2
multiply(5L, 3L) = 15
divide(5L, 3L) = 1.6666666666666667
```

## return문

- return문은 현재 실행 중인 메서드를 종료하고 호출한 메서드로 돌아감.
- 반환값의 유뮤에 관계없이 모든 메서드에는 적어도 하나의 return문이 있어야 함.
- 반환타입이 void인 경우 return문이 없어도 컴파일러가 메서드의 마지막에 return; 을 자동적으로 추가해주었기 때문에 문제가 없었음.

**반환값(return value)**

```java
int add(int x, int y)
{
		int result = x + y;           
		return result;
}

-> int add(int x, int y)
	{
			 return x + y;
	}	
```

아래의 코드는 return문의 반환값으로 수식이 적혀있지만, 수식이 반환되는 것이 아니라, 이 수식을 계산한 결과가 반환됨.

**매개변수의 유효성 검사**

- 메서드의 구현부{} 작성 시, 제일 먼저 매개변수의 값이 적절한 것인지 확인해야 함.
- 타입만 맞는다면 어떤 값도 매개변수를 통해 넘어올 수 있기에, 가능한 모든 경우의 수에 대해 고민하고 그에 대비한 코드를 작성해야 함.
    
    ```java
    float divide(int x, int y) 
    {
    			if (y == 0)
    			{
    						System.out.println("0으로 나눌 수 없습니다.");
    						return 0;  // 매개변수가 유효하지 않으므로 메서드 종료.
    			}
    			return x / (float) y;
    }
    ```
    

## JVM의 메모리 구조

응용프로그램이 실행되면, JVM은 시스템으로부터 프로그램을 수행하는데 필요한 메모리를 할당 받고 이 메모리를 용도에 따라 여러 영역으로 나누어 관리함.

![Untitled](https://github.com/DongHyeon1004/Java/blob/main/Java/image/6-6.png)

1. **메서드 영역(method area)**
    - 프로그램 실행 중 어떤 클래스가 사용되면, 해당 클래스의 클래스파일(*.class)을 읽고 분석하여 클래스에 대한 정보(클래스 데이터)를 저장.
    - 클래스변수도 이 영역에 함께 생성.

1. **힙(heap)**
    - 인스턴스변수들이 생성되는 공간.
    - 프로그램 실행 중 생성되는 인스턴스는 모두 이곳에 생성.

1. **호출스택(call stack 또는 execution stack)**
    - 메서드의 작업에 필요한 메모리 공간을 제공.
    - 메서드 호출 시, 호출된 메서드를 위한 메모리가 할당.
    - 할당된 메모리는 메서드가 작업을 수행하는 동안 지역변수(매개변수 포함)들과 연산의 중간결과 등을 저장하는데 사용.
    - 메서드가 작업을 끝내면 할당됐던 메모리 공간은 반환되어 비워짐.
    - **호출스택의 특징**
        - 메서드가 호출되면 수행에 필요한 만큼의 메모리를 스택에 할당받음.
        - 메서드가 수행을 마치고 나면 사용했던 메모리를 반환하고 스택에서 제거됨.
        - 호출스택의 제일 위에 있는 메서드가 현재 실행 중인 메서드임.
        - 아래에 있는 메서드가 바로 위의 메서드를 호출한 메서드임.

```java
//ex7
class CallStackTest {
    public static void main(String[] args) {
        firstMethod();
    }

    static void firstMethod() {
        secondMethod();
    }

    static void secondMethod() {
        System.out.println("secondMethod()");
    }
}

실행결과
secondMethod()
```

```java
//ex8
class CallStackTest2 {
    public static void main(String[] args) {
        System.out.println("main(String[] args)이 시작되었음.");
        firstMethod();
        System.out.println("main(String[] args이 끝났음.");
    }

    static void firstMethod() {
        System.out.println("firstMethod()이 시작되었음.");
        secondMethod();
        System.out.println("firstMethod()이 끝났음.");
    }

    static void secondMethod() {
        System.out.println("secondMethod()이 시작되었음.");
        System.out.println("secondMethod()이 끝났음.");
    }
}

실행결과
main(String[] args)이 시작되었음.
firstMethod()이 시작되었음.
secondMethod()이 시작되었음.
secondMethod()이 끝났음
firstMethod()이 끝났음.
main(String[] args이 끝났음.
```

## 기본형 매개변수와 참조형 매개변수

매개변수 타입이 기본형일 때는 기본형 값이 복사되지만, 참조형이면 인스턴스의 주소가 복사된다.

- **기본형 매개변수** : 변수의 값을 읽기만 할 수 있다. (read only)
- **참조형 매개변수** : 변수의 값을 읽고 변경할 수 있다. (read & write)

```java
//ex9
class Data { int x; }

class PrimitiveParamEx {
    public static void main(String[] args) {
        Data d = new Data();
        d.x = 10;
        System.out.println("main() : x = " + d.x); // main() : x = 10

        change(d.x);
        System.out.println("After change(d.x)");
        System.out.println("main() : x = " + d.x); // main() : x = 10
    }

    static void change(int x) {
        x = 1000;
        System.out.println("change() : x = " + x); // change() : x = 1000
    }
}

실행결과
main() : x = 10
change() : x = 1000
After change(d.x)
main() : x = 10
```

1. change메서드가 호출되면서 ‘d.x’가 change메서드의 매개변수 x에 복사됨.
2. change메서드에서 x의 값을 1000으로 변경.
3. change메서드가 종료되면서 매개변수 x는 스택에서 제거.

원본이 아닌 복사본이 변경된 것이라 원본에는 영향을 끼치지 못한다. 이렇게 기본형 매개변수는 변수에 저장된 값만 읽을 수만 있을 뿐 변경은 불가능하다.

```java
//ex10
class Data { int x; }

class ReferenceParamEx {
    public static void main(String[] args) {
        Data d = new Data();
        d.x = 10;
        System.out.println("main() : x = " + d.x); // main() : x = 10

        change(d);
        System.out.println("After change(d)");
        System.out.println("main() : x = " + d.x); // main() : x = 1000
    }

    static void change(Data d) {
        d.x = 1000;
        System.out.println("change() : x = " + d.x); // change() : x = 1000
    }
}

실행결과
main() : x = 10
change() : x = 1000
After change(d)
main() : x = 1000
```

change메서드의 매개변수가 잠초형이라서 값이 저장된 주소를 change메서드에게 넘겨주었기 때문에 값을 읽는 것 뿐만 아니라 변경하는 것도 가능하다.

1. change메서드가 호출되면서 참조변수 d의 값(주소)이 매개변수 d에 복사.
2. change메서드에서 매개변수 d로 x의 값을 1000으로 변경.
3. change메서드가 종료되면서 매개변수 d는 스택에서 제거.

```java
//ex11
class ReferenceParamEx2 {
    public static void main(String[] args) {
        int x[] = { 10 };
        System.out.println("main() : x = " + x[0]); // main() : x = 10

        change(x);
        System.out.println("After change(x)");
        System.out.println("main() : x = " + x[0]); // main() : x = 1000
    }

    static void change(int x[])
    {
        x[0] = 1000;
        System.out.println("change() : x = " + x[0]); // change() : x = 1000
    }
}

실행결과
main() : x = 10
change() : x = 1000
After change(d)
main() : x = 1000
```

변수 x도 int배열 타입의 참조 변수이기 때문에 앞에 예시와 같은 결과를 얻는다.

```java
//ex12
class ReferenceParamEx3 {
    public static void main(String[] args) {
        int arr[] = new int[] { 3, 2, 1, 6, 5, 4 };

        printArr(arr);
        sortArr(arr);
        printArr(arr);
        System.out.println("sum = " + sumArr(arr));
    }

    static void printArr(int arr[])
    {
        System.out.print("[");

        for (int i : arr)
            System.out.print(i + ",");
        System.out.println("]");
    }

    static int sumArr(int arr[])
    {
        int sum = 0;

        for (int i = 0; i < arr.length; i++)
            sum += arr[i];
        return sum;
    }

    static void sortArr(int arr[])
    {
        for (int i = 0; i < arr.length - 1; i++)
            for (int j = 0; j < arr.length - 1; j++)
                if (arr[j] > arr[j+1])
                {
                    int tmp = arr[j+1];
                    arr[j] = arr[j+1];
                    arr[j+1] = tmp;
                }
    }
}

실행결과
[3, 2, 1, 6, 5, 4]
[1, 2, 3, 4, 5, 6]
sum = 21
```

```java
//ex13
class ReturnTest {
    public static void main(String[] args) {
        ReturnTest r = new ReturnTest();

        int result = r.add(3,5);
        System.out.println(result);

        int result2[] = { 0 };
        r.add(3,5,result2);
        System.out.println(result2[0]);
    }

    int add(int a, int b)
    {
        return a + b;
    }

    void add(int a, int b, int result[])
    {
        result[0] = a + b;
    }
}

실행결과
8
8
```

## 참조형 반환타입

```java
//ex14
class Data { int x; }

class ReferenceReturnEx {
    public static void main(String[] args) {
        Data d = new Data();
        d.x = 10;
        
        Data d2 = copy(d);
        System.out.println("d.x = " + d.x); // d.x = 10
        System.out.println("d2.x = " + d2.x); // d2.x = 10
    }
    
    static Data copy(Data d)
    {
        Data tmp = new Data();
        tmp.x = d.x;
        
        return tmp;
    }
}

실행결과
d.x = 10
d2.x = 10
```

1. copy메서드를 호출하면서 참조변수 d의 갑이 매개변수 d에 복사.
2. 새로운 객체를 생성한 다음, d.x에 저장된 값을 tmp.x에 저장.
3. copy메서드가 종료되면서 반환한 tmp의 값은 참조변수 d2에 저장.
4. cpoy메서드가 종료되어 tmp가 사라졌지만, d2로 새로운 객체를 다룰 수 있음.

**반환 타입이 참조형이다. = 메서드가 객체의 주소를 반환한다.**

## 재귀호출(recursive call)

**재귀호출** : 메서드 내부에서 메서드 자신을 다시 호출하는 것

```java
void method() {
		 method();
}
// 무한히 자기 자신을 호출하기 때문에 무한반복에 빠지게 된다.
// 조건문이 필수적으로 필요하다. 
```

- 호출된 메서드는 값에 의한 호출(call by value)을 통해, 원래의 값이 아닌 복사된 값으로 작업하기 때문에 호출한 메서드와 관계없이 독립적인 수행이 가능하다.
- 메서드를 호출하는 것은 매개변수 복사와 종료 후 복귀할 주소 저장 등 반복문보다 몇 가지 과정이 추가로 필요하기 때문에 재귀호출의 수행시간이 더 길다.
- 재귀호출은 비효율적이므로 재귀호출에 드는 비용보다 재귀호출의 간결함이 주는 이득이 충분히 큰 경우에만 사용해야 한다.

**재귀호출을 사용하는 이유**

- **논리적 간결함**
    - 몇 겹의 반복문과 조건문으로 복잡하게 작성된 코드가 재귀호출로 작성하면 보다 단순한 구조로 바뀔 수 있다.
    - 다소 비효율적이라도 알아보기 쉽게 작성하는 것이 논리적 오류가 발생할 확률도 줄어들고 나중에 수정하기도 편리하다.

```java
//ex15
class FactorialTest {
    public static void main(String[] args) {
        int result = factorial(2);

        System.out.println(result);
    }

    static int factorial(int n) {
        if (n == 1) return 1;
				return n * factorial(n - 1);
    }
}

실행결과
24
```

factorial(2) 호출 시 실행과정

1. factorial(2)를 호출하면서 매개변수 n에 2가 복사된다.
2. return 2 * factorial(1); 을 계산하려면 factorial(1)을 호출한 결과가 필요하다. 그래서 factorial(1)이 호출되고 매개변수 n에 1이 복사된다.
3. if문의 조건식이 참이므로 1을 반환하면서 메서드는 종료된다. 그리고 factorial(1)을 호출한 곳으로 돌아간다.
4. 이제 factorial(1)의 결과값인 1을 얻었으므로, return문이 다음의 과정으로 계산된다.
    
    return 2 * factorial(1); 
    
    → return 2 * 1;
    
    → return 2;
    
    factorial(2)는 종료되면서 결과값 2를 반환하고, 이 값은 result에 저장된다.
    

매개변수의 값이 올바르지 않으면 어느 시점에 이르러서는 스택의 저장 한계를 넘게 되고, 스택 오버플로우 에러가 발생한다. 매개변수의 유효성 검사가 중요한 이유다.

```java
//ex16
class FactorialTest2 {
    static long factorial(int n)
    {
        if (n <= 0 || n > 20) return -1;
        if (n <= 1) return 1;
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {
        int n = 21;
        long result = 0;

        for (int i = 1; i <= n; i++)
        {
            result = factorial(i);

            if (result == -1)
            {
                System.out.printf("유효하지 않은 값입니다 (0 <= n < 20) : %d%n", n);
                break;
            }

            System.out.printf("%2d! = %20d%n", i, result);
        }
    }
}

실행결과
 1! =                    1
 2! =                    2
 3! =                    6
 4! =                   24
 5! =                  120
 6! =                  720
 7! =                 5040
 8! =                40320
 9! =               362880
10! =              3628800
11! =             39916800
12! =            479001600
13! =           6227020800
14! =          87178291200
15! =        1307674368000
16! =       20922789888000
17! =      355687428096000
18! =     6402373705728000
19! =   121645100408832000
20! =  2432902008176640000
유효하지 않은 값입니다 (0 <= n < 20) : 21
```

```java
//ex17
class MainTest {
    public static void main(String[] args) {
        main(null);
    }
}

실행결과
java.lang.StackOverflowError
			at.MainTest.main(mainTest.java:3)
			at.MainTest.main(mainTest.java:3)
			...
			at.MainTest.main(mainTest.java:3)
			at.MainTest.main(mainTest.java:3)
```

```java
//ex18
class PowerTest {
    public static void main(String[] args) {
        int x = 2;
        int n = 5;
        long result = 0;

        for (int i = 1; i <= n; i++)
        {
            result += power(x, i);
        }

        System.out.println(result);
    }

    static long power(int x, int n)
    {
        if (n == 1) return x;
        return x * power(x, n - 1);
    }
}

실행결과
62
```

## 클래스 메서드(static 메서드)와 인스턴스 메서드

- 인스턴스 메서드는 인스턴스 변수와 관련된 작업을 하는, 즉 메서드의 작업을 수행하는데 인스턴스 변수를 필요로 하는 메서드이다.
- 인스턴스와 관계없는(인스턴스 변수나 인스턴스 메서드를 사용하지 않는) 메서드를 클래스 메서드(static 메서드)로 정의한다.

1. **클래스를 설계할 때, 멤버변수 중 모든 인스턴스에 공통으로 사용하는 것에 static을 붙인다.**
    
    모든 인스턴스에서 같은 값이 유지되어야 하는 변수는 static을 붙여서 클래스 변수로 정의해야 한다.
    
2. **클래스 변수(static 변수)는 인스턴스를 생성하지 않아도 사용할 수 있다.**
    
    클래스 변수는 클래스가 메모리에 올라갈 때 이미 자동적으로 생성되기 때문이다.
    
3. **클래스 메서드(static 메서드)는 인스턴스 변수를 사용할 수 없다.**
    
    클래스 메서드는 인스턴스 생성 없이 호출 가능하므로 클래스 메서드가 호출되었을 때 인스턴스가 존재하지 않을 수도 있다. 그래서 클래스 메서드에서 인스턴스 변수의 사용을 금지한다.
    
    인스턴스 변수나 인스턴스 메서드에서는 static이 붙은 멤버들을 사용하는 것이 언제나 가능하다. 인스턴스 변수가 존재한다는 것은 static변수가 이미 메모리에 존재한다는 것을 의미한다.
    
4. **메서드 내에서 인스턴스 변수를 사용하지 않는다면, static을 붙이는 것을 고려한다.**
    
    static을 안 붙인 메서드(인스턴스 메서드)는 실행 시 호출되어야 할 메서드를 찾는 과정이 추가적으로 필요하기 때문에 시간이 더 걸린다.
    

```java
//ex19
class MyMath2 {
    long a, b;

    long add() { return a + b; }
    long subtract() { return a - b; }
    long multiply() { return a * b; }
    double divide() { return a / b; }

    static long add(long a, long b) { return a + b; }
    static long subtract(long a, long b) { return a - b; }
    static long multiply(long a, long b) { return a * b; }
    static double divide(double a, double b) { return a / b; }
}

class MyMathTest2 {
    public static void main(String[] args) {
        System.out.println(MyMath2.add(200L, 100L));
        System.out.println(MyMath2.subtract(200L, 100L));
        System.out.println(MyMath2.multiply(200L, 100L));
        System.out.println(MyMath2.divide(200.0, 100.0));

        MyMath2 mm = new MyMath2();
        mm.a = 200L;
        mm.b = 100L;

        System.out.println(mm.add());
        System.out.println(mm.subtract());
        System.out.println(mm.multiply());
        System.out.println(mm.divide());
    }
}

실행결과
300
100
20000
2.0
300
100
20000
2.0
```

## 클래스 멤버와 인스턴스 멤버간의 참조와 호출

- 같은 클래스에 속한 멤버들 간에는 인스턴스를 생성하지 않고도 서로 참조 / 호출이 가능하다.
- **인스턴스 멤버가 존재하는 시점에 클래스 멤버는 항상 존재하지만, 클래스멤버가 존재하는 시점에 인스턴스 멤버가 존재하지 않을 수도 있기 때문**에, 클래스 멤버가 인스턴스 멤버를 참조 / 호출하는 경우 인스턴스를 생성해야 한다.

```java
//ex20
class MemberCall {
    int iv = 10;
    static int cv = 20;
    
    int iv2 = cv;
    // static int cv2 = iv; // 에러. 클래스 변수는 인스턴스 변수를 사용할 수 없음.
    static int cv2 = new MemberCall().iv; // 객체를 생성해야 사용 가능.
    
    static void staticMethod1()
    {
        System.out.println(cv);
        //System.out.println(iv); // 에러. 클래스 변수는 인스턴스 변수를 사용할 수 없음.
        MemberCall c = new MemberCall();
        System.out.println(c.iv); // 객체를 생성한 후에야 인스턴스 변수의 참조 가능.
    }
    
    void instanceMethod1()
    {
        System.out.println(cv);
        System.out.println(iv); // 인스턴스 메서드에서는 인스턴스 변수를 바로 사용가능.
    }
    
    static void staticMethod2()
    {
        staticMethod1();
        //instanceMethod1(); // 에러. 클래스 메서드에서는 인스턴스 메서드를 호출할 수 없음.
        MemberCall c = new MemberCall();
        c.instanceMethod1(); // 인스턴스를 생성한 후에 호출 가능.
    }
    
    void instanceMethod2() // 인스턴스 메서드에서는 인스턴스 메서드와 클래스 메서드 모두 
		{                      // 인스턴스 생성없이 바로 호출 가능.
        staticMethod1();
        instanceMethod1();
    }
}
```

- 클래스 멤버(클래스 변수, 클래스 메서드)는 언제나 참조 / 호출이 가능.
- 인스턴스 멤버(인스턴스 변수, 인스턴스 메서드)는 반드시 객체를 생성한 후에 참조 / 호출 가능.
- 하지만, **인스턴스 멤버간의 호출에는 문제가 없음. 하나의 인스턴스 멤버가 존재한다는 것은 인스턴스가 이미 생성됐다는 것을 의미하며, 즉 다른 인스턴스 멤버들도 모두 존재하기 때문.**

---

# 오버로딩

## 오버로딩이란?

자바에서는 한 클래스 내에 이미 사용하려는 이름과 같은 이름을 가진 메서드가 있더라도 매개변수의 개수 또는 타입이 다르면, 같은 이름을 사용해서 메서드를 정의할 수 있다.

**오버로딩** : 한 클래스 내에서 같은 이름의 메서드를 여러 개 정의한 것

## 오버로딩의 조건

1. 메서드 이름이 같아야 한다.
2. 매개변수의 개수 또는 타입이 달라야 한다.

**반환 타입은 오버로딩을 구현하는데 아무런 영향을 주지 못한다.**

## **오버로딩의 예**

- **println메서드**
    
    println메서드를 호출할 때 매개변수로 지정하는 값의 타입에 따라서 호출되는 println메서드가 달라진다.
    
    ```java
    PrintStream 클래스에 오버로딩된 println메서드 정의
    
    void println()
    void println(boolean x)
    void println(char x)
    void println(char[] x)
    void println(double x)
    void println(float x)
    void println(int x)
    void println(long x)
    void println(Object x)
    void println(String x)
    ```
    
- **예시 1**
    
    ```java
    int add(int a, int b) { return a + b; }
    int add(int x, int y) { return x + y; }
    ```
    
    매개변수의 이름만 다를 뿐 매개변수의 타입이 같기 때문에 오버로딩이 성립하지 않는다.
    
- **예시 2**
    
    ```java
    int add(int a, int b) { return a + b; }
    long add(int a, int b) { return a + b; }
    ```
    
    리턴 타입만 다르고, 매개변수의 타입과 개수가 일치하기 때문에 add(3,3)을 호출했을 때 어떤 메서드가 호출된 것인지 결정할 수 없기 때문에 오버로딩으로 간주되지 않는다.
    
- **예시 3**
    
    ```java
    long add(int a, long b) { return a + b; }
    long add(long a, int b) { return a + b; }
    ```
    
    호출 시 매개변수의 값에 의해 호출될 메서드가 구분될 수 있으므로 중복된 메서드가 아닌, 오버로딩으로 간주한다.
    
    매개변수의 순서만을 다르게 하여 오버로딩을 구현하면, 사용자가 매개변수의 순서를 외우지 않아도 되는 장점이 있지만, 오히려 단점이 될 수 있다.
    
    add(3,3)을 호출하는 경우 두 메서드 중 어느 메서드가 호출된 것인지 알 수 없기 때문에 메서드를 호출하는 곳에서 컴파일 에러가 발생한다.
    
- **예시 4**
    
    ```java
    int add(int a, int b) { return a + b; }
    long add(long a, long b) { return a + b; }
    long add(int a[]) 
    {
    		long result = 0;
    		
    		for (int i = 0; i < a.length; i++)
    		{
    					result += a[i];
    		}
    		return result;
    }
    ```
    
    같은 일을 하지만 매개변수를 달리 해야하는 경우에, 이렇게 이름은 같고 매개변수를 다르게 하여 오버로딩을 구현한다.
    

## 오버로딩의 장점

1. 여러 메서드들이 하나의 이름으로 정의될 수 있다면, 이름만 기억하면 되므로 기억하기도 쉽고 이름도 짧게 할 수 있어서 오류의 가능성을 많이 줄일 수 있다.
2. 메서드의 이름만 보고도 ‘이름이 같으니, 같은 기능을 하겠구나’라고 쉽게 예측할 수 있다.
3. 하나의 이름으로 여러 개의 메서드를 정의할 수 있으니, 메서드의 이름을 짓는데 고민을 덜 수 있는 동시에 사용됐어야 할 메서드 이름을 다른 메서드의 이름으로 사용할 수 있다.

```java
//ex21
class OverloadingTest {
    public static void main(String[] args) {
        MyMath3 mm = new MyMath3();
        System.out.println("mm.add(3, 3) 결과 : " + mm.add(3,3));
        System.out.println("mm.add(3L, 3) 결과 : " + mm.add(3L,3));
        System.out.println("mm.add(3, 3L) 결과 : " + mm.add(3,3L));
        System.out.println("mm.add(3L, 3L) 결과 : " + mm.add(3L,3L));

        int a[] = { 100, 200, 300 };
        System.out.println("mm.add(a) 결과 : " + mm.add(a));
    }
}

class MyMath3 {
    int add(int a, int b)
    {
        System.out.println("int add(int a,int b) - ");
        return a + b;
    }

    long add(int a, long b)
    {
        System.out.println("long add(int a, long b) - ");
        return a + b;
    }

    long add(long a, int b)
    {
        System.out.println("long add(long a, int b) - ");
        return a + b;
    }

    long add(long a, long b)
    {
        System.out.println("long add(long a, long b) - ");
        return a + b;
    }

    int add(int a[])
    {
        System.out.println("int add(int a[]) - ");
        int result = 0;
        for (int i = 0; i < a.length; i++)
        {
            result += a[i];
        }
        return result;
    }
}

실행결과
int add(int a,int b) - mm.add(3, 3) 결과 : 6
long add(long a, int b) - mm.add(3L, 3) 결과 : 6
long add(int a, long b) - mm.add(3, 3L) 결과 : 6
long add(long a, long b) - mm.add(3L, 3L) 결과 : 6
int add(int a[]) - mm.add(a) 결과 : 600
```

## 가변인자(varargs)와 오버로딩

**가변인자** : 메서드의 매개변수 개수를 동적으로 지정해 주는 것. **타입… 변수명** 형식으로 선언

```java
public PrintScream printf(String format, Object… args) { … }
```

가변인자 외에도 매개변수가 더 있다면, 가변인자인지 아닌지를 구별할 방법이 없기 때문에 가변인자를 매개변수 중에서 제일 마지막에 선언해야 한다.

```java
public PrintStream printf(Object... args, String format) { ... } //컴파일 에러 발생.
```

```java
String concatenate(String... str) { ... }

System.out.println(concatenate()); // 인자 없음
System.out.println(concatenate("a")); // 인자 하나
System.out.println(concatenate("a", "b")); // 인자 둘
System.out.println(concatenate(new String[]{"A","B"})); // 배열도 가능
```

가변인자는 내부적으로 배열을 이용하는 것이기 때문에 가변인자가 선언된 메서드를 호출할 때마다 배열이 새로 생성된다. 가변인자가 편리하지만, 비효율이 숨어있으므로 꼭 필요한 경우에만 가변인자를 사용하는 것이 좋다.

```java
//ex22
class VarArgsEx {
    public static void main(String[] args) {
        String strArr[] = { "100", "200", "300" };

        System.out.println(concatenate("", "100", "200", "300"));
        System.out.println(concatenate("-", strArr));
        System.out.println(concatenate(",", new String[]{"1", "2", "3"}));
        System.out.println("[" + concatenate(",", new String[0] + "]"));
        System.out.println("[" + concatenate(",") + "]");
    }

    static String concatenate(String delim, String... args)
    {
        String result = "";

        for (String str : args)
        {
            result += str + delim;
        }

        return result;
    }
}

실행결과
100200300
100-200-300-
1, 2, 3,
[]
[]
```

가변인자를 선언한 메서드를 오버로딩하면, 메서드를 호출했을 때 구별되지 못하는 경우가 발생하기 쉽기 때문에 주의해야 한다. 가능하면 가변인자를 사용한 메서드는 오버로딩하지 않는 것이 좋다.

---

# 생성자(Constructor)

## 생성자란?

**생성자** : 인스턴스가 생성될 때 호출되는 인스턴스 초기화 메서드

- 인스턴스 변수의 초기화 작업에 주로 사용되고, 인스턴스 생성 시에 실행되어야 할 작업을 위해서도 사용됨.
- 메서드처럼 클래스 내에 선언되며, 구조도 메서드와 유사하지만 리턴값이 없다. 생성자 앞에 void를 사용하지 않고, 아무것도 적지 않는다.
- 생성자의 조건
    1. 생성자의 이름은 클래스의 이름과 같아야 한다.
    2. 생성자는 리턴 값이 없다.

**생성자 정의 방법**

```java
클래스이름(타입 변수명, 타입 변수명, ...) {
		// 인스턴스 생성 시 수행될 코드,
		// 주로 인스턴스 변수의 초기화 코드
}

class Card() {
		Card() {  // 매개변수가 없는 생성자
				...
		}

		Card(String k, int num) {  // 매개변수가 있는 생성자
				...
		}
		...
}
```

연산자 new가 인스턴스를 생성하는 것이지 생성자가 인스턴스를 생성하는 것이 아니다

**Card c = new Card();**

1. 연산자 new에 의해서 메모리(heap)에 Card클래스의 인스턴스가 생성된다.
2. 생성자 Card()가 호출되어 수행된다.
3. 연산자 new의 결과로, 생성된 Card인스턴스의 주소가 반환되어 참조변수 c에 저장된다.

## 기본 생성자(default constructor)

**기본 생성자** : 클래스에는 반드시 하나 이상의 생성자가 정의되어 있어야 하지만, 클래스에 생성자를 정의하지 않고도 인스턴스를 생성할 수 있게 해주는 것

```java
클래스이름() { }

Card() { } // 매개변수도 없고 아무런 내용도 없는 간단한 것
```

컴파일 할 때, 소스파일의 클래스에 생성자가 하나도 정의되지 않은 경우 컴파일러는 자동적으로 기본 생성자를 추가하여 컴파일한다.

```java
//ex23
class Data1 {
    int value;
}

class Data2 {
    int value;

    Data2 (int x) {
        value = x;
    }
}

class ConstructorTest {
    public static void main(String[] args) {
        Data1 d1 = new Data1;
        Data2 d2 = new Data2; // 컴파일 에러 발생
    }
}

실행결과
ConstructorTest.java:15: cannot resolve symbol
symbol : constructor Data2 ()
location : class Data2
						 Data2 d2 = new Data2();
^
1 error
```

Data1에는 정의되어 있는 생성자가 하나도 없으므로 컴파일러가 기본 생성자를 추가해주었지만, Data2에는 이미 생성자 Data2(int x)가 정의되어 있으므로 기본 생성자가 추가되지 않았기 때문에 컴파일 에러가 발생한다.

**기본 생성자가 컴파일러에 의해 추가되는 경우는 클래스에 정의된 생성자가 하나도 없을 때 뿐이다.**

## 매개변수가 있는 생성자

생성자도 메서드처럼 매개변수를 선언하여 호출 시 값을 넘겨 받아서 인스턴스의 초기화 작업에 사용 가능하다.

인스턴스마다 다른 값으로 초기화되어야 하는 경우가 많기 때문에 유용하다.

```java
class Car {
		String color;
		String gearType;
		int door;

		Car() {}   // 생성자
		Car(String c, String g, int d) {   // 생성자
				 color = c;
				 gearType = g;
				 door = d;
		}
}
```

**Car()**

인스턴스를 생성한 다음에 인스턴스변수들을 따로 초기화 해주어야 한다.

**Car(String c, String g, int d)**

인스턴스를 생성하는 동시에 원하는 값으로 초기화 할 수 있다.

```java
Car c = new Car();                           
c.color = "white";
c.gearType = "auto";                  ->      Car c = new Car("white", "auto", 4);
c.door = 4;
```

인스턴스를 생성한 다음에 인스턴스변수의 값을 변경하는 것보다 매개변수를 갖는 생성자를 사용하는 것이 코드를 보다 간결하고 직관적으로 만든다.

```java
//ex24
class Car {
    String color;
    String gearType;
    int door;

    Car() {}
    Car(String c, String g, int d) {
        color = c;
        gearType = g;
        door = d;
    }
}

class CarTest {
    public static void main(String[] args) {
        Car c1 = new Car();
        c1.color = "white";
        c1.gearType = "auto";
        c1.door = 4;

        Car c2 = new Car("white", "auto", 4);

        System.out.println("c1의 color = " + c1.color + ", gearType = " + c1.gearType + ", door = " + c1.door);
        System.out.println("c2의 color = " + c2.color + ", gearType = " + c2.gearType + ", door = " + c2.door);
    }
}

실행결과
c1의 color = white, gearType = auto, door = 4
c2의 color = white, gearType = auto, door = 3
```

## 생성자에서 다른 생성자 호출하기 - this(), this

******this :** 인스턴스 자신을 가리키는 참조변수, 인스턴스의 주소가 저장되어 있다. 모든 인스턴스 메서드에 지역변수로 숨겨진 채 존재한다.

**this(), this(매개변수)** : 생성자, 같은 클래스의 다른 생성자를 호출할 때 사용한다.

**생성자 간에 호출 가능 조건**

1. **생성자의 이름으로 클래스이름 대신 this를 사용한다.**
    
    
2. **한 생성자에서 다른 생성자를 호출할 때는 반드시 첫 줄에서만 호출이 가능하다.**
    
    생성자 내에서 초기화 작업 도중에 다른 생성자를 호출하게 되면, 호출된 다른 생성자 내에서도 멤버변수들의 값을 초기화를 할 것이므로 다른 생성자를 호출하기 이전의 초기화 작업이 무의미해질 수 있기 때문이다. 
    

```java
Car(String color) {
		 door = 5;
		 Car(color, "auto", 4);  // 에러1. 생성자의 두 번째 줄에서 다른 생성자 호출
}                            // 에러2. this(color, "auto", 4); 로 해야함
```

생성자 내에서 다른 생성자를 호출할 때는 클래스 이름 대신 this를 사용해야 한다.

생성자 호출은 첫 번째 줄에서 이뤄져야 한다.

```java
//ex25
class Car {
    String color;
    String gearType;
    int door;

    Car() {
        this("white", "auto", 4);   // Car(String color, String gearType, int door)를 호출
    }

    Car(String color) {
        this(color, "auto", 4);
    }

    Car(String color, String gearType, int door) {
        this.color = color;
        this.gearType = gearType;
        this.door = door;
    }
}

class CarTest2 {
    public static void main(String[] args) {
        Car c1 = new Car();
        Car c2 = new Car("blue");

        System.out.println("c1의 color = " + c1.color + ", gearType = " + c1.gearType + ", door = " + c1.door);
        System.out.println("c2의 color = " + c2.color + ", gearType = " + c2.gearType + ", door = " + c2.door);
    }
}

실행결과
c1의 color = white, gearType = auto, door = 4
c2의 color = blue, gearType = auto, door = 4
```

생성자 간의 호출에는 생성자의 이름 대신 this를 사용해야만 하므로 Car 대신 this를 사용했고, 생성자 Car()의 첫째 줄에서 호출했다.

같은 클래스 내의 생성자들은 일반적으로 서로 관계가 깊은 경우가 많아서 서로 호출하도록 하여 유기적으로 연결해주면 더 좋은 코드를 얻을 수 있고, 수정이 필요한 경우에도 보다 적은 코드만을 변경하면 되므로 유지보수가 쉬워진다.

```java
Car(String color, String gearType, int door) {
		this.color = color;
		this.gearType = gearType;
		this.door = door;
}
```

- 생성자의 매개변수로 선언된 변수의 이름이 color로 인스턴스변수 color와 같은 경우에 이름만으로는 두 변수가 서로 구분이 안되므로, 인스턴스변수 앞에 this를 사용하면 된다.
- this.color은 인스턴수변수이고, color는 생성자의 매개변수로 정의된 지역변수로 구별이 가능하다.
- this를 사용할 수 있는 것은 인스턴스멤버뿐이다. 클래스 메서드는 인스턴스를 생성하지 않고도 호출될 수 있으므로 클래스 메서드가 호출된 시점에 인스턴스가 존재하지 않을 수도 있기 때문이다.

## 생성자를 이용한 인스턴스의 복사

현재 사용하고 있는 인스턴스와 **같은 상태(두 인스턴스의 모든 인스턴스 변수가 동일한 값을 갖고 있다)**를 갖는 인스턴스를 하나 더 만들고자 할 때 생성자를 이용할 수 있다.

```java
Car(Car c) {
		color = c.color;
		gearType = c.gearType;
		door = c.door;
}
```

매개변수로 넘겨진 참조변수가 가리키는 Car인스턴스의 인스턴스변수인 color, gearType, door의 값을 인스턴스 자신으로 복사한다.

어떤 인스턴스의 상태를 전혀 알지 못해도 똑같은 상태의 인스턴스를 추가로 생성할 수 있다.

```java
//ex26
class Car {
    String color;
    String gearType;
    int door;

    Car() {
        this("white", "auto", 4);
    }

    Car(Car c) {
        color = c.color;
        gearType = c.gearType;
        door = c.door;
    }

    Car(String color, String gearType, int door) {
        this.color = color;
        this.gearType = gearType;
        this.door = door;
    }
}

class CarTest3 {
    public static void main(String[] args) {
        Car c1 = new Car();
        Car c2 = new Car(c1);

        System.out.println("c1의 color = " + c1.color + ", gearType = " + c1.gearType + ", door = " + c1.door);
        System.out.println("c2의 color = " + c2.color + ", gearType = " + c2.gearType + ", door = " + c2.door);

        c1.door = 100;
        System.out.println("c1.dorr = 100; 수행 후");
        System.out.println("c1의 color = " + c1.color + ", gearType = " + c1.gearType + ", door = " + c1.door);
        System.out.println("c2의 color = " + c2.color + ", gearType = " + c2.gearType + ", door = " + c2.door);
    }
}

실행결과
c1의 color = white, gearType = auto, door = 4
c2의 color = white, gearType = auto, door = 4
c1.dorr = 100; 수행 후
c1의 color = white, gearType = auto, door = 100
c2의 color = white, gearType = auto, door = 4
```

**인스턴스 생성 시 결정해야 할 2가지 사항**

1. 클래스 - 어떤 클래스의 인스턴스를 생성할 것인가?
2. 생성자 - 선택한 클래스의 어떤 생성자로 인스턴스를 생성할 것인가?

---

# 변수의 초기화

## 변수의 초기화

**변수의 초기화** : 변수를 선언하고 처음으로 값을 저장하는 것.

- 선언과 동시에 적절한 값으로 초기화 하는 것이 바람직하다.
- 멤버변수(클래스 변수와 인스턴수 변수)와 배열의 초기화는 선택적이지만, **지역변수의 초기화는 필수적이다.**
- 타입이 다른 변수는 함께 선언하거나 초기화 할 수 없다.
    
    ex) int i = 10, long j = 0;
    

**멤버변수의 초기화 방법**

1. 명시적 초기화(explicit initialization)
2. 생성자(constructor)
3. 초기화 블럭(initialization block)
    - 인스턴스 초기화 블럭 : 인스턴스 변수를 초기화 하는데 사용
    - 클래스 초기화 블럭 : 클래스 변수를 초기화 하는데 용

## 명시적 초기화(explicit initialization)

**명시적 초기화** : 변수를 선언과 동시에 초기화 하는 것

```java
class Car {
		int door = 4; // 기본형 변수의 초기화
		Engine e = new Engine(); // 참조형 변수의 초기화

		...
}
```

## 초기화 블럭(initialization block)

초기화 작업이 복잡하여 명시적 초기화만으로는 부족한 경우에 사용.

- **클래스 초기화 블럭** : 클래스 변수의 복잡한 초기화에 사용. 단순히 클래스 내에 블럭{}만들고 그 안에 코드를 작성하면 됨.
- **인스턴스 초기화 블럭** : 인스턴스 변수의 복잡한 초기화에 사용. 인스턴스 초기화 블럭 앞에 단순히 static을 덧붙이기만 하면 됨

```java
class initBlock {
		static { /* 클래스 초기화 블럭 */ }

		{ /* 인스턴스 초기화 블럭 */ }
}
```

클래스 초기화 블럭은 클래스가 메모리에 처음 로딩될 때 한번만 수행되고, 인스턴스 초기화 블럭은 생성자와 같이 인스턴스를 생성할 때 마다 수행된다.

생성자보다 인스턴스 초기화 블럭이 먼저 수행된다.

```java
{   // 인스턴스 초기화 블럭
		count++;
		serialNo = count;
}

Car() {
			color = "white";
			gearType = "auto";
}

Car(String color, String gearType, int door) {
			this.color = color;
			this.gearType = gearType;
}
```

클래스의 모든 생성자에 공통으로 수행되어야 하는 문장들이 있을 때, 인스턴스 블럭에 넣어주면 코드가 간결해진다.

코드의 중복을 제거하는 것은 코드의 신뢰성을 높여 주고, 오류의 발생 가능성을 줄여 준다.

```java
//ex27
class BlockTest {
    static {
        System.out.println("static  { } ");
    }

    {
        System.out.println("{ }");
    }

    public BlockTest() {
        System.out.println("생성자");
    }

    public static void main(String[] args) {
        System.out.println("BlockTest bt = new BlockTest(); ");
        BlockTest bt = new BlockTest();

        System.out.println("BlockTest bt2 = new BlockTest(); ");
        BlockTest bt2 = new BlockTest();
    }
}

실행결과
static { }
BlockTest bt = new BlockTest();
{ }
생성자
BlockTest bt2 = new BlockTest();
{ }
생성자
```

1. 실행되면서 BlockTest가 메모리에 로딩될 때, 클래스 초기화 블럭이 가장 먼저 수행되어 static { } 이 화면에 출력된다.
2. main메서드가 수행되어 BlockTest인스턴스가 생성되면서 인스턴스 초기화 블럭이 수행된다.
3. 생성자가 수행된다.

```java
//ex28
class StaticBlockTest {
    static int arr[] = new int[10];

    static {
        for (int i = 0; i < arr.length; i++)
            arr[i] = (int)(Math.random() * 10) + 1;
    }

    public static void main(String[] args) {
        for (int i = 0; i < arr.length; i++)
            System.out.println("arr[" + i + "] : " + arr[i]);
    }
}

매 실행마다 실행결과가 다름.
```

## 멤버변수의 초기화 시기와 순서

**클래스변수의 초기화 시점** : 클래스가 처음 로딩될 때 단 한번 초기화

**인스턴스변수의 초기화 시점** : 인스턴스가 생성될 때마다 각 인스턴스별로 초기화

**클래스변수의 초기화 순서** : 기본값 → 명시적 초기화 → 클래스 초기화 블럭

**인스턴스변수의 초기화 순서** : 기본값 → 명시적 초기화 → 인스턴스 초기화 블럭 → 생성자

```java
class InitTest {
			static int cv = 1;
			int iv = 1;

			static { cv = 2; }
			{ iv = 2; }
			InitTest () {
					iv = 3;
			}
}
```

1. cv가 메모리(method area)에 생성되고, cv에는 int형의 기본값인 0이 cv에 저장된다.
2. 명시적 초기화(int cv = 1)에 의해서 cv에 1이 저장된다.
3. 클래스 초기화 블럭(cv = 2)가 수행되어 cv에는 2가 저장된다.
4. InitTest클래스의 인스턴스가 생성되면서 iv가 메모리(heap)에 존재하게 되고, iv 역시 int형의 기본값인 0이 저장된다.
5. 명시적 초기화에 의해서 iv에 1이 저장된다.
6. 인스턴스 초기화 블럭이 수행되어 iv에 2가 저장된다.
7. 생성자가 수행되어 iv에는 3이 저장된다. 

```java
//ex29
class Product {
    static int count = 0;
    int serialNo;

    {
        ++count;
        serialNo = count;
    }

    public Product() {} // 생략 가능
}

class ProductTest {
    public static void main(String[] args) {
        Product p1 = new Product();
        Product p2 = new Product();
        Product p3 = new Product();

        System.out.println("p1의 제품번호(serial no)는 " + p1.serialNo);
        System.out.println("p2의 제품번호(serial no)는 " + p2.serialNo);
        System.out.println("p3의 제품번호(serial no)는 " + p3.serialNo);
        System.out.println("생성된 제품의 수는 모두 " + Product.count + "개 입니다.");
    }
}

실행결과
p1의 제품번호(serial no)는 1
p2의 제품번호(serial no)는 2
p3의 제품번호(serial no)는 3
생성된 제품의 수는 모두 3개 입니다.
```

```java
//ex30
class Document {
    static int count = 0;
    String name;

    Document() {
        this("제목없음" + ++count);
    }

    Document(String name) {
        this.name = name;
        System.out.println("문서 " + this.name + "가 생성되었습니다.");
    }
}

class DocumentTest {
    public static void main(String[] args) {
        Document d1 = new Document();
        Document d2 = new Document("자바.txt");
        Document d3 = new Document();
        Document d4 = new Document();
    }
}

실행결과
문서 제목없음1이 생성되었습니다.
문서 자바.txt가 생성되었습니다.
문서 제목없음2가 생성되었습니다.
문서 제목없음3가 생성되었습니다.
```
