## Class

ES6부터 클래스[^1] 문법을 사용할 수 있습니다. 클래스를 정의하고, 속성을 설정하는 기본 사용법은 다음과 같습니다.

```js
/* 클래스 */
class Book {

  /* 생성자 */
  constructor(title, author, pages) {
    this.title  = title;
    this.author = author;
    this.pages  = pages;
  }

}

/* 인스턴스 생성 ------------------------------------------------ */

let indRevo = new Book('한 권으로 정리하는 4차 산업혁명', '최진기', 367);
console.log(indRevo); // Book {}
```

<br>

---

##### 각주

[^1]: 객체 지향 프로그래밍(OOP)에서 특정 객체(인스턴스)를 생성하기 위해 변수와 메소드를 정의하는 일종의 틀을 말합니다. 객체를 정의하기 위한 상태(멤버변수)와 메서드(함수)로 구성됩니다. [Wiki 참고](https://goo.gl/A8JzG8)