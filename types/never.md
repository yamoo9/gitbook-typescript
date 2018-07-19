# never 타입

## 설명 {#desc}

`never`는 **일반적으로 함수의 리턴 타입으로 사용**됩니다. 함수의 리턴 타입으로 `never`가 사용될 경우, **항상 오류를 출력하거나 리턴 값을 절대로 내보내지 않음을 의미**합니다. 이는 무한 루프\(loop\)에 빠지는 것과 같습니다.

```typescript
// 항상 오류 발생
function invalid(message:string): never {
  throw new Error(message);
}

// never 타입을 결과 추론(Inferred)
function fail() {
  return invalid('실패');
}

// 무한 루프
function infiniteAnimate(): never {
  while ( true ) { infiniteAnimate(); }
}
```

`never` 타입을 지정한 변수에 `never`가 아닌 타입은 할당할 수 없습니다.

```typescript
let never_type:never;

// 오류 발생: 숫자 값을 never 타입 변수에 할당할 수 없습니다.
never_type = 99;

// 함수의 반환 값이 never 타입 이기 때문에 오류가 발생하지 않습니다.
never_type = (function():never { throw new Error('ERROR') })();
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-never?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-never - StackBlitz\",\"description\":\"TypeScript : never 타입\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-never?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-never?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/basic-types.html\#never\",\"type\":\"link\",\"title\":\"Basic Types · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - never 타입\"}" %}

TypeScript 공식 핸드북은 `never` 사용법에 대해 애매한 설명으로 일관합니다. 대신 TypeScript Deep Dive를 참고해 `never` 사용법을 정리하세요.

{% embed data="{\"url\":\"https://basarat.gitbooks.io/typescript/docs/types/never.html\",\"type\":\"link\",\"title\":\"Never Type · TypeScript Deep Dive\",\"icon\":{\"type\":\"icon\",\"url\":\"https://basarat.gitbooks.io/typescript/gitbook/images/apple-touch-icon-precomposed-152.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"caption\":\"Never 타입\"}" %}



