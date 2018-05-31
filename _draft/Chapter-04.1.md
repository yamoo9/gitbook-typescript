## TypeScript Class

### 속성 설정 (with 접근 제어자)

TypeScript의 클래스 문법은 ES6의 기능을 포함하면서 보다 강력한 기능을 제공합니다.
접근 제어자(access modifiers)[^1]통해 접근 가능한 범위를 설정할 수 있고, 각 속성에 데이터 타입을 지정할 수 있습니다.

```ts
class Book {

  // 제목
  // public: 클래스 외부에서 접근 가능
  public title:string;

  // 저자
  // public은 기본 값으로 생략 가능합니다.
  author:string;

  // 제조 공장
  // private: Book 클래스 내부에서만 접근 가능
  private _manufacturing_plant:string;

  // 종이 유형
  // protected: Book 클래스를 포함한 서브 클래스에서만 접근 가능
  protected paper_type:string;

  // constructor() 매개변수 앞에
  // public, private, protected를 사용하면
  // Book 클래스의 타입(type)을 별도 선언하지 않아도 됩니다.
  constructor(title:string, author:string, public pages:number) {
    this.title = title;
    this.author = author;
    this.pages = pages;
  }

}

/* 인스턴스 생성 ------------------------------------------------ */

let indRevo = new Book('한 권으로 정리하는 4차 산업혁명', '최진기', 367);
console.log(indRevo); // Book {}
```

<br>

---

##### 각주

[^1]: 키워드 `public`, `private`, `protected` 등을 사용해 외부에서의 접근을 제어하는 것을 말합니다.