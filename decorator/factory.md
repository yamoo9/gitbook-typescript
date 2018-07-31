# 데코레이터 / 팩토리

## 데코레이터

데코레이터는 [**클래스**](classes.md)**,** [**속성**](properties.md)**,** [**메서드**](methods.md)**,** [**접근 제어자**](accessor.md)**,** [**매개변수**](parameters.md) **등에 사용할 수 있는 특별한 함수**입니다. 선언된 데코레이터 함수를 사용할 때는 데코레이터 이름 앞에 `@`를 붙입니다.

```typescript
// 데코레이터 함수
function Component(target:Function) {
  console.log(target);
  console.log(target.prototype);
}

// 데코레이터를 사용한 클래스 TabsComponent 정의
@Component
class TabsComponent {}
```

{% hint style="info" %}
클래스, 속성, 메서드, 접근자, 매개변수에 따라 데코레이터 함수가 전달 받는 인자는 각각 다릅니다.
{% endhint %}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"type\":\"rich\",\"title\":\"ts-decorator - StackBlitz\",\"description\":\"TypeScript : 데코레이터\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 데코레이터 팩토리

함수 사용 시, 사용자가 인자를 전달할 수 있는 것과 유사하게, 데코레이터 함수 또한 팩토리를 사용해 사용자로부터 인자를 전달 받도록 설정할 수 있습니다. **데코레이터 팩토리 함수는 데코레이터 함수를 감싸는 래퍼 함수**입니다. 팩토리는 사용자로부터 전달 받은 인자를, 내부에서 반환되는 데코레이터 함수는 데코레이터로 사용됩니다.

```typescript
// 데코레이터 팩토리
function Component(value:string) {
  console.log(value);
  
  // 데코레이터 함수
  return function(target:Function) {
    console.log(target);
    console.log(target.prototype);
  }
  
}

// 데코레이터 팩토리를 사용하면 값을 전달할 수 있습니다.
@Component('tabs')
class TabsComponent {}

// TabsComponent 객체 생성
const tabs = new TabsComponent();
```

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator-factory?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"type\":\"rich\",\"title\":\"ts-decorator-factory - StackBlitz\",\"description\":\"TypeScript : 데코레이터 팩토리\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator-factory?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator-factory?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/decorators.html\",\"type\":\"link\",\"title\":\"Decorators · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 데코레이터\"}" %}

