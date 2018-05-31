### Imports

#### 방법 3. 임포트 활용

네임스페이스 임포트(`/// <reference path="<file.ts>" />`) 구문을 사용해 `app.ts` 파일에서 네임스페이스 파일들을 불러오도록 설정할 수 있습니다.

```ts
// app.ts

/// <reference path="./Dom/selectors.ts" />
/// <reference path="./Dom/events.ts" />

let body = Dom.el('body');

Dom.on(body, 'click', function(e) {
  this.classList.toggle('clicked');
});
```

`tsc` 명령을 사용해 `app.ts` 파일을 번들링하여 `dist/app.js`로 내보냅니다. 명령 구문은 다음과 같습니다.

```sh
$ tsc app.ts --outFile dist/app.js
```

JavaScript로 컴파일된 코드를 확인하면 나눠진 모든 파일이 `app.js`로 병합된 것을 확인할 수 있습니다.

컴파일 코드:

```js
// JavaScript

var Dom;
(function (Dom) {
  var document = window.document;
  function el(selector, context) {
    if (context === void 0) { context = document; }
    return context.querySelector(selector);
  }
  Dom.el = el;
  function els(selector, context) {
    if (context === void 0) { context = document; }
    return context.querySelectorAll(selector);
  }
  Dom.els = els;
})(Dom || (Dom = {}));

var Dom;
(function (Dom) {
  Dom.version = '0.0.2';
  function on(el, type, handler, is_capture) {
      if (is_capture === void 0) { is_capture = false; }
      el.addEventListener(type, handler, is_capture);
  }
  Dom.on = on;
  function off(el, type, handler, is_capture) {
      if (is_capture === void 0) { is_capture = false; }
      el.removeEventListener(type, handler, is_capture);
  }
  Dom.off = off;
})(Dom || (Dom = {}));

/// <reference path="./Dom/selectors.ts" />
/// <reference path="./Dom/events.ts" />
var body = Dom.el('body');
Dom.on(body, 'click', function (e) {
  this.classList.toggle('clicked');
});
```