# 매개변수(Parameter)와 전달인자(Argument)

## 매개변수(parameter)

매개변수란 서로 종속인 변수들을 묶어주는 변수를 말한다. 프로그래밍에서는 함수에 투입되는 '변수'를 의미하는데, 함수를 정의할 때 초기값이 정해지는 것이다.

```java
public class Main {
	public static int subtract(int a, int b) {
		return a - b;
	}
	
	public static void main(String[] args) {
		System.out.println(subtract(7,3));
	}
}
```

2개의 정수를 빼서 차를 계산하려면 int a와 int b라는 매개변수가 있어야 한다. a와 b는 subtract 메서드 안에서 쓰인다.

매개변수가 여러 개 있을 수도 있지만 하나도 없을 수도 있다.


## 전달인자(Argument)

함수를 호출하는 부분에서 값에 해당하는 부분이 함수의 전달인자가 된다. 함수를 호출할 때마다 값이 바뀐다. 파라미터에 전달해주는 값이다.

```java
public class Main {
	public static int subtract(int a, int b) {
		return a - b;
	}
	
	public static void main(String[] args) {
		System.out.println(subtract(7,3));
	}
}
```

함수를 호출할 때 전달되는 값인 7와 3을 전달인자라고 한다.