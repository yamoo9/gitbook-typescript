# 사용자 정의 타입

## 설명 {#desc}

복잡한 타입을 매번 설정하는 것은 상당히 번거로운 작업입니다. `Dom`, `y9` 변수에 할당될 객체의 각 속성별 타입 설정 구문을 살펴보면 매우 복잡하죠.

```typescript
let Dom: {version:string, el:(selector:string)=>void, css:(prop:string)=>void} = {
  version: '0.0.1',
  el(){},
  css(){}
};

let y9: {version:string, el:(selector:string)=>void, css:(prop:string)=>void} = {
  version: '0.0.2',
  el(){},
  css(){}
};
```

이러한 경우 복잡한 타입을 사용자 정의하여 재사용하기 용이하도록 TypeScript는 지원합니다. **타입 별칭\(Type Alias\)을 정의 하려면 `type` 키워드를 사용합니다.**

```typescript
// 사용자 정의 타입 operation 정의
// 타입 별칭(Type Alias)
type operation = {
  data: number[],
  output:(num:number)=>number[]
};

// 사용자 정의 타입 operation 적용 예시
let sum:operation = {
  data: [10, 30, 60],
  output(num){
    return this.data.map(n=>n+num);
  }
};

let multiply:operation = {
  data: [110, 230, 870, 231],
  output(num){
    return this.data.map(n=>n*num);
  }
};
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-type?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-type - StackBlitz\",\"description\":\"TypeScript : 사용자 정의 type\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-type?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-type?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

