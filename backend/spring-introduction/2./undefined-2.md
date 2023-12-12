# 변수 선언과 초기화

#### 변수 선언

변수를 선언하면 컴퓨터의 메모리 공간을 확보해서 그곳에 데이터를 저장할 수 있다. 그리고 변수의 이름을 통해서 해당 메모리 공간에 접근하는 것이다.



변수는 다음과 같이 하나씩 선언할 수도 있고, 한번에 여러 변수를 선언할 수 있다.

```java
package variable;

public class Var4 {
    public static void main(String[] args) {
        int a;
        int b;

        int c, d;
    }
}
```



#### 변수 초기화

변수를 선언하고, 선언한 변수에 처음으로 값을 저장하는 것을 변수 초기화라고 한다.

```java
package variable;

public class Var5 {
    public static void main(String[] args) {
        int a;
        a = 10;
        
        int b = 10;
    }
}
```

* a는 선언과 초기화를 각각 따로 한 것이다.
* b는 선언과 초기화를 한번에 한 것이다.



#### 변수는 초기화를 해야한다.

```java
package variable;

public class Var6 {
    public static void main(String[] args) {
        int a;
        System.out.println(a);
    }
}
```

초기값을 지정하지 않고 접근하게 된다면 에러가 발생하게 된다.

{% hint style="warning" %}
java: variable a might not have been initialized
{% endhint %}

해석하자면 변수가 초기화되지 않았다는 오류이다.

왜 이러한 오류가 발생할까?

컴퓨터에서 메모리는 여러 시스템이 함께 사용하는 공간이다. 그래서 어떠한 값들이 계속 저장된다. 변수를 선언하면 메모리상의 어떤 공간을 차지하고 사용한다. 그런데 그 공간에 기존에 어떤 값이 있었는지 아무도 모른다.&#x20;

따라서 변수를 초기화하지 않으면 이상한 값이 출력될 수 있다. 이러한 문제를 해결하기 위해 자바는 변수를 초기화하도록 강제한다.

{% hint style="info" %}
javascript는 초기화를 하지 않으면 undefined 값으로 초기화 된다.
{% endhint %}

#### 컴파일 에러

컴파일 에러는 자바 문법에 맞지 않았을 때 발생하는 에러이다. 컴파일 에러는 오류를 빨리 그리고 명확하게 찾을 수 있기 때문에 좋은 정보를 알려주는 에러이다. 덕분에 빠르게 버그를 찾아서 고칠 수 있다.

인텔리제이에서는 이러한 컴파일에러를 아주 자세하게 알려준다.

어디 파일에서, 어느 줄에서, 몇번째 칸?에서 에러가 발생했는지 알려준다.



