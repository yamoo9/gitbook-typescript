# 속성 데코레이터

## 속성 데코레이터 {#decorators}

속성 데코레이터는 **속성 선언 앞에 사용**됩니다. 속성 데코레이터는 **속성 선언을 확인, 수정, 교체하는데 사용**될 수 있습니다. 앞에서 다룬 메서드, 접근 제어자와 달리 **속성 데코레이터 함수는 전달 받는 인자가 총 2가지 입니다.**

1. target: `any`
2. prop: `string`

속성 데코레이터 사용 예시를 살펴보겠습니다. 속성을 읽거나, 쓸 때 로그를 남기는 데코레이터를 등록해보겠습니다. ECMAScript 5의 [`defineProperty`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)를 사용해 속성을 관찰할 수 있도록 `get`, `set` 설정 합니다.

```typescript
// logProp 속성 데코레이터 정의
function logProp(t:any, p:string) {

  // 속성 값
  let v = t[p];

  // getter 속성
  let getter = function() {
    console.log(`GET: ${p} => ${v}`);
    return v;
  }

  // setter 속성
  let setter = function(new_v:any) {
    v = new_v;
    console.log(`SET: ${p} => ${v}`);
  }


  // 속성 값을 제거한 후,
  if (delete t[p]) {
    // 새 속성 정의
    Object.defineProperty(t, p, {
      // getter 속성 연결
      get: getter,
      // settert 속성 연결
      set: setter,
      enumerable: true,
      configurable: true
    });
  }

}
​
// Button 클래스
class Button {

  // logProp 속성 데코레이터 사용
  @logProp
  type:string = 'button';
  
  @logProp
  version:string = '0.0.2';

  // 생성자
  constructor(public el:HTMLButtonElement){}
​
}
```

Button 객체를 생성하는 구문을 작성한 후, 인스턴스 참조 변수에 할당 합니다. 

type 속성을 읽고, 쓰는 시도를 코드로 작성하면

```typescript
// Button 객체 인스턴스 생성
const btn = new Button( document.querySelector('.button') as HTMLButtonElement );

// btn.type 읽기 시도
console.log(btn.type);

// btn.type 쓰기 시도
btn.type = '버튼';
```

결과는 Console 에 다음과 같이 출력됩니다. 사용자가 속성을 읽거나 쓰려고 시도할 때 마다 로그를 남깁니다.

{% code-tabs %}
{% code-tabs-item title="Console" %}
```typescript
// getter
GET: type => button
typescript.js:54 button

// setter
typescript.js:20 SET: type => 버튼
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator-properties?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"type\":\"rich\",\"title\":\"ts-decorator-properties - StackBlitz\",\"description\":\"TypeScript : 속성 데코레이터\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator-properties?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator-properties?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/decorators.html\",\"type\":\"link\",\"title\":\"Decorators · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 데코레이터\"}" %}

