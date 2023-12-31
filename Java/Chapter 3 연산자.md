# 연산자

# 연산자

**연산자** : 연산을 수행하는 기호

### 연산자와 피연산자

**연산자(operator)** : 연산을 수행하는 기호 ex) -, +, *,  / 

**피연산자(operand**) : 연산자의 작업 대상(변수, 상수, 리터럴, 수식)

```java
x + 3 // 연산자 : +, 피연산자 : x, 3
```

연산자는 피연산자로 연산을 수행하고 나면 항상 결과값을 반환한다.

### 식과 대입연산자

**식(expression)** : 연산자와 피연산자를 조합하여 계산하고자하는 바를 표현한 것

**식을 평가한다** : 식을 계산하여 결과를 얻는 것

```java
4 * x + 3; // x의 값이 5일 때 23이라는 결과가 나오지만 사용되지 않고 사라진다.

y = 4 * x + 3; // 저장할 수 있는 공간을 주어야 평가결과가 저장된다.

System.out.println(4 * x + 3); // 출력하기만을 원할 때
```

### 연산자의 종류

- 산술 연산자 : +  -  *  /  %  <<  >>    사칙 연산과 나머지 연산
- 비교 연산자 : <  >  >=  <=  ==  !=      크고 작음과 같고 다름을 비교
- 논리 연산자 : &&  ||  !  &  |  ^  ~        ‘그리고’와 ‘또는’으로 조건을 연결
- 대입 연산자 :    =      우변의 값을 좌변에 저장
- 기타 : (type)  ?:  instanceof       형변환 연산자, 삼항 연산자, instanceof연산자

### 피연산자의 개수에 의한 분류

피연산자의 개수에 따라 **n항 연산자**라고 부른다. 

대부분은 이항 연산자이고 삼항 연산자는 오직 ? : 하나 뿐이다. 

```java
-(부호 연산자)3 -(뺄셈 연산자) 5
부호 연산자는 단항 연산자
뺄셈 연산자는 이항 연산자
```

연산자의 우선순위 때문에 연산자를 기능별, 피연산자의 개수별로 나누어 분류한다.

### 연산자의 우선순위와 결합 규칙

1. 산술 > 비교 > 논리 > 대입. 대입의 우선순위가 가장 낮다.
2. 단항 > 이항 > 삼항. 단항 연산자의 우선순위가 이항 연산자보다 높다.
3. 단항 / 대입 연산자를 제외한 모든 연산의 진행방향은 왼쪽에서 오른쪽이다.
4. **단항 > 산술 > 비교 >논리 > 삼항 > 대입**

### 산술 변환

**산술 변환(일반 산술 변환)** : 연산 전에 피연산자 타입의 일치를 위해 자동으로 형변환 되는 것

**산술 변환의 규칙**

- **두 피연산자의 타입을 큰 타입으로 일치시킨다.**

피연산자의 값손실을 최소화하기 위함.

- **피연산자의 타입이 int보다 작은 타입이면 int로 변환된다.**

정수형 기본 타입인 int가 가장 효율적으로 처리할 수 있는 타입.

**연산 결과의 타입 = 피연산자의 타입**

---

# 단항 연산자

### 증감 연산자 ++ / --

증감 연산자의 피연산자로 정수, 실수는 가능하지만, 상수는 값의 변경이 불가능하므로 피연산자가 될 수 없다.

- **증가 연산자(++)** : 피연산자의 값을 1 증가시킨다.
- **감소 연산자**(--) : 피연산자의 값을 1 감소시킨다.

증감 연산자가 전위형 / 후위형에 따라 결과가 다르다.

- **전위형** : 값이 참조되기 **전에** 증가시킨다.
- **후위형** : 값이 참조된 **후에** 증가시킨다.

```java
int i = 1;
int j;
int k;

j = ++i; // j = 2

i = 1;
k = i++; // k = 1
```

```java
int i = 5, j = 5;
System.out.println(i++); // 5  출력 후에 1이 증가함.
System.out.println(++j); // 6
System.out.println("i = " + i + ", j = " + j); // i = 6, j = 6 
```

식에 두 번 이상 포함된 변수에 증감 연산자를 사용하는 것은 피해야 한다.

### 부호 연산자 + / -

부호 연산자는 boolean형 / char형을 제외한 기본형에만 사용 가능하다.

**-**는 피연산자의 부호를 반대로 변경한 결과를 반환한다.

+는 하는 일이 없어 쓰이는 경우도 거의 없다.

```java
int i = -10;
i = +i;
System.out.println(i); // -10

i = -i;
System.out.println(i); // 10
```

---

# 산술 연산자

### 사칙 연산자 +, -, *, /

***(곱셈), /(나눗셈), %(나머지) 연산자**가 +(덧셈), -(뺄셈) 연산자보다 우선순위가 높다. 

피연산자가 정수형인 경우, 나누는 수로 0을 사용할 수 없다. 0으로 실행 시 오류 발생.

```java
int a = 10;
int b = 4;

System.out.println("%d / %d = %d%n", a, b, a / b); // 10 / 4 = 2
```

두 피연산자가 모두 int타입인 경우, 연산 결과도 int타입이다. int타입은 소수점을 저장하지 못하고 정수만 남고 소수점 이하는 버려지기 때문이다. **반올림은 발생하지 않는다.**

```java
int a = 10;
int b = 4;

System.out.println("%d / %f = %f%n", a, (float)b, a / (float)b); // 10 / 2.000000 = 2.500000
```

올바른 연산 결과를 얻기 위해서는 어느 한 쪽을 실수형으로 형변환 해줘야 한다. 다른 한 쪽은 실수형으로 자동 형변환되기 때문에 연산 결과도 실수형이 된다.

```java
byte a = 10;
byte b = 20;
byte c = a + b; // 오류 발생.
System.out.println(c); // 출력되지 않음.

// byte c = (byte)(a + b); 로 변경해주면 오류가 일어나지 않는다. 
```

a와 b 모두 int형보다 작은 byte형이기 때문에 int형으로 변환한 다음 연산이 수행된다. 연산 결과는 int형이기 때문에 byte형인 c에 형변환 없이 연산 결과를 저장할 수 없다.

```java
byte a = 10;
byte b = 30;
byte c = (byte)(a * b);
System.out.println(c); // 44
```

연산 결과는 300이지만, byte형의 범위를 넘기 때문에 byte형으로 변환하면 값 손실이 발생해 44가 c에 저장된다. 이러한 값 손실을 예방하기 위해선 충분히 큰 자료형을 사용해야 한다.

```java
int a = 1_000_000;
int b = 2_000_000;

long c = a * b;
System.out.println(c) // -1454759936

// long c = (long)a * b 로 변경해주면 연산 결과가 정상적으로 나온다.
```

c의 자료형은 long타입으로 연산 결과를 저장하기에 충분하지만, 쓰레기 값이 출력된다. 그 이유는  a * b의 연산 결과가 int타입이기 때문에 long형으로 변환되어도 값이 변하지 않는다. 올바른 결과를 위해선 한 쪽을 long형으로 변환해줘야 한다.

  

```java
long a = 1_000_000 * 1_000_000;
long b = 1_000_000 * 1_000_000L;

System.out.println("a = " + a); // a = -727379968
System.out.println("b = " + b); // b = 1000000000000
```

a의 자료형은 long타입으로 $10^{12}$을 저장하기에 충분하지만, 쓰레기 값이 출력됐다. 그 이유는 연산 결과는 int타입이고 int타입의 최대값을 넘어 오버플로우가 발생했기 때문이다.

b는 한 쪽이 long타입이기 때문에 연산 결과가 long타입이 되므로 오류가 발생하지 않는다.

```java
int a = 1_000_000;

int result1 = a * a / a;
int result2 = a / a * a;

System.out.println(result1); // -727
System.out.println(result2); // 1000000
```

같은 의미의 식이라도 연산의 순서에 따라 다른 결과를 얻을 수 있다.

 사칙연산의 피연산자로 문자도 가능하다. 문자는 해당 문자의 유니코드로 바뀌어 저장되므로 문자간의 사칙연산은 정수간의 연산과 동일하다.

```java
char c1 = 'a';
char c2 = c1;
char c3 = ' ';

int i = c1 + 1; // 'a' + 1 -> 97 + 1 -> 98

c3 = (char)(c1 + 1);
c2++;
c2++;

System.out.println("i = " + i); // i = 98
System.out.println("c2 = " + c2); // c2 = c
System.out.println("c3 = " + c3); // c3 = b
```

c1 + 1을 계산할 때, c1은 char형이므로 int형으로 변환 후 덧셈 연산을 한다.

```java
char c1 = 'a'

//char c2 = c1 + 1;    컴파일 에러 발생.
char c2 = 'a' + 1; // OK.

System.out.println(c2); // b
```

‘a’ + 1은 리터럴 간의 연산이기 때문에 에러가 발생하지 않는다. 상수 또는 리터럴 간의 연산은 실행 과정동안 변하는 값이 아니기 때문에, 컴파일 시에 컴파일러가 계산해서 그 결과로 대체한다.

c1 + 1과 같이 수식에 변수가 들어가 있는 경우에는 컴파일러가 미리 계산할 수 없기 때문에 형변환을 해줘야 한다.

```java
double pi = 3.141592;
double shortPi = Math.round(pi * 1000) / 1000.0;
System.out.println(shortPi); // 3.142
```

round메서드는 매개변수로 받은 값을 소수점 첫째 자리에서 반올림을 하고 그 결과를 정수로 돌려주는 메서드이다.

Math.round(pi * 1000) / 1000.0

→ Math.round(3.141592 * 1000) / 1000.0

→ Math.round(3141.592) / 1000.0

→ 3142 / 1000.0

→ 3.142

### 나머지 연산자 %

왼쪽의 피연산자를 오른쪽 피연산자로 나누고 난 나머지 값을 결과로 반환하는 연산자

나누는 수로 0을 사용할 수 없다.

```java
System.out.println(10 % 8);
System.out.println(10 % -8); // 두 코드의 결과는 같다.
```

나누는 수로 음수를 허용하지만, 부호가 무시된다.

---

# 비교 연산자

### 대소비교 연산자 <, >, <=, >=

참이면 true, 거짓이면 false를 결과로 반환한다. 

boolean형을 제외한 기본형에 사용할 수 있지만, 참조형에는 사용할 수 없다.

- **<** : 좌변 값이 작으면 true, 아니면 false
- **>** : 좌변 값이 크면 true, 아니면 false
- **<=** : 좌변 값이 작거나 같으면 true, 아니면 false
- **>=** : 좌변 값이 크거나 같으면 true, 아니면 false

### 등가비교 연산자 ==, !=

두 피연산자의 값이 같은지 또는 다른지 비교하는 연산자

대소비교 연산자와는 다르게 기본형과 참조형 모두 사용할 수 있다. 기본형의 경우 저장되어 있는 값이 같은지 알 수 있고, 참조형의 경우 같은 객체를 가리키고 있는지 알 수 있다.

기본형과 참조형은 서로 형변환이 가능하지 않기 때문에 비교할 수 없다.

- == : 두 값이 같으면 true, 아니면 false
- **!=** : 두 값이 다르면 true, 아니면 false

```java
System.out.println("%b%n", 10 == 10.0f); // true
System.out.println("%b%n", '0' == 0); // false
```

비교 연산자도 이항 연산자이므로 형변환을 통해 두 피연산자의 타입을 갖게 맞추고 비교한다.

10 == 10.0f

→ 10.0f == 10.0f

→ true

문자는 유니코드로 저장된다.

‘0’ == 0

→ 48 == 0

→ false

```java
float f = 0.1f // 0.10000000149011612
double d = 0.1 // 0.10000000000000001

System.out.println("%b%n", d == f); // false
```

10.0f는 오차없이 저장할 수 있는 값이라서 double로 형변환해도 그대로 10.0이지만, 0.1f는 저장할 때 2진수로 변환하는 과정에서 오차가 발생한다. 0.1f를 double타입으로 형변환해도 값은 전혀 달라지지 않는다. 즉, float타입의 값을 정밀도가 더 높은 double타입으로 형변환했다고 해서 오차가 적이지는 것이 아니다.

d == f 

→ d == (double)f

→ 0.10000000000000001 == (double)0.10000000149011612

→ 0.10000000000000001 == 0.10000000149011612

→ false

float타입의 값과 double타입의 값을 비교하려면 double타입의 값을 float타입으로 형변환한 다음에 비교해야 한다.

### 문자열의 비교

문자열을 비교할 때는, **equals()라는 메서드를 사용**해야 한다. equals()는 비교하는 두 문자열이 같으면 true, 다르면 false를 반환한다.

```java
String str = new String("abc"); // String str = "abc";
boolean result = str.equals("abc"); // true 저장
```

equals()는 객체가 달라도 내용이 같으면 true를 반환한다. 그래서 문자열을 비교할 때는 항상 equals()를 사용해야 한다. 대소문자의 구분 없이 비교하고 싶으면 **equalsIgnoreCase()를 사용**하면 된다.

# 논리 연산자

### 논리 연산자 &&, ||, !

- **&&(AND결합)** : 피연산자 양쪽 모두 true이어야 true를 결과로 얻는다.
- **||(OR결합)** : 피연산자 중 어느 한 쪽만 true이면 true를 결과로 얻는다.

ex)

1. x는 10보다 크고, 20보다 작다

```java
 x > 10 && x < 20
```

1. i는 2의 배수 또는 3의 배수지만 6의 배수는 아니다

```java
(i % 2 == 0 ****|| i % 3 == 0) ****&& ****i % 6 != 0
```

&&의 우선순위가 ||보다 높기 때문에 괄호를 사용해줘야 한다.

1. 문자 ch는 대문자 또는 소문자이다.

```java
('a' <= ch && ch <= 'z') || ('A' <= ch <= 'Z')
```

### 효율적인 연산(short circuit evaluation)

OR연산의 경우 피연산자 중 어느 한 쪽만 참이어도 전체 결과가 참이므로 좌측 피연산자가 true이면, 우측 피연산자의 값은 평가하지 않는다.

AND연산도 마찬가지로 어느 한 쪽만 거짓이어도 전체 결과가 거짓이므로 좌측 피연산자가 false면, 우측 피연산자의 값은 평가하지 않는다. 

같은 조건식이라도 피연산자의 위치에 따라서 연산속도가 달라질 수 있다.

### 논리 부정 연산자 !

true → false, false → true를 결과로 반환한다.

x : true  !x : false

x : false  !x : true

어떤 값에 !를 반복적으로 적용하면, 참과 거짓이 차례대로 반복된다. 이 성질을 이용하면 토글 버튼을 논리적으로 구현할 수 있다.

```java
boolean b = true;

System.out.println("%b%n", !b); // false
System.out.println("%b%n", !!b); // true
System.out.println("%b%n", !!!b); // false
```

단항연산자는 피연산자와 가까운 것부터 먼저 연산된다.

!!b

→ !!true

→ !false

→ true

### 비트 연산자 &, |, ^, ~, <<, >>

비트 연산자는 피연산자를 비트 단위로 논리 연산한다. 피연산자를 이진수로 표현했을 때 각 자리를 규칙에 따라 연산을 수행하며, 피연산자로 실수는 허용하지 않고 정수(문자 포함)만 허용된다.

- **|(OR연산자)** : 피연산자 중 한 쪽의 값이 1이면, 1을 결과로 얻는다. 그 외에는 0을 얻는다.
- **&(AND연산자)** : 피연산자 양 쪽이 모두 1이어야만 1을 결과로 얻는다. 그 외에는 0을 얻는다.
- **^(XOR연산자)** : 피연산자의 값이 서로 다를 때만 1을 결과로 얻는다. 같을 때는 0을 얻는다.

‘|’은 주로 특정 비트의 값을 변경할 때 사용한다.

ex) **0xAB | 0xF = 0xAF**

   1 0 1 0 1 0 1 1   0xAB

|) 0 0 0 0 1 1 1 1   0xF 

 ——————————

   1 0 1 0 1 1 1 1   0xAF

‘&’는 주로 특정 비트의 값을 뽑아낼 때 사용한다.

ex) **0xAB & 0xF = 0xB (마지막 4bit의 값)**

     1 0 1 0 1 0 1 1   0xAB

&) 0 0 0 0 1 1 1 1   0xF

——————————

     0 0 0 0 1 0 1 1   0xB

‘^’는 같은 값으로 두고 XOR연산을 수행하면 원래의 값으로 돌아오는 특징이 있어서 간단한 암호화에 사용된다.

ex) **0xAB ^ 0xF = 0xA4**  

     **0xA4 ^ 0xF = 0xAB**

    1 0 1 0 1 0 1 1   0xAB

^) 0 0 0 0 1 1 1 1   0xF

———————————

    1 0 1 0 0 1 0 0   0xA4

^) 0 0 0 0 1 1 1 1   0xF

———————————

    1 0 1 0 1 0 1 1   0xAB

비트 연산에서도 피연산자의 타입을 일치시키는 산술 변환이 일어날 수 있다.

### 비트 전환 연산자 ~

피연산자를 2진수로 표현했을 때, 0 → 1, 1 → 0으로 바꾼다.

x : 1    ~x : 0

x : 0    ~x : 1

비트 전환 연산자 ‘~’에 의해 비트 전환이 되면, 부호 있는 타입의 피연산자는 부호가 반대로 변경된다. 즉, **1의 보수**를 얻을 수 있는 것이다. 그래서 비트 전환 연산자를 **1의 보수 연산자**라고도 한다.

    0 0 0 0 1 0 1 0  (10진수 10)

→ 1 1 1 1 0 1 0 1  (10진수 -11)

### 쉬프트 연산자 >>, <<

피연산자의 각 자리(2진수로 표현 했을 때)를 오른쪽(>>) 또는 왼쪽(<<)으로 이동한다.

자리 이동으로 저장 범위를 벗어난 값들은 버려지고 빈자리는 0으로 채워진다.

ex) 8 << 2 = 32

    0 0 0 0 1 0 0 0

→ ~~0 0~~ 0 0 1 0 0 0 **0 0**  

>>연산자는 오른쪽으로 이동시키기 때문에 부호있는 정수는 부호를 유지하기 위해서 왼쪽 피연산자가 음수이면 빈자리를 1로 채우고, 양수이면 0으로 채운다.

ex) 

-8 >> 2 = -2

    1 1 1 1 1 0 0 0

→ **1 1** 1 1 1 1 1 0 ~~0 0~~  

8 >> 2 = 2

    0 0 0 0 1 0 0 0 

→ **0 0** 0 0 0 0 1 0 ~~0 0~~

**x << n은 * $2^n$의 결과와 같다.**

**x >> n은 / $2^n$의 결과와 같다.**

---

# 그 외의 연산자

### 조건 연산자 ? :

조건 연산자는 조건식, 식1, 식2 모두 세 개의 피연산자를 필요로 하는 삼항 연산자이며, 삼항 연산자는 조건 연산자 하나뿐이다.

                                                             **조건식 ? 식1 : 식2**

조건 연산자는 첫 번째 피연산자인 조건식의 평과 결과에 따라 다른 결과를 반환한다. 조건식의 평가 결과가 true이면 식1이, false이면 식2가 연산 결과가 된다.

ex)

x = 5, y = 3

result = (x > y) ? x : y;

→ result = (5 > 3) ? 5 : 3;

→ result = (true) ? 5 : 3;

→ result = 5;

조건 연산자는 조건문인 if문으로 바꿔 쓸 수 있으며, if문 대신 조건 연산자를 사용하면 코드를 보다 간단히 할 수 있다.

조건 연산자를 중첩해서 사용하면 셋 이상 중의 하나를 결과로 얻을 수 있다.

ex) 1, 0, -1

x = 3

result = x > 0 ? 1 : ( x == 0 ? 0 : -1);

→ result = x > 0 ? 1 : (3 == 0 ? 0 : -1);

→ result = x > 0 ? 1 : (false ? 0 : -1);

→ result = 3 > 0 ? 1 : -1;

→ result = true ? 1 : -1;

→ result = 1;

두 피연산자의 타입이 다른 경우, 이항 연산자처럼 산술 변환이 발생한다.

### 대입 연산자 =, op=

변수와 같은 저장공간에 값 또는 수식의 연산결과를 저장하는데 사용된다. 연산자는 오른쪽 피연산자의 값(식이라면 평가값)을 왼쪽 피연산자에 저장한다. 그리고 저장된 값을 연산결과로 반환한다.

```java
System.out.println(x = 3); // 변수 x에 3이 저장되고 연산결과인 3이 출력된다.
```

대입 연산자는 연산자들 중에서 가장 낮은 우선순위를 가지고 있기 때문에 제일 나중에 수행된다. 연산 진행 방향은 오른쪽에서 왼쪽이다.

### lvalue와 rvalue

대입 연산자의 왼쪽 **피연산자를 lvalue(left value)**이라 하고, **오른쪽 피연산자를 rvalue(right value)**라고 한다.

rvalue는 변수뿐만 아니라 식이나 상수 등이 모두 가능하지만 lvalue는 반드시 변수처럼 값을 변경할 수 있는 것이어야 한다. 리터럴이나 상수같이 값을 저장할 수 없는 것들은 lvalue가 될 수 없다.

```java
int i = 0;
3 = i + 3; // 에러. lvalue가 값을 저장할 수 있는 공간이 아님.
i + 3 = i; // 에러. lvalue의 연산결과는 리터럴

final int MAX = 3; 
MAX = 10; // 에러. 상수에 새로운 값을 지정할 수 없다.
```

### 복합 대입 연산자

대입 연산자는 다른 연산자(op)와 결합하여 ‘op=’와 같은 방식으로 사용될 수 있다.

ex)

- i += 3; → i = i + 3;
- i -= 3; → i = i - 3;
- i *= 3; → i = i * 3;
- i /= 3; → i = i / 3;
- i %= 3; → i = i %3;
- i <<= 3; → i = i << 3;
- i >>= 3; → i = i >> 3;
- i &= 3; → i = i & 3;
- i ^= 3; → i = i ^ 3;
- i |= 3; → i = i | 3;
- **i *= 10 + j; → i = i * (10 + j);**