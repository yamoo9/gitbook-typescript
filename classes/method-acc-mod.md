# 메서드 with 접근 제어자

속성과 마찬가지로 메서드 또한 접근 제어자를 사용해 외부에서의 접근을 제어할 수 있습니다.

```typescript
class Book {

  public    title:string;
  public    author:string;
  public    pages:number = 150;
  private   _manufacturing_plant:string = '충무로 공장';
  protected paper_type:string = '밍크지';

  constructor(title:string, author:string, pages:number) {
    this.title  = title;
    this.author = author;
    this.pages  = pages;
  }

  /* 메서드 ------------------------------------------------ */

  // public 메서드
  // 클래스 외부에서 접근 가능
  public printPages(): string {
    return `${this.pages}페이지`;
  }

  // protected 메서드
  // Book 클래스를 포함한 서브 클래스에서만 접근 가능
  protected changePaperType(type:string): void {
    this.paper_type = type;
  }

  // private 메서드
  // Book 클래스 내부에서만 접근 가능
  private setManufacturingPlant(plant:string): void {
    this._manufacturing_plant = plant;
  }


  /* 클래스 내부 메서드에서 private, protected 메서드 접근 가능 */

  public setPaperType(type:string):void {
    // protected 메서드 접근 가능
    this.changePaperType(type);
    console.log(this.paper_type);
  }

  public setPlant(plant:string):void {
    // private 메서드 접근 가능
    this.setManufacturingPlant(plant);
    console.log(this._manufacturing_plant);
  }

}


/* 인스턴스 생성 ------------------------------------------------ */

let indRevo = new Book('한 권으로 정리하는 4차 산업혁명', '최진기', 367);

console.log(indRevo.printPages()); // '367페이지'

// [오류]
// [ts] 'changePaperType' 속성은 보호된 속성이며
// 'Book' 클래스 및 해당 하위 클래스 내에서만 액세스할 수 있습니다.
// (method) Book.changePaperType(type: string): void
console.log(indRevo.changePaperType('인디언지'));

// [오류]
// [ts] 'setManufacturingPlant' 속성은 private이며
// 'Book' 클래스 내에서만 액세스할 수 있습니다.
// (method) Book.setManufacturingPlant(plant: string): void
console.log(indRevo.setManufacturingPlant('파주 공장'));
```

## 주의!

TypeScript 상에서는 접근 제어자에 따라 접근 또는 차단을 제어할 수 있지만, 컴파일된 JavaScript 코드에서는 그렇지 않습니다. JavaScript\(ES5\)는 언어 차원에서 접근 제어자를 지원하지 않기 때문입니다. 즉, 컴파일된 Book 클래스의 메서드는 모두 접근 가능합니다.

컴파일 코드:

```javascript
// JavaScript

var Book = /** @class */ (function () {

  function Book(title, author, pages) {
    this.pages = 150;
    this._manufacturing_plant = '충무로 공장';
    this.paper_type = '밍크지';
    this.title = title;
    this.author = author;
    this.pages = pages;
  }

  /* 메서드 ------------------------------------------------ */

  Book.prototype.printPages = function () {
    return this.pages + "\uD398\uC774\uC9C0";
  };

  Book.prototype.changePaperType = function (type) {
    this.paper_type = type;
  };

  Book.prototype.setManufacturingPlant = function (plant) {
    this._manufacturing_plant = plant;
  };

  Book.prototype.setPaperType = function (type) {
    this.changePaperType(type);
    console.log(this.paper_type);
  };
  Book.prototype.setPlant = function (plant) {
    this.setManufacturingPlant(plant);
    console.log(this._manufacturing_plant);
  };

  return Book;

}());

/* 인스턴스 생성 ------------------------------------------------ */

var indRevo = new Book('한 권으로 정리하는 4차 산업혁명', '최진기', 367);
console.log(indRevo.printPages()); // '367페이지'
console.log(indRevo.changePaperType('인디언지'));
console.log(indRevo.setManufacturingPlant('파주 공장'));
```

