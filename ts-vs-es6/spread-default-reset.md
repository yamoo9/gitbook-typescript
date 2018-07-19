# 전개 연산자 / 매개변수

## Default Parameters

ES6부터 함수 매개변수의 기본 값을 설정할 수 있습니다. TypeScript는 매개변수 타입 설정 후 `=` 뒤에 기본 값을 할당하면 됩니다. 컴파일 된 코드를 살펴보면 기본 값으로 할당된 매개변수는 `void 0`과 비교한 후 조건이 참일 경우 기본 값을 설정합니다.

작성 코드:

```typescript
// TypeScript
function countDown(start:number = 10): ()=>number {
  return () => start > 0 ? start-- : 0;
}
```

컴파일 코드:

```javascript
// JavaScript
function countDown(start) {
  if (start === void 0) { start = 10; }
  return function () { return start > 0 ? start-- : 0; };
}
```

## Spread Operator

ES6부터 전개 연산자를 사용할 수 있습니다. 전개 연산자는 쓰임새가 다양합니다. TypeScript 역시 전개 연산자를 훌륭하게 지원합니다. 활용 방법을 살펴봅시다.

작성 코드:

```typescript
// TypeScript
let numbers:number[] = [101, 21, -12, 934, 87];

numbers = [10, 31, 11, ...numbers, -2, 0];

let min_number:number = Math.min(...numbers);
let max_number:number = Math.max(...numbers);
```

컴파일 코드:

```javascript
// JavaScript
var numbers = [101, 21, -12, 934, 87];

numbers = [10, 31, 11].concat(numbers, [-2, 0]);

var min_number = Math.min.apply(Math, numbers);
var max_number = Math.max.apply(Math, numbers);
```

## Rest Parameters

ES6부터 나머지 매개변수를 사용할 수 있습니다. 나머지 매개변수는 함수에서 활용되며 전개 연산자를 매개변수 앞에 붙여 사용합니다. TypeScript에서 활용 방법 또한 동일합니다.

작성 코드:

```typescript
// TypeScript
function makeArray(...args:(number|string)[]): (number|string)[] {
  return args;
}

makeArray(11, 'eleven', 100, 'one hundred');
```

컴파일 코드:

```javascript
// JavaScript
function makeArray() {
  var args = [];
  for (var _i = 0; _i < arguments.length; _i++) {
    args[_i] = arguments[_i];
  }
  return args;
}

makeArray(11, 'eleven', 100, 'one hundred');
```

{% embed data="{\"url\":\"https://slides.com/yamoo9/es6\#/1\",\"type\":\"video\",\"title\":\"ECMAScript 2015 \(ES6\)\",\"description\":\"ECMAScript 2015 학습용 슬라이드.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://slides.com/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://s3.amazonaws.com/media-p.slid.es/thumbnails/11b67116bd8eff286b365665fd3cb621/thumb.jpg?1512767343\",\"width\":500,\"height\":500,\"aspectRatio\":1},\"embed\":{\"type\":\"player\",\"url\":\"https://slides.com/yamoo9/es6/embed\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.2493%;\\\"><iframe src=\\\"https://slides.com/yamoo9/es6/embed\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.7778}}" %}

