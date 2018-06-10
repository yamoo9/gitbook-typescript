# 인터페이스와 매개변수

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

