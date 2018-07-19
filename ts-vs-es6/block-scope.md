# 블록 영역 변수, 상수 선언

ES6부터 `let`, `const` 키워드를 사용해 변수, 상수를 정의할 수 있습니다. TypeScript 또한 마찬가지로 활용 가능합니다. `let` 변수는 `var` 변수가 불러오는 문제점\(중복 선언, 호이스트에 따른 의도치 않은 동작 등\)을 훌륭하게 해결하므로 사용이 권장됩니다. 그리고 `let`, `const` 키워드를 사용하면 블록 스코프\(Block Scope\)를 사용할 수 있습니다.

작성 코드:

```typescript
// TypeScript

let context = document.querySelector('html');

{
  let context = document.querySelector('body');
  console.log('블록문 내부 context = ', context);
}

console.log('글로벌 context = ', context);
```

컴파일 코드:

```javascript
// JavaScript

var context = document.querySelector('html');

{
  var context_1 = document.querySelector('body');
  console.log('블록문 내부 context = ', context_1);
}

console.log('글로벌 context = ', context);
```

{% embed data="{\"url\":\"https://slides.com/yamoo9/es6\#/1\",\"type\":\"video\",\"title\":\"ECMAScript 2015 \(ES6\)\",\"description\":\"ECMAScript 2015 학습용 슬라이드.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://slides.com/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://s3.amazonaws.com/media-p.slid.es/thumbnails/11b67116bd8eff286b365665fd3cb621/thumb.jpg?1512767343\",\"width\":500,\"height\":500,\"aspectRatio\":1},\"embed\":{\"type\":\"player\",\"url\":\"https://slides.com/yamoo9/es6/embed\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.2493%;\\\"><iframe src=\\\"https://slides.com/yamoo9/es6/embed\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.7778}}" %}

