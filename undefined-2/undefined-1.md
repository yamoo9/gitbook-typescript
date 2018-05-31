# 게터 / 세터

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

컴파일 코드:

```javascript
// JavaScript

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

