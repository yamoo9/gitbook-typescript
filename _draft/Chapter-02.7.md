#### Object 타입

TypeScript에서는 **변수에 초기 설정된 값을 암시적으로 할당 가능한 데이터 타입으로 설정**하기에 초기 설정된 값과 다른 형태로 할당될 경우 다음과 같은 오류를 출력합니다.

```ts
let Dom = {
  version: '0.0.1',
  el(){},
  css(){}
};

// [오류]
// [ts]
// '{ append(): void; }' 형식은 '{ version: string; el(): void; css(): void; }' 형식에 할당할 수 없습니다.
//   객체 리터럴은 알려진 속성만 지정할 수 있으며 '{ version: string; el(): void; css(): void; }' 형식에 'append'이(가) 없습니다.
// (method) append(): void
Dom = {
  append(){}
};
```

객체의 각 속성별 타입을 명시하려면 다음과 같이 코드를 작성할 수 있습니다.

```ts
let Dom: {version:string, el:()=>void, css:()=>void};

Dom = {
  version: '0.0.1',
  el(){},
  css(){}
};
```

또는

```ts
let Dom: {version:string, el:()=>void, css:()=>void} = {
  version: '0.0.1',
  el(){},
  css(){}
};
```

하지만 타입으로 설정되지 않은 객체의 속성을 새롭게 추가할 경우, 다음과 같은 오류 메시지를 출력합니다.

```ts
// [오류]
// [ts] '{ version: string; el: () => void; css: () => void; }' 형식에 'each' 속성이 없습니다.
// any
Dom.each = function(){};
```

새롭게 추가할 `each` 속성을 타입에 추가하면 문제가 해결되겠지만, 매번 새로운 속성을 추가할 때마다
타입을 지정하는 것은 매우 번거롭습니다. 새 속성을 추가해도 오류 메시지를 출력하지 않게 구성하려면
`[propName: string]: any`를 사용할 수 있습니다.

```ts
let Dom: {
  version: string,
  el: () => void,
  css: () => void,
  [propName: string]: any // ⬅︎
};

Dom = {
  version: '0.0.1',
  el(){},
  css(){}
};

Dom.each   = function(){};
Dom.map    = function(){};
Dom.filter = function(){};
```
