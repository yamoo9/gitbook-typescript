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

## 각주

