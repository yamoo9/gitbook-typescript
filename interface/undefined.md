# 인터페이스 읽기 전용 속성

## 읽기 전용 속성

일부 속성은 처음 만들어 질 때만 외에는 수정할 수 없도록 설정하고 싶을 수 있습니다. 그런 경우 속성의 이름 앞에 `readonly`를 넣어 설정할 수 있습니다.

```typescript
interface Notebook { 
  readonly CPU: string; 
  readonly RAM: string;
};
```

인터페이스 이행이 지정된 객체의 `readonly`로 지정된 속성을 할당 이후, 임의로 변경 시도하면 오류가 발생합니다.

```typescript
let mackbook:Notebook = { 
  CPU: '2.9GHz 코어 i9',
  RAM: '32GB'
};

// [오류]
// 'RAM'은 읽기 전용 속성 또는 상수로 변경할 수 없습니다.
// (property) Notebook["RAM"]: string
macbook.RAM = '128GB';
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-readonly?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-readonly - StackBlitz\",\"description\":\"TypeScript : 인터페이스 읽기 전용 속성\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-readonly?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-readonly?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/interfaces.html\#readonly-properties\",\"type\":\"link\",\"title\":\"Interfaces · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 읽기 전용 속성\"}" %}

