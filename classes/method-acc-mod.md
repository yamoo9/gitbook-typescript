# 메서드 with 접근 제어자

## 접근 제어 메서드 설정 {#setting-acc-mod-methods}

속성과 마찬가지로 메서드 또한 접근 제어자를 사용해 외부에서의 접근을 제어할 수 있습니다.

{% code-tabs %}
{% code-tabs-item title="TypeScript" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
TypeScript 상에서는 접근 제어자에 따라 접근 또는 차단을 제어할 수 있지만, 컴파일된 JavaScript 코드에서는 그렇지 않습니다. JavaScript\(ES5\)는 언어 차원에서 접근 제어자를 지원하지 않기 때문입니다. 즉, 컴파일된 Book 클래스의 메서드는 모두 접근 가능합니다.
{% endhint %}

**컴파일 코드:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
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
{% endcode-tabs-item %}
{% endcode-tabs %}

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-access-modifiers-methods?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"type\":\"rich\",\"title\":\"ts-access-modifiers-methods - StackBlitz\",\"description\":\"TypeScript : 클래스 속성 접근 제어자\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-access-modifiers-methods?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-access-modifiers-methods?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=0&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/classes.html\#public-private-and-protected-modifiers\",\"type\":\"link\",\"title\":\"Classes · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript 클래스 접근 제어자\"}" %}

