# 자바 프로그램 실행

```java
public class HelloJava {
    public static void main(String[] args) {
        System.out.println("hello java");
    }
}
```

#### 코드 설명

**public class HelloJava:**

* HelloJava는 클래스이다. 클래스의 개념은 조금 복잡하기 때문에 지금은 넘어간다.
* 지금은 단순히 `HelloJava.java`라는 파일을 만들었다고 이해하면된다.
* 파일명과 클래스는 이름이 같아야 한다.
* `{ }` 블록을 사용해서 클래스의 시작과 끝을 나타낸다.

```
public static void main(String[] args)
```

**public static void main(String\[] args):**

* main은 메서드라고 한다.
* 지금은 단순히 main은 프로그램의 시작점이라고 이해하면 된다.
* `{ }` 블록을 사용해서 메서드의 시작과 끝을 나타낸다.

**System.out.println("hello java"):**

* 콘솔에 메세지를 출력하는 문법이다.
* `( )` 소괄호 안에 넘겨온 문자를 출력한다.
* 자바는 실행 코드의 끝마다 세미콜론을 작성해야 한다.



#### 실행 순서

1. mac은 `control + shift + R` 단축어를 이용해 코드를 실행할 수 있따.
2. java의 시작지점인 main을 찾는다.
3. Systme.out.println을 실행한다.
4. 인자로 넘어온 문자열을 콘솔창에 출력한다.
5. 코드는 위에서부터 아래로(순서대로) 실행한다.





#### 코드 작성 관례

* 들여쓰기를 구분해야 가독성이 좋다.

```
public class HelloJava {
    public static void main(String[] args) {
        System.out.println("hello java");
    }
}
```

```
public class HelloJava {
public static void main(String[] args) {
System.out.println("hello java");
}
}
```

* 자바에서는 끝에 세미콜론이 필수이다. 세미콜론이 없다면 에러가 발생한다.

