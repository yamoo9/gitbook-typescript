## Namespaces

JavaScript(ES)에는 네임스페이스를 공식적으로 지원하지 않지만, TypeScript를 사용하면 네임스페이스를 활용할 수 있습니다.
네임스페이스를 사용하는 기본 작성 방법은 다음과 같습니다.

```js
// 네임스페이스 Dom 정의
namespace Dom {

  // 외부에서 접근 불가
  const document = window.document;

  // 외부에서 접근 가능하도록 export
  export function el(selector:string, context:HTMLElement|Document = document) {
    return context.querySelector(selector);
  }

  // 외부에서 접근 가능하도록 export
  export function els(selector:string, context:HTMLElement|Document = document) {
    return context.querySelectorAll(selector);
  }

  // export 하지 않은 네임스페이스 내부에 정의된 함수는 외부에서 접근 불가
  function each(list:any[], callback:(item:any, index:number, list:any[])=>void): void {
    list.forEach(callback);
  }

}

// [오류]
// [ts] 'el' 이름을 찾을 수 없습니다.
// any
console.log(el('body')); // 오류

// [오류]
// [ts] 'typeof Dom' 형식에 'each' 속성이 없습니다.
// any
Dom.each([1, 4, 9], (item, index) => console.log(index, item));

// 네임스페이스 Dom을 통해서만 정의된 el()에 접근 사용 가능합니다.
console.log(Dom.el('body')); // <body>
```

JavaScript(ES5)로 컴파일 된 코드를 살펴보면 IIFE 패턴을 사용해 외부와 차단된 공간을 만든 후, `Dom` 객체를 네임스페이스처럼 활용합니다. 이 방법은 네임스페이스를 지원하지 않는 JavaScript 개발자들이 오래 전부터 사용하던 방법 중 하나입니다.

컴파일 코드:

```js
// JavaScript

// 네임스페이스 Dom 정의
var Dom;
(function (Dom) {
  // 외부에서 접근 불가
  var document = window.document;
  // 외부에서 접근 가능하도록 export
  function el(selector, context) {
    if (context === void 0) { context = document; }
    return context.querySelector(selector);
  }
  Dom.el = el;
  // 외부에서 접근 가능하도록 export
  function els(selector, context) {
    if (context === void 0) { context = document; }
    return context.querySelectorAll(selector);
  }
  Dom.els = els;
  // export 하지 않은 네임스페이스 내부에 정의된 함수는 외부에서 접근 불가
  function each(list, callback) {
    list.forEach(callback);
  }
})(Dom || (Dom = {}));
```