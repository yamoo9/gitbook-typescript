# 네임스페이스 멀티 파일

## 네임스페이스 멀티 파일 관리 {#manage-namespace-multi}

네임스페이스 코드를 단 하나의 파일에서 관리할 필요는 없습니다. 예를 들어 `events.ts`, `selectors.ts`로 나뉘어 개발된 파일이 2개 있다고 가정 해봅니다. 각각의 코드는 다음과 같이 작성되어 있습니다.

{% code-tabs %}
{% code-tabs-item title="Dom/events.ts" %}
```typescript
namespace Dom {

  export let version:string = '0.0.2';

  export function on(
    el         : Element|Document,
    type       : string,
    handler    : (e:Event)=>void,
    is_capture : boolean = false
  ):void {
    el.addEventListener(type, handler, is_capture);
  }

  export function off(
    el         : Element|Document,
    type       : string,
    handler    : (e:Event)=>void,
    is_capture : boolean = false
  ):void {
    el.removeEventListener(type, handler, is_capture);
  }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Dom/selectors.ts" %}
```typescript
namespace Dom {

  const document = window.document;

  export function el(
    selector:string, 
    context:Element|Document = document
  ): Element {
    return context.querySelector(selector);
  }

  export function els(
    selector:string, 
    context:Element|Document = document
  ): NodeList {
    return context.querySelectorAll(selector);
  }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

그리고 네임스페이스 Dom을 활용하려는 코드를 가진 `app.ts` 파일이 있다고 합시다. 하지만 아래 작성된 코드는 네임스페이스를 호출하지 않아 오류가 발생합니다.

{% code-tabs %}
{% code-tabs-item title="app.ts" %}
```typescript
let body = Dom.el('body');

Dom.on(body, 'click', function(e) {
  this.classList.toggle('clicked');
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 방법 1. 컴파일 된 파일 로드 {#method-1}

컴파일 된 JavaScript 파일들을 `app.js` 보다 먼저 호출하면 `app.js` 코드가 정상 작동합니다. 분명 잘 작동하지만 문제가 있습니다. **나눠진 파일 개수가 많아질수록 서버에 요청\(Request\)하는 횟수가 증가하게 되어 성능에 악영향**을 미칩니다.

```markup
<head>
  <style> body { min-height: 100vh; } </style>

  <!-- 네임스페이스 파일 로드 -->
  <script src="./Dom/selectors.js">
  <script src="./Dom/events.js">
  
  <!-- 앱 파일 로드 -->
  <script async defer src="./app.js">

</head>
```

### 방법 2. 파일 번들링 {#method-2}

**`Dom` 디렉토리 내부에 있는 네임스페이스 파일들을 병합**한 후, **`dist` 디렉토리 안에 `Dom.js`를 생성**합니다.   
\(`app.js`는 별도로 개발자가 작성하는 파일로 네임스페이스 파일들과 병합하지 않습니다\)

```python
# tsc --outFile <생성할 파일.js> [<namespace 파일 1>, <namespace 파일 1>, ...]
$ tsc --outFile dist/Dom.js Dom/selector.ts Dom/events.ts
```

나뉘어진 파일들이 많을 경우 아래와 같은 구문으로 작성해도 됩니다.

```bash
$ tsc --outFile dist/Dom.js Dom/*
```

컴파일된 JavaScript 파일 코드를 살펴보면 나눠졌던 네임스페이스 코드가 하나로 병합된 결과를 볼 수 있습니다.

**컴파일 파일:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
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
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 방법 3. 임포트 활용 {#method-3}

네임스페이스 임포트\(**`/// <reference path="<file.ts>" />`**\) 구문을 사용해 `app.ts` 파일에서 네임스페이스 파일들을 불러오도록 설정할 수 있습니다.

{% code-tabs %}
{% code-tabs-item title="app.ts" %}
```typescript
/// <reference path="./Dom/selectors.ts" />
/// <reference path="./Dom/events.ts" />

let body = Dom.el('body');

Dom.on(body, 'click', function(e) {
  this.classList.toggle('clicked');
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

`tsc` 명령을 사용해 `app.ts` 파일을 번들링하여 `dist/app.js`로 내보냅니다. 명령 구문은 다음과 같습니다.

```python
$ tsc app.ts --outFile dist/app.js
```

JavaScript로 컴파일된 코드를 확인하면 나눠진 모든 파일이 `app.js`로 병합된 것을 확인할 수 있습니다.

**컴파일 코드:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
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
{% endcode-tabs-item %}
{% endcode-tabs %}

## 실습 {#practice}

{% file src="../.gitbook/assets/dom.zip" caption="네임스페이스 멀티 파일 실습자료" %}

![](../.gitbook/assets/image%20%2812%29.png)

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/namespaces.html\#multi-file-namespaces\",\"type\":\"link\",\"title\":\"Namespaces · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 네임스페이스 멀티 파일\"}" %}

