# 변수 값 변경

```java
package variable;

public class Var3 {
    public static void main(String[] args) {
        int a; // 변수 선언
        a = 10; // 변수 초기화
        System.out.println(a);
        a = 50; // 변수 값 변경
        System.out.println(a);
    }
}
```

#### 실행 결과

```
10 
50
```

변수의 값이 변경된 이후에는 10 대신에 50이 출력된다.



#### 변수 값 변경

프로그램은 한 줄씩 순서대로 실행된다.&#x20;

출력문 실행 후 50으로 변경했으니 10은 삭제되고 50이 출력되는 것이다.

