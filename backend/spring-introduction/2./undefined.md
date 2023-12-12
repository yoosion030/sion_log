# 변수 시작

```java
package variable;

public class Var1 {
    public static void main(String[] args) {
        System.out.println(10);
        System.out.println(10);
        System.out.println(10);
    }
}
```

#### 패키지(package)

* 패키지는 자바 파일을 구문하기 위한 폴더로 이해하면 된다.
* ex. variable이라는 패키지를 만들었다면, java 파일 첫 줄에 `package variagle;` 을 선언해주어야 한다.
* 자바 파일이 위치하는 패키지와 `package variable` 선언 위치가 같아야 한다.
* 인텔리제이에서는 해당 패키지에 맞게 선언을 자동적으로 작성해준다.

#### 변수가 존재하는 이유

```
10
10
10
```

단순히 10을 출력하는 코드에서, 10 말고 20을 출력하도록 코드를 변경해보자.

```java
System.out.println(10); // 변경
System.out.println(10); // 변경
System.out.println(10); // 변경
```

똑같은 코드를 불필요하게 3번 변경을 해야한다. 만약 더 대규모 프로젝트에서 출력문이 100개라면 100번 수정을 해줘야 한다.

그래서 어딘가에 값을 보관해두고 필요할 때 값을 꺼내서 읽을 수 있는 저장소가 필요하다. 데이터를 담을 수 있는 그릇을 말한다.

모든 프로그래밍 언어는 이런 문제를 해결하기 위해 **변수**라는 기능을 제공한다.

#### 변수 사용

```java
package variable;

public class Var2 {
    public static void main(String[] args) {
        int a = 10;
        System.out.println(a);
        System.out.println(a);
        System.out.println(a);
    }
}
```

* 여기서 int는 integer로 정수를 의미한다.
* 정수라는 a를 선언하고, 10이라는 데이터를 초기화 해주었다.
* 그러고 출력문에 a를 호출하면 a를 가르키는 값인 10이 출력된다.

아까와 같이 10을 20으로 변경해야 한다면? a의 데이터 값을 10에서 20을 변경해주면 된다! 이전에는 3번 변경이 일어나지만 변수를 선언한 이후로는 변수를 한.번. 수정하기만 하면 된다.

