# any 타입

## 설명 {#desc}

동적 형 지정 언어인 JavaScript는 선언된 변수에 어떤 값이든 재 할당이 가능합니다. 반면 **TypeScript는 명시적으로 데이터 유형을 설정해 사용하는 정적 형 지정 언어로 타입을 지정해 사용하는 것이 권장**됩니다.

하지만 애플리케이션 개발 시 어떤 타입을 할당해야 할지 알지 못하는 경우\(외부 라이브러리나 동적 콘텐츠를 사용할 경우\)가 있을 수 있습니다. 이런 경우 어떤 타입도 할당 가능하도록 `any`를 설정할 수 있습니다. JavaScript는 기본적으로 변수에 `any`가 할당된 것과 같습니다. \(자동으로 형 변환이 이루어집니다\)

```typescript
// 명시적으로 any 타입 지정
let product_id:any = 124981;

// any 유형이 설정되었으므로 어떤 유형도 값으로 할당 가능
product_id = 'p9023412';
```

다음과 같이 변수 선언과 초기화 과정에서 값을 할당하지 않으면, 암시적으로 `any` 타입이 지정됩니다.

```typescript
// 암시적으로 any 타입 지정
let product_id;

product_id = 124981;
product_id = 'p9023412';
```

## 실습 {#practice}

학습한 내용을 아래 에디터에 직접 입력해 확인해봅니다.

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-any?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-any - StackBlitz\",\"description\":\"TypeScript 원시 데이터 유형\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-any?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-any?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

