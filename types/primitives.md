# primitive 타입

## 설명 {#desc}

원시 데이터 타입 `number`, `string`, `boolean`을 명시적으로 설정한 변수 선언은 다음과 같이 작성합니다.

```typescript
// 명시적으로 number 타입을 설정
let product_id:number = 124981;

// 명시적으로 string 타입을 설정
let product_name:string = 'VR 글래스';

// 명시적으로 boolean 타입을 설정
let is_waterprofing:boolean = false;
```

설정된 데이터 타입이 아닌, 데이터 타입을 할당하려 할 경우 TypeScript는 컴파일 과정에서 다음과 같은 오류 메시지를 출력해 사용자에게 알립니다.

```typescript
// [오류]
// [ts] '"p9023412"' 형식은 'number' 형식에 할당할 수 없습니다.
// let product_id: number
product_id = 'p9023412';

// [오류]
// [ts] '() => void' 형식은 'string' 형식에 할당할 수 없습니다.
// let product_name: string
product_name = function(){};

// [오류]
// [ts] '() => void' 형식은 'string' 형식에 할당할 수 없습니다.
// let product_name: string
is_waterprofing = 0;
```

## 실습 {#practice}

학습한 내용을 아래 에디터에 직접 입력해 확인해봅니다.

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-primitives?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-primitives - StackBlitz\",\"description\":\"Blank starter project for building TypeScript apps.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-primitives?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-primitives?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

