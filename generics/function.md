# 제네릭과 함수

## 함수 × 제네릭 {#generic}

다음과 같이 작성된 JavaScript 함수는 배열의 아이템을 특정 타입으로 한정할 수 없습니다.

```typescript
function getItemArray(arr, index) {
  return arr[index];
}

function pushItemArray(arr, item) {
  arr.push(item)
}
```

이를 TypeScript로 변경하면 다음과 같이 구현할 수 있습니다. 타입이 특정지어 지지 않아 `any`를 사용할 수 있습니다. 하지만 **`any`를 사용할 거라면 TypeScript를 사용할 이유가 없습니다.**

```typescript
function getItemArray(arr:any[], index:number):any {
  return arr[index];
}

function pushItemArray(arr:any[], item:any):void {
  arr.push(item);
}
```

TypeScript의 제네릭을 사용하여 외부에서 특정 타입을 지정할 수도 있도록 구현 하면, 사용자가 함수 호출 시 지정한 타입으로 한정할 수 있어 보다 사용 하기 좋아집니다.

```typescript
function getItemArray<T>(arr:T[], index:number):T {
  return arr[index];
}

function pushItemArray<T>(arr:T[], item:T):void {
  arr.push(item);
}


const potatoChip_materials = ['어니언'];

getItemArray(potatoChip_materials, 0);                 // '어니언'
pushItemArray<string>(potatoChip_materials, '사워크림'); // ['어니언', '사워크림']
```

만약 함수 호출 과정에서 전달된 타입과 다른 경우가 발생하면 TypeScript는 컴파일 과정에서 다음과 같은 오류를 발생시켜 코드에 문제가 있음을 사용자에게 알려줍니다.

```typescript
const potatoChip_materials = ['어니언'];
​
// [오류]
// 'string[]' 형식의 인수는 'number[]' 형식의 매개 변수에 할당될 수 없습니다.
// 'string' 형식은 'number' 형식에 할당할 수 없습니다.
pushItemArray<number>(potatoChip_materials, 999);
```

하지만 TypeScript 프로그래밍 과정에서 부득이하게 정해진 타입이 아닌, 경우를 사용해야 하는 경우가 종종 발생합니다. 이런 경우 [타입 어설션](../types/type-assertions.md) 문법을 컴파일 과정의 타입 검사를 우회할 수 있으나, 꼭 필요한 경우에만 사용하는 것이 좋습니다.

```typescript
// pushItemArray()에 사용자가 타입을 지정한 경우
pushItemArray<number>(potatoChip_materials as any, 61);
```

```typescript
// pushItemArray()에 사용자가 타입을 지정하지 않은 경우
pushItemArray(potatoChip_materials, <any>999);
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-generic-function?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-generic-function - StackBlitz\",\"description\":\"TypeScript :제네릭 & 함수\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-generic-function?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-generic-function?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/generics.html\",\"type\":\"link\",\"title\":\"Generics · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 제네릭\"}" %}

