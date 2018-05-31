### Nested Namespace

네임스페이스 내부에 네임스페이스를 선언할 수 있고 공개(export) 할 수도 있습니다. 즉, 중첩된(nested) 네임스페이스를 활용할 수 있습니다. 작성 방법은 다음과 같습니다.

```ts
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

중첩된 네임스페이스에 접근하기 위해 코드가 길어진다면 별칭([Alias](http://www.typescriptlang.org/docs/handbook/namespaces.html#aliases))를 만들어 사용할 수도 있습니다. 네임스페이스 별칭을 만들 때 `import` 키워드를 사용합니다. 아래 코드를 참고하세요.

```ts
// app.ts

/// <reference path="./Dom.ts" />

// Dom.Events 네임스페이스를 import 하여 Events 변수에 참조
import Events = Dom.Events;

let body = Dom.el('body');

Events.on(body, 'click', function(e) {
  this.classList.toggle('clicked');
});
```

컴파일된 JavaScript 코드를 살펴보면 중첩된 IIFE 패턴이 사용된 것을 확인할 수 있습니다.

컴파일 코드:

```js
// JavaScript

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