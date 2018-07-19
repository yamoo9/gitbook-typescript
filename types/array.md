# array 타입

## 설명 {#desc}

명시적 타입 지정 없이 코드를 아래와 같이 작성하면 TypeScript는 컴파일 과정에서 다음과 같은 오류를 출력합니다.

```typescript
let members = ['이권', '감장겸', '장도일'];

// [오류]
// [ts] 'number[]' 형식은 'string[]' 형식에 할당할 수 없습니다.
//      'number' 형식은 'string' 형식에 할당할 수 없습니다.
// let members: string[]
members = [9, 13, 26];
```

오류가 발생한 이유는 암시적으로 `members` 변수에 설정된 데이터 타입이 `string[]`이기 때문입니다. `string` 타입만으로 아이템이 채워진 초기 배열과 달리, `members = [9, 13, 26]` 구문은 `number` 타입으로만 데이터를 채워 문제가 된다고 경고합니다.

```typescript
let members:string[] = ['이권', '감장겸', '장도일'];
```

만약 복합적으로 어떠한 데이터 타입도 아이템으로 설정할 수 있는 배열이 필요하다면 다음과 같이 명시적 타입 선언을 수행할 수 있습니다. `any`는 어떤 데이터 타입도 배열 아이템으로 설정 가능함을 말합니다.

```typescript
let members:any[] = [{name: '이권'}, '감장겸', ['장도일']];
```

`any[]`는 배열 타입을 명시적 선언한 것이므로 배열이 아닌 다른 데이터는 할당될 수 없습니다. 다른 데이터 타입을 할당하면 다음과 같은 오류를 컴파일 과정에서 출력합니다.

```typescript
// [오류]
// [ts] '209' 형식은 'any[]' 형식에 할당할 수 없습니다.
// let members: any[]
members = 209;
```

TypeScript에서 배열 타입 할당 조건을 명시적으로 선언하는 방법은 다음과 같습니다.

```typescript
// 오직 숫자 아이템만 허용
let nums:number[] = [100, 101, 102];

// 오직 문자 아이템만 허용
let strs:string[] = ['ㄱ', 'ㄴ', 'ㄷ'];

// 오직 불리언 아이템만 허용
let boos:boolean[] = [true, false, true];

// 모든 데이터 타입을 아이템으로 허용
let anys:any[] = [100, 'ㄴ', true];

// 특정 데이터 타입만 아이템으로 허용
let selects:(number|string)[] = [102, 'ㅇ'];
```

## 실습 {#practice}

학습한 내용을 아래 에디터에 직접 입력해 확인해봅니다.

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-array?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-array - StackBlitz\",\"description\":\"TypeScript 원시 데이터 유형\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-array?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-array?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

