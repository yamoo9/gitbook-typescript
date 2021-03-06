# 클래스 데코레이터

## 클래스 데코레이터 {#decorator}

클래스에 설정하는 데코레이터를 말합니다. 클래스 데코레이터가 설정된 **클래스 선언을 관찰, 수정 또는 대체하는데 사용**할 수 있습니다. 클래스 데코레이터는 런타임에 함수로 호출 되며, **데코레이팅 되는 클래스가 유일한 인자로 전달되어 호출**됩니다.

```typescript
// Component 데코레이터
function Component(target:Function) {
  
  // 프로토타입 객체 참조
  let $ = target.prototype;

  // 프로토타입 객체 확장
  $.type = 'component';
  $.version = '0.0.1';

}
​
// Component 데코레이터 사용
@Component
class TabsComponent {};

// TabsComponent 객체 인스턴스 생성
const tabs = new TabsComponent();

// 데코레이터로 설정된 프로토타입 확장은 
// 타입 단언(Type Assertion) 필요
console.log((tabs as any).type); // 'component' 출력
```

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator-class?embed=1&file=index.ts\",\"type\":\"rich\",\"title\":\"ts-decorator-class - StackBlitz\",\"description\":\"TypeScript : 클래스 데코레이터\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator-class?embed=1&file=index.ts\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator-class?embed=1&amp;file=index.ts\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 클래스 재정의 {#re-define}

클래스 데코레이터 함수에 생성자 함수 제너릭을 사용한 후, 새로운 클래스를 반환하면 생성자 함수 및 속성 등을 재 정의 할 수 있습니다. **클래스 데코레이터 함수에서 재정의한 속성 및 메서드는 사용자 정의 속성 및 메서드 보다 우선합니다.**

```typescript
// Component 데코레이터
// function Component(target) {
function Component<T extends new (...args:any[]) => {}>(target:T) {

  // 재정의
  return class extends target {
    // 속성
    type:string = 'component';
    version:string = '0.1.0';
    // 메서드
    open() { console.log('탭 활성화') }
    close() { console.log('탭 비활성화') }
  }
​
}
​
// Component 데코레이터 사용
@Component
class TabsComponent {
  
  el:HTMLElement;
  
  constructor(el:HTMLElement) {
    this.el = el;
  }
  
  open() { console.log('사용자 정의 탭 open 메서드') }
​
};
​
// TabsComponent 객체 인스턴스 생성
const tabs = new TabsComponent(document.querySelector('.tabs'));

console.log((tabs as any).type); // 'component' 출력
console.log((tabs as any).open()); // '탭 활성화' 출력
```

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator-class-redefine?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"type\":\"rich\",\"title\":\"ts-decorator-class-redefine - StackBlitz\",\"description\":\"TypeScript : 클래스 재정의\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator-class-redefine?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator-class-redefine?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 클래스 데코레이터 팩토리 {#decorator-factory}

**사용자로부터 옵션 객체를 전달 받으려면 데코레이터 팩토리를 사용해야 합니다.** 데코레이터 함수를 반환하는 래퍼 함수를 만들어 사용자로부터 옵션을 전달 받을 수 있습니다.

```typescript
// ComponentType 타입 앨리어스 정의
type ComponentType = { 
  el:string;
  [prop:string]:any;
};

// Component 데코레이터 팩토리
function Component(options:ComponentType) {
  const _el = document.querySelector(options.el);
  // Component 데코레이터
  return function Component<T extends new (...args:any[]) => {}>(target:T) {
    return class extends target {
      el:HTMLElement = <HTMLElement>_el;
    }
  }
}
​
// Component 데코레이터 사용
@Component({
  el: '.tabs'
})
class TabsComponent {};
​
// TabsComponent 객체 인스턴스 생성
const tabs = new TabsComponent();
console.log((tabs as any).el);
```

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator-class-factory?embed=1&file=index.ts\",\"type\":\"rich\",\"title\":\"ts-decorator-class-factory - StackBlitz\",\"description\":\"TypeScript : 클래스 팩토리\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator-class-factory?embed=1&file=index.ts\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator-class-factory?embed=1&amp;file=index.ts\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/decorators.html\",\"type\":\"link\",\"title\":\"Decorators · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 데코레이터\"}" %}

