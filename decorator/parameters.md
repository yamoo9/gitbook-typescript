# 매개변수 데코레이터

매개변수 데코레이터는 메서드 선언 앞에 사용됩니다. 매개변수 데코레이터는 클래스 생성자 함수 또는 메서드의 매개변수 에 사용될 수 있습니다. 매개변수 데코레이터 함수는 전달 받는 인자가 총 3가지 입니다.

1. target: `any`
2. prop: `string`
3. parameter\_index: `number`

매개변수 데코레이터는 예시를 살펴보겠습니다. 전달 받은 인자 중 마지막 매개변수 인덱스는 클래스 생성자 또는 메서드  매개변수 내 데코레이터를 사용한 순서입니다. 이름이 없는 생성자 함수의 경우는 `undefined`가 출력됩니다.

```typescript
// Log 매개변수 데코레이터
function Log(t:any, p:string, i:number) {
  console.log(t.name);
  console.log(`매개변수 순서: ${i}, 멤버 이름: ${p === undefined ? 'constructor' : p}`);
}
​
// Button 클래스
class Button {

  el:HTMLButtonElement;
  color:string;

  // 생성자 함수 내에 Log 데코레이터 사용
  constructor(@Log el:HTMLButtonElement, @Log color:string = 'transparent') {
    this.el = el;
    this.color = color;
  }

  // 스태틱 메서드 내에 Log 데코레이터 사용
  static initialize(@Log els:NodeList, @Log color:string = 'transparent'){
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
typescript.js:14 매개변수 순서: 1, 멤버 이름: initialize

Button
typescript.js:14 매개변수 순서: 0, 멤버 이름: initialize

Button
typescript.js:14 매개변수 순서: 1, 멤버 이름: constructor

Button
typescript.js:14 매개변수 순서: 0, 멤버 이름: constructor
```
{% endcode-tabs-item %}
{% endcode-tabs %}

