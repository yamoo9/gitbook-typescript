# 메서드 데코레이터

## 메서드 데코레이터 {#decorators}

메서드 데코레이터는 **메서드 선언 앞에 사용**됩니다. 데코레이터는 **메서드 선언을 확인, 수정, 교체하는데 사용**될 수 있습니다. 메서드 데코레이터 함수가 전달 받는 인자는 총 3가지로 다음과 같습니다.

1. target: `any`
2. prop: `string`
3. descriptor: `PropertyDescriptor`

{% hint style="info" %}
descripter 매개변수는 ES5부터 지원하는 [Object.defineProperty\(\)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)를 참고합니다.
{% endhint %}

메서드 데코레이터 사용 예시를 살펴보겠습니다.

```typescript
// Write 데코레이터 팩토리
function Write(able:boolean = true) {
  // Write 데코레이터
  return function(t:any,p:string,d:PropertyDescriptor) { 
    d.writable = able;
  }
}

// Button 클래스
class Button {
  // 생성자
  constructor(public el:HTMLButtonElement){}
  // Write 데코레이터 사용
  // false 전달 ⟹ 쓰기 불가
  @Write(false)
  disable(){ this.el.setAttribute('disabled', 'disabled'); }
}

// Button 객체 인스턴스 생성 및 변수 참조
const btn = new Button( <HTMLButtonElement>document.querySelector('.button') );

// [오류]
// 쓸 수 없는 메서드를 쓰려고 하였기에 쓸 수 없다고 오류 메시지를 출력합니다.
// Uncaught TypeError: 
// Cannot assign to read only property 'disable' of object '#<Button>'
btn.disable = function() { console.log(this); };
```

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator-metods?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"type\":\"rich\",\"title\":\"ts-decorator-metods - StackBlitz\",\"description\":\"TypeScript : 메서드 데코레이터\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator-metods?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator-metods?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/decorators.html\",\"type\":\"link\",\"title\":\"Decorators · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 데코레이터\"}" %}

