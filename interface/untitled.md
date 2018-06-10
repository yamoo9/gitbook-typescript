# 인터페이스와 객체 리터럴

클래스 선언 과정에서 `implements` 키워드를 사용해 명시적으로 인터페이스를 설정하는 방법이 아니어도, 객체 리터럴에 인터페이스를 설정할 수 있습니다. 인터페이스가 설정된 객체는 요구 조건을 충족하지 못할 경우 오류를 출력합니다.

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

