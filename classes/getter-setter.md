# 게터 / 세터

## getters / setters

비공개로 설정할 필요가 있는 속성을 `private`로 설정한 후, 이 속성에 접근하여 값을 읽거나, 쓰기 위한 Getter, Setter 함수를 사용하여 속성을 정의할 수 있습니다.

```typescript
class Plant {

  // 비공개 속성 '종(Species)'
  private _species:string|null = null;

  // getter 함수
  get species(): string {
    return this._species;
  }

  // setter 함수
  set species(value:string) {
    if ( value.length > 3 ) { this._species = value; }
  }

}


/* 인스턴스 생성 ------------------------------------------------ */

let plant = new Plant();

console.log(plant.species); // null

plant.species = '줄기';

console.log(plant.species); // null

plant.species = '푸른 식물';

console.log(plant.species); // '푸른 식물'
```

JavaScript\(ES5\)로 컴파일된 코드를 살펴보면 `Object.defineProperty()`를 사용하여 `get`, `set` 함수를 사용하여 동일하게 작동하도록 처리한 것을 확인할 수 있습니다.

**컴파일 코드:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
var Plant = /** @class */ (function () {
  function Plant() {
    this._species = 'Default';
  }
  Object.defineProperty(Plant.prototype, "species", {
    // getter
    get: function () {
      return this._species;
    },
    // setter
    set: function (value) {
      if (value.length > 3) {
        this._species = value;
      }
    },
    enumerable: true,
    configurable: true
  });
  return Plant;
}());


/* 인스턴스 생성 ------------------------------------------------ */

var plant = new Plant();

console.log(plant.species); // null

plant.species = '줄기';

console.log(plant.species); // null

plant.species = '푸른 식물';

console.log(plant.species); // '푸른 식물'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-getters-setters?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"type\":\"rich\",\"title\":\"ts-getters-setters - StackBlitz\",\"description\":\"TypeScript : 게터 / 세터\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-getters-setters?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-getters-setters?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=0&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/classes.html\#accessors\",\"type\":\"link\",\"title\":\"Classes · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - getters / setters\"}" %}

