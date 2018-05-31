# 모듈

ES6부터 모듈을 지원합니다. TypeScript 또한 모듈을 사용할 수 있습니다. 모듈은 파일 자체 범위\(Local Scope\) 내에서 실행됩니다. 이는 모듈 내 선언된 변수, 함수, 클래스 등을 명시적으로 내보내지 않는 이상 모듈 외부에서 접근할 수 없음을 의미합니다. 반대로 다른 모듈에서 내보낸 변수, 함수, 클래스, 인터페이스 등을 사용하려면 불러와야 합니다.

## 모듈 내보내기

**Dom/events.ts** 파일은 모듈로 자체 영역 내에 `on`, `off` 함수가 선언되어 있습니다. 모듈 내 내보내고자 하는 변수, 함수, 클래스 앞에 `export` 키워드를 붙이면 내보내게 됩니다. 즉, 모듈 외부에서 접근하여 사용할 수 있게 됩니다.

```typescript
// Dom/events.ts

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
```

## 모듈 불러오기

**app.ts** 파일에서 외부 모듈을 불러와 사용하려면 `import` 구문을 사용합니다. 사용 방법은 ES6 모듈 문법과 동일합니다. 이 예제에서는 객체 비구조화 할당\(Destructuring Object\)을 사용해 `on`, `off` 함수를 불러와 사용할 수 있습니다.

```typescript
// app.ts

import { on, off } from './Dom/events';

on(document, 'click', (e) => document.body.style.background = '#912f03');
```

## default 모듈 내보내기

`default`를 사용해 모듈 내에서 내보낼 것을 묶어 기본으로 내보낼 수 있습니다. 이 예제에서는 함수를 속성으로 참조하는 객체를 기본으로 내보냈습니다.

```typescript
// Dom/selectors.ts

function el(selector:string, context:HTMLElement|Document = document): HTMLElement {
  return context.querySelector(selector);
}

function els(selector:string, context:HTMLElement|Document = document): NodeList {
  return context.querySelectorAll(selector);
}

export default { el, els };
```

## default 모듈 불러오기

`default`로 내보내진 모듈은 `import` 구문에서 참조할 모듈 이름\(변수명\)으로 설정할 수 있습니다. 예제에서는 `Dom` 이름으로 모듈을 참조하여 사용합니다.

```typescript
// app.ts

import Dom from './Dom/selectors';
import { on, off } from './Dom/events';

on(document, 'click', (e) => Dom.el('body').style.background = '#912f03');
```

