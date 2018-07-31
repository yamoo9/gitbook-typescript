# 인터페이스와 객체 리터럴

## 객체 리터럴 이행 규칙 {#implement-object}

클래스 선언 과정에서 `implements` 키워드를 사용해 명시적으로 인터페이스를 설정하는 방법이 아니어도, **객체 리터럴에 인터페이스를 설정할 수 있습니다.** 인터페이스가 설정된 객체는 요구 조건을 충족하지 못할 경우 오류를 출력합니다.

```typescript
interface OnInitInterface {
  onInit():void;
  initialize():void;
}
​
const o:OnInitInterface = {
  onInit():void { console.log('onInit 라이프 사이클') },
  initialize():void { console.log('객체 초기화') }  
};
​
// [오류]
// '{ settings(): void; }' 형식은 'OnInitInterface' 형식에 할당할 수 없습니다.
// 개체 리터럴은 알려진 속성만 지정할 수 있으며 'OnInitInterface' 형식에 'settings'이(가) 없습니다.
const j:OnInitInterface = {
  settings():void { console.log('객체 설정') }
};
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-object?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-object - StackBlitz\",\"description\":\"TypeScript : 인터페이스 & 객체 리터럴\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-object?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-object?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/interfaces.html\",\"type\":\"link\",\"title\":\"Interfaces · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 인터페이스\"}" %}

