# 읽기전용 속성

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

**주의!**

컴파일된 JavaScript\(ES5\) 코드를 살펴보면 읽기 전용 속성으로 처리되지 않는 것을 확인할 수 있습니다. JavaScript에서는 읽기전용 속성을 지원하지 않기 때문입니다.

컴파일 코드:

```javascript
// JavaScript

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

