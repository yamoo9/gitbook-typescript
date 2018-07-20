# 싱글턴

![](../.gitbook/assets/singleton_uml_class_diagram.svg)

## 싱글턴 패턴 {#singleton-pattern}

`private` 접근 제어자를 사용해 `constructor()` 앞에 붙이면 `new` 키워드를 통해 인스턴스를 생성하지 못하도록 제한할 수 있습니다. 대신 공개된 스태틱 메서드 `getInstance()`를 통해 **오직 한 번만 인스턴스를 생성**할 수 있습니다. 이를 싱글턴 패턴이라 부릅니다.

```typescript
class OnlyOne {

  private static instance: OnlyOne;

  public name:string;

  // new 클래스 구문 사용 제한을 목적으로
  // constructor() 함수 앞에 private 접근 제어자 추가
  private constructor(name:string) {
    this.name = name;
  }
  
  // 오직 getInstance() 스태틱 메서드를 통해서만
  // 단 하나의 객체를 생성할 수 있습니다.
  public static getInstance() {
    if (!OnlyOne.instance) {
      OnlyOne.instance = new OnlyOne('싱글턴 객체');
    }
    return OnlyOne.instance;
  }
  
}


/* 인스턴스 생성 ------------------------------------------------ */

// [오류]
// [ts] 'OnlyOne' 클래스의 생성자는 private이며 클래스 선언 내에서만 액세스할 수 있습니다.
// constructor OnlyOne(name: string): OnlyOne
let bad_case = new OnlyOne('오류 발생');

let good_case = OnlyOne.getInstance();
```

{% hint style="danger" %}
컴파일된 JavaScript\(ES5\) 코드를 살펴보면 싱글턴 패턴과 상관 없이 여러 차례 인스턴스를 생성할 수 있습니다. 하지만 **JavaScript는 객체\({}\) 자체가 싱글턴**이 될 수 있습니다.
{% endhint %}

**컴파일 코드:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
var OnlyOne = /** @class */ (function () {
  function OnlyOne(name) {
    this.name = name;
  }
  OnlyOne.getInstance = function () {
    if (!OnlyOne.instance) {
      OnlyOne.instance = new OnlyOne('싱글턴 객체');
    }
    return OnlyOne.instance;
  };
  return OnlyOne;
}());


let only_one    = new OnlyOne('오류 발생'); // 정상 작동
let special_one = new OnlyOne('스페셜 원'); // 새로운 인스턴스 생성!
let normal_one  = new OnlyOne('노멀 원');  // 새로운 인스턴스 생성!!
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-singleton?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"type\":\"rich\",\"title\":\"ts-singleton - StackBlitz\",\"description\":\"TypeScript : 싱글턴 패턴\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-singleton?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-singleton?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=0&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://basarat.gitbooks.io/typescript/docs/tips/singleton.html\",\"type\":\"link\",\"title\":\"singleton pattern · TypeScript Deep Dive\",\"icon\":{\"type\":\"icon\",\"url\":\"https://basarat.gitbooks.io/typescript/gitbook/images/apple-touch-icon-precomposed-152.png\",\"width\":152,\"height\":152,\"aspectRatio\":1},\"caption\":\"TypeScript - 싱글턴 패턴\"}" %}

