# 상속

TypeScript는 ES6에서와 마찬가지로 **클래스 상속에 `extends` 키워드를 사용**합니다. 그리고 아래 코드와 같은 방법으로 수퍼 클래스 Book의 `paper_type` 속성을 다른 값으로 덮어쓸 수 있습니다. \(ES6에서는 지원하지 않습니다\)

```typescript
// Book 수퍼 클래스를 상속 받은 E_Book 클래스
class E_Book extends Book {
  // paper_type 오버라이딩
  paper_type = '스크린';
}
```

컴파일된 JavaScript\(ES5\) 코드를 살펴보면 상속을 위해 별도의 `__extends` 유틸리티 함수가 생성된 것을 확인할 수 있습니다. 상속은 ES6부터 지원하기 때문에 ES5로 컴파일된 코드에서는 상속을 처리해주는 함수가 필요한 것입니다.

**컴파일 코드:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
// 상속 유틸리티 함수
var __extends = (this && this.__extends) || (function () {
    var extendStatics = Object.setPrototypeOf ||
        ({ __proto__: [] } instanceof Array && function (d, b) { d.__proto__ = b; }) ||
        function (d, b) { for (var p in b) if (b.hasOwnProperty(p)) d[p] = b[p]; };
    return function (d, b) {
        extendStatics(d, b);
        function __() { this.constructor = d; }
        d.prototype = b === null ? Object.create(b) : (__.prototype = b.prototype, new __());
    };
})();

// E_Book 클래스
var E_Book = /** @class */ (function (_super) {
    __extends(E_Book, _super); // 수퍼 클래스 상속
    function E_Book() {
        var _this = _super !== null && _super.apply(this, arguments) || this;
        _this.paper_type = '스크린'; // 오버라이팅(덮어쓰기)
        return _this;
    }
    return E_Book;
}(Book));
```
{% endcode-tabs-item %}
{% endcode-tabs %}

하지만 `private` 접근 제어자에 의해 서브 클래스에서 접근 불가능한 속성을 덮어쓸 수는 없습니다. `manufacturing_plant` 속성을 E\_Book 클래스 내부에 설정하려 하면 다음과 같은 오류 메시지가 출력됩니다.

```typescript
// [오류]
// [ts]
// 'E_Book' 클래스가 기본 클래스 'Book'을(를) 잘못 확장합니다.
//   'manufacturing_plant' 속성은 'Book' 형식에서 private 이지만
//   'E_Book' 형식에서는 그렇지 않습니다.
// class E_Book
class E_Book extends Book {
  paper_type = '스크린';

  // [오류]
  _manufacturing_plant = '출판사 웹서버';

}
```

## 상속 / constructor, super

일반적으로 수퍼 클래스를 상속받은 **서브 클래스는 수퍼 클래스의 기능에 더하여 좀 더 많은 기능을 갖도록 설계**합니다. `constructor()`를 사용해 상속 받은 수퍼 클래스의 생성자를 서브 클래스의 생성자로 덮어쓸 수 있습니다. 이 때 반드시 **`super()`를 사용해 수퍼 클래스의 생성자에 요구되는 인자를 전달**해야 합니다.

```typescript
class E_Book extends Book {
  paper_type = '스크린';
  constructor(
    title:string, 
    author:string, 
    pages:number, 
    public is_downloadable:boolean
  ){
    // 수퍼 클래스 constructor를 덮어쓰기 위해서는 super() 실행이 필요합니다.
    super(title, author, pages);
    this.is_downloadable = is_downloadable;
  }
}
```

{% hint style="warning" %}
super\(\)를 사용하지 않을 경우, 다음과 같은 오류가 발생합니다. 

> \[오류\] \[ts\]   
> 파생 클래스의 생성자는 'super' 호출을 포함해야 합니다. constructor E\_Book\(title: string, author: string, pages: number, is\_downloadable: boolean\): E\_Book
{% endhint %}

수퍼 클래스의 `protected` 속성은 서브 클래스에서 접근 가능한 반면, `private`속성은 접근이 불가능합니다.

```typescript
class E_Book extends Book {

  constructor(
    title:string, 
    author:string, 
    pages:number, 
    public is_downloadable:boolean
  ){

    super(title, author, pages);
    this.is_downloadable = is_downloadable;

    // 수퍼 클래스의 protected 속성은 접근 가능
    console.log(this.paper_type);

    // 수퍼 클래스의 private 속성은 접근 불가능
    // [오류]
    // [ts] '_manufacturing_plant' 속성은 private이며 'Book' 클래스 내에서만 액세스할 수 있습니다.
    // (property) Book._manufacturing_plant: string
    console.log(this._manufacturing_plant);

  }

}
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-inheritance?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"type\":\"rich\",\"title\":\"ts-inheritance - StackBlitz\",\"description\":\"TypeScript : 클래스 상속\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-inheritance?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-inheritance?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=0&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/classes.html\#inheritance\",\"type\":\"link\",\"title\":\"Classes · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 상속\"}" %}

