# 제네릭과 함수

다음과 같이 작성된 JavaScript 함수는 배열 데이터를 특정 타입으로 한정할 수 없습니다.

```typescript
function getItemArray(arr, index) {
  return arr[index];
}

function pushItemArray(arr, item) {
  arr.push(item)
}
```

이를 TypeScript로 변경하면 다음과 같이 구현할 수 있습니다. 타입이 특정지어지지 않아 `any`를 사용할 수 있습니다. 하지만 `any`를 사용할 거라면 TypeScript를 사용할 이유가 없습니다.

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

