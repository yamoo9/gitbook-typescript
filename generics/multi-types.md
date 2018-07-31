# 멀티 타입 설정

### 함수 + 멀티 타입 {#function}

함수 또는 클래스에서 멀티 타입 변수를 활용할 수 있습니다. 배열 내부에 사용자가 지정한 멀티 타입을 포함하는 배열을 추가하는 함수를 만든다면 TypeScript 멀티 타입 변수를 사용하여 다음과 같이 작성할 수 있습니다.

```typescript
// pairArray 사용자 정의 타입(Type Alias) 정의
type pairArray = [any, any][];

// 멀티 타입 T, M 설정된 함수 pushPairItem 정의
function pushPairItem<T,M>(arr:pairArray, item:[T,M]):pairArray {
  arr.push(item);
  return arr;
}

// piarArray 타입으로 설정된 data 배열 선언
const data:pairArray = [];

// 멀티 타입을 지정한 후, 적절한 타입을 포함하는 데이터 추가
pushPairItem<boolean, string>(data, [false, 'false']);
pushPairItem<number, string>(data, [2019, '이천십구년']);
```

{% hint style="info" %}
`T`, `M` 등 타입 변수 이름은 사용자가 임의로 지정하는 것입니다. 반복문의 `i`, `j` 변수와 유사하다고 생각하면 이해하기 쉽습니다.
{% endhint %}

### 팩토리 함수 + 멀티 타입 {#factory}

클래스와 옵션을 멀티 타입으로 설정하여 처리하는 팩토리 함수가 있다고 가정해봅시다. 눈여겨 볼 부분은 클래스를 전달 받을 때 타입을 어떻게 설정해야 하는가 입니다.

```typescript
// 클래스 Model
class Model {
  constructor(public options:any) {}
}

// 팩토리 함수
function create<T, U>( C: {new (U): T}, options: U ):T {
  return new C(options);
}
​
// create() 팩토리 함수에 Model, string[] 멀티 타입 설정
create<Model, string[]>(Model, ['class type']);
```

{% hint style="info" %}
`C: {new (U): T}` 표현에서 new \(\)는 **외부에서 전달된 생성자 함수 또는 클래스**를 나타냅니다.  
중괄호로 묶는 표현 대신, `=>`를 사용하는 표현도 가능합니다.

```typescript
C: new (U) => T
```

즉, create\(\) 팩토리 함수는 다음과 같이 작성할 수도 있습니다.

```typescript
function create<T, U>(C: new(U)=>T, options: U): T {
  return new C(options);
}
```
{% endhint %}

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-generic-multi-types?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-generic-multi-types - StackBlitz\",\"description\":\"TypeScript : 제네릭 멀티 타입\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-generic-multi-types?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-generic-multi-types?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/generics.html\#using-class-types-in-generics\",\"type\":\"link\",\"title\":\"Generics · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 제네릭 클래스 타입\"}" %}

