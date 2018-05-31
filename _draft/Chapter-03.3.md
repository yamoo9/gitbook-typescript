### Arrow Function

ES6부터 식(Expression)[^1]에 한해 화살표 함수식을 사용할 수 있습니다. TypeScript 또한 화살표 함수식을 사용할 수 있고, 더 나아가 매개변수, 리턴 타입을 명시적으로 선언해 컴파일 과정에서 타입 검사를 수행해 사전에 문제를 방지할 수 있습니다.

작성 코드:
```ts
// TypeScript

let corsURL = (url:string): string => `https://crossorigin.me/${url}`;

corsURL('http://yamoo9.herokuapp.com/rest/ediya-menu');
```

컴파일 코드:
```js
// JavaScript
var corsURL = function (url) {
  return "https://crossorigin.me/" + url;
};

corsURL('http://yamoo9.herokuapp.com/rest/ediya-menu');
```

<!-- 링크 -->
[1]: https://ko.wikipedia.org/wiki/%EC%8B%9D_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)

<br>

---

##### 각주

[^1]:  프로그래밍 언어에서 값, 변수, 연산자, 함수의 모임을 말합니다. [Wiki 참고][1]