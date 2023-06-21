# Lambda
## 람다식이란

>   메서드를 하나의 식(expression)으로 표현한 것

- 메서드를 람다식으로 표현하면 메서드의 이름과 반환값이 없어지므로, 람다식을 '익명함수(anonymous function)'이라고도 한다.

```java
int[] arr = new int[5];
Arrays.setAll(arr, (i) -> (int)(Math.random()*5)+1);
```
위 람다식이 하는 일을 메서드로 표현한다면 다음과 같다.

```java
int method() {
	return (int)(Math.random()*5)+1;
```

- 메서드보다 람다식이 간결하다는 것을 알 수 있다. 람다식 자체만으로 메서드의 역할을 대신할 수 있다.

## 람다식 작성하기

람다식은 메서드에서 이름과 반환타입을 제거하고 매개변수 선언부와 몸통{} 사이에 '->'을 추가한다.

==<변환 전>==
```java
반환타입 메서드이름(매개변수 선언) {
	문장들
}
```

==<변환 후>==
```java
				(매개변수 선언) -> { 
	문장들
}
```

## 함수형 인터페이스(Functional Interface)

> 단 하나의 추상 메서드만 선언된 인터페이스

- 왜?
하나의 추상 메서드만 정의되어야 람다식과 인터페이스의 메서드가 		1:1로 연결될 수 있기 때문이다.

####  Q. 람다식으로 정의된 익명 객체의 메서드를 어떻게 호출할 수 있을까?
참조변수가 있어야 객체의 메서드를 호출할 수 있다.

```java
타입 f = (int a, int b)  -> a > b ? a : b;
```

참조변수 f의 타입은 참조형이므로 클래스 또는 인터페이스가 가능하다. 
하나의 메서드가 선언된 인터페이스를 정의해서 람다식을 다루는 것은 자연스럽다. 그래서 인터페이스를 통해 람다식을 다루기로 결정되었으며, 람다식을 다루기 위한 인터페이스를 '함수형 인터페이스(Functional Interface)'라고 부르기로 했다.

```java
@FunctionalInterface
interface MyFunction {
	public abstract int max(int a, int b);
}
```
람다식은 익명 객체이므로 타입을 알 수 없다. 따라서 타입을 일치시켜야할 때 형변환이 필요하다.

### 자주 쓰이는 함수형 인터페이스
 
 - java.lang.Runnable
 - Supplier<T>
 - Consumer<T>
 - Function<T, R>
 - Predicate<T>
 

## 메서드 참조(Method Reference)
하나의 메서드만 호출하는 람다식은 '메서드 참조(method reference)'로 더 간략히 표현할 수 있다.
> 클래스이름 :: 메서드이름

1. static메서드참조
2. 인스턴스메서드 참조
