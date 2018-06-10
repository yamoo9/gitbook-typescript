# 애로우 함수

ES6부터 식\(Expression\)에 한해 화살표 함수식을 사용할 수 있습니다. TypeScript 또한 화살표 함수식을 사용할 수 있고, 더 나아가 매개변수, 리턴 타입을 명시적으로 선언해 컴파일 과정에서 타입 검사를 수행해 사전에 문제를 방지할 수 있습니다.

작성 코드:

```typescript
// TypeScript

let corsURL = (url:string): string => `https://crossorigin.me/${url}`;

corsURL('http://yamoo9.herokuapp.com/rest/ediya-menu');
```

컴파일 코드:

```javascript
// JavaScript
var corsURL = function (url) {
  return "https://crossorigin.me/" + url;
};

corsURL('http://yamoo9.herokuapp.com/rest/ediya-menu');
```

