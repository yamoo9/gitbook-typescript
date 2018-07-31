# 인터페이스와 매개변수

## 매개변수 이행 규칙 {#implement-params}

매개변수에도 인터페이스를 설정할 수 있습니다. 인터페이스가 설정된 매개변수는 인터페이스에 정의된 요구 사항을 충족해야 합니다. 충족하지 못할 경우, TypeScript는 컴파일 과정에서 오류를 발생 시킵니다.

```typescript
// onInit(), initialize() 메서드가 필요함을 정의한 인터페이스
interface OnInitInterface {
  onInit():void;
  initialize():void;
}
​
// 인터페이스 요구 조건에 충족하는 객체
const o = {
  onInit():void { console.log('onInit 라이프 사이클') },
  initialize():void { console.log('객체 초기화') }  
};

// 인터페이스 요구 조건에 충족하지 않은 객체​
const j = {
  settings():void { console.log('객체 설정') }
};
​
// 매개변수에 인터페이스가 설정된 함수
function ready(m:OnInitInterface):void {
  m.onInit();
  m.initialize();
}
​
// 전달된 객체 o는 OnInitInterface 인터페이스 요구 조건을 충족
ready(o);

// [오류]
// '{ settings(): void; }' 형식의 인수는 'OnInitInterface' 형식의 매개 변수에 할당될 수 없습니다.
// 'onInit' 속성이 '{ settings(): void; }' 형식에 없습니다.
ready(j);
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-params?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-params - StackBlitz\",\"description\":\"TypeScript : 인터페이스 & 매개변수\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-params?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-params?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/interfaces.html\",\"type\":\"link\",\"title\":\"Interfaces · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 인터페이스\"}" %}

