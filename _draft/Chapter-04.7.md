### Singleton

`private` 접근 제어자를 사용해 `constructor()` 앞에 붙이면 `new` 키워드를 통해 인스턴스를 생성하지 못하도록 제한할 수 있습니다. 대신 공개된 스태틱 메서드 `getInstance()`를 통해 오직 한 번만 인스턴스를 생성할 수 있습니다. 이를 싱글턴 패턴[^1]이라 부릅니다.

<img src="./assets/Singleton_UML_class_diagram.svg" alt width="300">

```ts
class OnlyOne {

  private static instance: OnlyOne;

  public name: string;

  private constructor(name: string) {
    this.name = name;
  }

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

**주의!**

컴파일된 JavaScript(ES5) 코드를 살펴보면 싱글턴 패턴과 상관 없이 여러 차례 인스턴스를 생성할 수 있습니다. 하지만 JavaScript는 객체(`{}`) 자체가 싱글턴이 될 수 있습니다.

컴파일 코드:
```js
// JavaScript

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

<br>

---

##### 각주

[^1]: 소프트웨어 디자인 패턴에서 싱글턴 패턴(Singleton pattern)을 따르는 클래스는 생성자가 여러 차례 호출되더라도 실제로 생성되는 객체는 하나이고 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴합니다. [Wiki 참고](https://ko.wikipedia.org/wiki/%EC%8B%B1%EA%B8%80%ED%84%B4_%ED%8C%A8%ED%84%B4)