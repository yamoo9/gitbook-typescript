# 클래스

ES6부터 클래스 문법을 사용할 수 있습니다. 클래스를 정의하고, 속성을 설정하는 기본 사용법은 다음과 같습니다.

```javascript
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

## 각주

