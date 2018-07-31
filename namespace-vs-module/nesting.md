# 네임스페이스 중첩

## 중첩된 네임스페이스 {#namespace-nesting}

네임스페이스 내부에 네임스페이스를 선언할 수 있고 공개\(export\) 할 수도 있습니다. 즉, **중첩된\(nested\) 네임스페이스를 활용**할 수 있습니다. 작성 방법은 다음과 같습니다.

{% code-tabs %}
{% code-tabs-item title="Dom.ts" %}
```typescript
namespace Dom {

  // 중첩된 Events 네임스페이스
  export namespace Events {
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

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 중첩된 네임스페이스 별칭 {#namespace-alias}

**중첩된 네임스페이스에 접근하기 위해 코드가 길어진다면 별칭\(**[**Alias**](http://www.typescriptlang.org/docs/handbook/namespaces.html#aliases)**\)를 만들어 사용**할 수도 있습니다. 네임스페이스 별칭을 만들 때 **`import` 키워드를 사용**합니다. 아래 코드를 참고하세요.

{% code-tabs %}
{% code-tabs-item title="app.ts" %}
```typescript
/// <reference path="./Dom.ts" />

// Dom.Events 네임스페이스를 import 하여 Events 변수에 참조
import Events = Dom.Events;

let body = Dom.el('body');

Events.on(body, 'click', function(e) {
  this.classList.toggle('clicked');
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

컴파일된 JavaScript 코드를 살펴보면 중첩된 IIFE 패턴이 사용된 것을 확인할 수 있습니다.

**컴파일 코드:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
var Dom;
(function (Dom) {
  // 중첩된 Events 네임스페이스
  var Events;
  (function (Events) {
    function on(el, type, handler, is_capture) {
      if (is_capture === void 0) { is_capture = false; }
      el.addEventListener(type, handler, is_capture);
    }
    Events.on = on;
    function off(el, type, handler, is_capture) {
      if (is_capture === void 0) { is_capture = false; }
      el.removeEventListener(type, handler, is_capture);
    }
    Events.off = off;
  })(Events = Dom.Events || (Dom.Events = {}));
})(Dom || (Dom = {}));
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-namespace-nesting?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-namespace-nesting - StackBlitz\",\"description\":\"TypeScript : 네임스페이스 멀티 파일\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-namespace-nesting?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-namespace-nesting?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/namespaces.html\#aliases\",\"type\":\"link\",\"title\":\"Namespaces · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 별칭\"}" %}

