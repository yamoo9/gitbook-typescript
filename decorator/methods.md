# 메서드 데코레이터

메서드 데코레이터는 메서드 선언 앞에 사용됩니다. 데코레이터는 메서드 선언을 확인, 수정, 교체하는데 사용될 수 있습니다. 메서드 데코레이터 함수가 전달 받는 인자는 총 3가지로 다음과 같습니다.

1. target: `any`
2. prop: `string`
3. descriptor: `PropertyDescriptor`

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

