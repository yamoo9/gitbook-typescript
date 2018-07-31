# 매개변수 데코레이터

## 매개변수 데코레이터 {#decorators}

매개변수 데코레이터는 메서드 선언 앞에 사용됩니다. 매개변수 데코레이터는 **클래스 생성자 함수 또는 메서드의 매개변수 에 사용**될 수 있습니다. 매개변수 데코레이터 함수는 전달 받는 인자가 총 3가지 입니다.

1. target: `any`
2. prop: `string`
3. parameter\_index: `number`

매개변수 데코레이터는 예시를 살펴보겠습니다. **전달 받은 인자 중 마지막 매개변수 인덱스는 클래스 생성자 또는 메서드  매개변수 내 데코레이터를 사용한 순서입니다.** 이름이 없는 생성자 함수의 경우는 `undefined`가 출력됩니다.

```typescript
// Log 매개변수 데코레이터
function Log(t:any, p:string, i:number) {
  console.log(t.name);
  console.log(`
    매개변수 순서: ${i}, 
    멤버 이름: ${p === undefined ? 'constructor' : p}
  `);
}
​
// Button 클래스
class Button {

  el:HTMLButtonElement;
  color:string;

  // 생성자 함수 내에 Log 데코레이터 사용
  constructor(
    @Log el:HTMLButtonElement, 
    @Log color:string = 'transparent'
  ) {
    this.el = el;
    this.color = color;
  }

  // 스태틱 메서드 내에 Log 데코레이터 사용
  static initialize(
    @Log els:NodeList, 
    @Log color:string = 'transparent'
  ){
    return [].slice.call(els).map(el => new Button(el, color));
  }

}

// Button.initialize() 스태틱 메서드 사용
const btns = Button.initialize( document.querySelectorAll('.button'), '#900' );
```

Console에 출력된 결과는 다음과 같습니다. 매개변수의 순서가 역순인 것이 눈에 띕니다. 버튼 객체 인스턴스들을 순환 생성 처리하는 `initialize` 스태틱 메서드 다음에 `constructor` 생성자 함수가 출력됩니다.

{% code-tabs %}
{% code-tabs-item title="Console" %}
```typescript
Button
매개변수 순서: 1, 멤버 이름: initialize

Button
매개변수 순서: 0, 멤버 이름: initialize

Button
매개변수 순서: 1, 멤버 이름: constructor

Button
매개변수 순서: 0, 멤버 이름: constructor
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator-parameters?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"type\":\"rich\",\"title\":\"ts-decorator-parameters - StackBlitz\",\"description\":\"TypeScript : 매개변수 데코레이터\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator-parameters?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator-parameters?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/decorators.html\",\"type\":\"link\",\"title\":\"Decorators · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 데코레이터\"}" %}

