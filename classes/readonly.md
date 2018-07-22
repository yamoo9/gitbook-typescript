# 읽기전용 속성

## 읽기 전용 {#readonly}

`readonly` 키워드를 사용해 클래스 속성 이름 앞에 추가하면 읽기 전용 속성이 되어 속성을 다른 값으로 쓸 수 없습니다. 다른 값을 설정하려고 시도하면 컴파일 과정에서 다음과 같은 오류 메시지를 출력합니다.

```typescript
class OnlyOne {

  private static instance:OnlyOne;

  // 읽기 전용 속성 설정
  public readonly name:string;

  private constructor(name:string) {
    this.name = name;
  }

  public static getInstance(name:string):OnlyOne {
    if (!OnlyOne.instance) {
      OnlyOne.instance = new OnlyOne(name);
    }
    return OnlyOne.instance;
  }

}


/* 인스턴스 생성 ------------------------------------------------ */

let special_one = OnlyOne.getInstance('스페셜 원');

console.log(special_one.name);

// [오류]
// [ts] 상수 또는 읽기 전용 속성이므로 'name'에 할당할 수 없습니다.
// (property) OnlyOne.name: string
special_one.name = '노멀 원';
```

{% hint style="info" %}
컴파일된 JavaScript\(ES5\) 코드를 살펴보면 읽기 전용 속성으로 처리되지 않는 것을 확인할 수 있습니다. **JavaScript는 읽기전용\(readonly\) 속성을 지원하지 않기 때문**입니다.
{% endhint %}

**컴파일 코드:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
var OnlyOne = /** @class */ (function () {
  function OnlyOne(name) {
    this.name = name;
  }
  OnlyOne.getInstance = function (name) {
    if (!OnlyOne.instance) {
      OnlyOne.instance = new OnlyOne(name);
    }
    return OnlyOne.instance;
  };
  return OnlyOne;
}());


/* 인스턴스 생성 ------------------------------------------------ */

var special_one = OnlyOne.getInstance('스페셜 원');

console.log(special_one.name); // '스페셜 원'

special_one.name = '노멀 원';

console.log(special_one.name); // '노멀 원'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-readonly?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"type\":\"rich\",\"title\":\"ts-readonly - StackBlitz\",\"description\":\"TypeScript : 읽기전용 속성\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-readonly?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-readonly?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=0&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/classes.html\#readonly-modifier\",\"type\":\"link\",\"title\":\"Classes · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 읽기 전용 속성\"}" %}

