# function / union / void 타입

## 함수 매개변수 타입 {#parameters}

다음 코드는 JavaScript에서 아무런 문제가 없지만 `tsconfig.json`에 설정된 [`noImplicitAny`](../cli-env/tsconfig.md#tsconfig-json) 설정 값이 `true`일 경우, 명시적으로 타입 설정을 하지 않아 컴파일 시 다음과 같은 오류를 출력합니다.

```typescript
// [오류]
// [ts] 'id' 매개 변수에는 암시적으로 'any' 형식이 포함됩니다.
// (parameter) id: any
// [ts] 'name' 매개 변수에는 암시적으로 'any' 형식이 포함됩니다.
// (parameter) name: any
function setInfo(id, name) {
  return { id, name };
}

let product_one = setInfo(120912, '스노우보드');
```

{% hint style="info" %}
**noImplicitAny** 설정 값이 **true**이면,   
**암시적인 any 사용 시, 오류 메시지를 출력**합니다.
{% endhint %}

오류 메시지에서 말한 `any` 타입이 아닌, `number`, `string` 타입으로만 인자를 전달 받으려면 매개변수에 다음과 같이 설정해 사용합니다.

```typescript
function setInfo(id:number, name:string) {
  return { id, name };
}

let product_one = setInfo(120912, '스노우보드');
```

### 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-function-params?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-function-params - StackBlitz\",\"description\":\"TypeScript : 함수 매개변수 타입\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-function-params?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-function-params?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 유니온 타입 {#union}

`id` 매개 변수에 설정 가능한 타입 값을 `number`, `string` 모두 가능하게 하려면 파이프\(`|`\)를 사용하여 설정합니다. 이를 유니온\(union\) 타입이라고 부릅니다.

```typescript
function setInfo(id:number|string, name:string){
  return { id, name };
}
```

### 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-union?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-union - StackBlitz\",\"description\":\"TypeScript : 함수 유니온 타입\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-union?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-union?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 함수 리턴 타입 {#return}

`void`는 결과 값을 반환하지 않는 함수에 설정합니다. 반면 **결과 값을 반환하는 함수**의 경우 **명시적으로 반환 값의 타입을 기술할 수 있습니다.** 아래 코드를 살펴보세요.

```typescript
// 리턴 값 타입이 명시적으로 설정되지 않는 함수
function assignClass(name:string): void {
  document.documentElement.classList.add(name);
}

// 리턴 값 타입이 숫자인 함수
function factorial(n:number): number {
  if (n < 0) { return 0; }
  if (n === 1) { return 1; }
  return n * factorial(n-1);
}

// 리턴 값 타입이 문자인 경우
function repeat(text:string, count:number=1): string {
  let result:string = '';
  while(count--) { result += text; }
  return result;
}
```

{% hint style="info" %}
void 0은 undefined와 같습니다. 명시적으로 반환 값을 설정하지 않는 함수는 undefined를 반환하기에 TypeScript에서는 void를 명시합니다.
{% endhint %}

### 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-function-return?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-function-return - StackBlitz\",\"description\":\"TypeScript : 함수 반환값 타입\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-function-return?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-function-return?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 함수 식 {#function-expression}

변수에 함수 값을 할당하는 식\(Expression\)은 컴파일 과정에서 오류를 발생시키지는 않습니다.

```typescript
let assignClass = function(name) {
  document.documentElement.classList.add(name);
};
```

하지만 보다 명시적으로 함수에 설정 가능한 타입을 정의하고자 한다면 다음과 같이 작성할 수 있습니다.

```typescript
// 변수에 함수 매개변수, 리턴 타입에 대한 명시적 설정
let assignClass: (n:string) => void;

// 변수에 함수 값 할당
assignClass = function(name) {
  document.documentElement.classList.add(name);
};
```

변수에 명시적 타입 설정과 함수 값 할당 구문을 별도로 나누지 않고, 한번에 정의할 수도 있습니다.

```typescript
let factorial:(n:number)=>number = function (n) {
  if (n < 0) { return 0; }
  if (n === 1) { return 1; }
  return n * factorial(n-1);
};
```

ES6 화살표 함수 식을 사용하면 다음과 같이 기술할 수도 있습니다.

```typescript
let factorial:(n:number)=>number = n => {
  if (n < 0) { return 0; }
  if (n === 1) { return 1; }
  return n * factorial(n-1);
};
```

문이 아닌 식으로 화살표 함수를 활용하면 다음과 같이 작성해도 결과는 동일합니다. 하지만 읽기는 불편해집니다.

```typescript
let factorial:(n:number)=>number = n => n < 0 ? 0 : n === 1 ? 1 : n * factorial(n-1);
```

### 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-function-expression?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-function-expression - StackBlitz\",\"description\":\"TypeScript : 함수식 타입\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-function-expression?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-function-expression?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/functions.html\",\"type\":\"link\",\"title\":\"Functions · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 함수 데이터 타입\"}" %}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/basic-types.html\#void\",\"type\":\"link\",\"title\":\"Basic Types · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - void 데이터 타입\"}" %}

