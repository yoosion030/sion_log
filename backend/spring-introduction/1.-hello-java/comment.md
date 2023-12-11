# 주석(comment)

특정 코드의 실행을 막거나 코드의 설명을 적을때 사용한다.

자바는 주석이 있는 곳을 무시하기 때문이다.

{% hint style="info" %}
java 프로젝트 생성 후 public static void main 뭐시기 일일히 작성하기 귀찮을때는 psvm을 입력 후 enter를 누르면 자동으로 생성된다!
{% endhint %}

#### 주석의 종류

*   한 줄 주석

    * `//` 을 통해 주석을 나타낸다.

    ```java
    public class CommentJava {
        public static void main(String[] args) {
            System.out.println("hello java 1"); // hello java1을 출력합니다.
        }
    }
    ```
*   여러 줄 주석

    * `/*  */` 을 통해 주석을 나타낸다.
    * `/*`로 시작하고  `*/ 로` 끝나는 범위 내에서 코드의 실행을 무시한다.



    ```java
    public class CommentJava {
        public static void main(String[] args) {
            System.out.println("hello java 1"); // hello java1을 출력합니다.
            System.out.println("hello java 2");

            /*
            System.out.println("hello java 3");
            System.out.println("hello java 4");
             */
        }
    }
    ```

{% hint style="info" %}
콘솔창을 찍는 System.out.println 마찬가지로 sout을 입력 후 enter를 누르면 자동으로 생성된다
{% endhint %}
