# 생성자 (constructor)

생성자 :  클래스의 인스턴스를 초기화하는 특별한 메서드
객체를 생성할 떄 호출
주로 객체의 멤버 변수를 초기화하고 객체의 초기 상태를 설정하는 데 사용된다.

1. 생성자의 특징  
   - 생성자는 클래스의 인스턴스를 초기화하는 데 사용됩니다.  
   - 생성자는 객체를 생성할 때 자동으로 호출됩니다.  
   - 생성자는 클래스 이름과 동일한 이름을 가지고 있습니다.  
   - 생성자는 반환 값이 없고, 반환 타입을 선언하지 않습니다.  
   - 클래스에 생성자를 명시적으로 선언하지 않으면 컴파일러가 기본 생성자를 자동으로 생성합니다.  
  
2. 생성자의 사용 방법  
   - 생성자는 new 키워드와 함께 사용하여 객체를 생성할 때 호출됩니다.  
   - 생성자를 호출할 때는 클래스 이름 다음에 괄호를 사용합니다.  
   - 생성자를 오버로딩(여러 개의 생성자를 선언)하여 다양한 초기화 방법을 제공할 수 있습니다.

```java
public class Person {
	private String name;
	private int age;

	// 매개변수가 없는 디폴트 생성자 - name, age 초기화
	public Person() {
		name = "Unknown";
		age = 0;
	}

	// 이름과 나이를 받는 생성자 - 전달된 값을 사용하여 초기화
	public Person(String name, int age) {
		this.name = name;
		this.age = age;
	}

	// Getter 및 Setter 메서드 생략

	public static void main(String[] args) {
		Person person1 = new Person();
		System.out.println(person1.getName());
		System.out.println(person1.getAge());
	
	}
}

```

디폴트 생성자는 name과 age를 초기화하고, 매개변수를 받는 생성자는 전달된 값을 사용하여 초기화합니다.


```java
class Child extends Parent {
	private int childData; 
	
	public Child(int parentData, int childData) {
		super(parentData); // 부모 클래스의 생성자 호출
		this.childData = childData;
		System.out.println("Child constructor");
	} 
}

public class Main {
	public static void main(String[] args) {
		Child child = new Child(10, 20);
	}
}
```

 Child 클래스의 생성자에서 super(parentData)를 호출하여 Parent 클래스의 생성자를 호출하고 있습니다. 이렇게 하면 Parent 클래스의 생성자가 먼저 실행되고, 그 후에 Child 클래스의 생성자가 실행됩니다.
 
※ 클래스를 정의할 때 생성자를 명시적으로 정의하지 않으면, 컴파일러는 디폴트 생성자를 자동으로 생성합니다. 디폴트 생성자는 매개변수 없이 객체를 초기화하는 역할을 합니다.


# 자바에서는 명시적인 소멸자(Destructor)를 정의할 필요가 없다.

소멸자는 객체가 메모리에서 해제되기 전에 호출되는 메서드이다. 자바에서는 명시적인 디스트럭터 개념이 없으며, 메모리 관리는 가비지 컬렉터(Garbage Collector)가 처리한다. 메모리 누수와 같은 문제를 방지할 수 있다.

