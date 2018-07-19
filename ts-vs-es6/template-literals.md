# 템플릿 리터럴

ES6부터 템플릿 리터럴을 활용해 보다 손쉽게 템플릿 구문을 처리\(문자열 접합\)할 수 있습니다. TypeScript에서도 템플릿 리터럴을 사용해 템플릿 구문을 손쉽게 사용할 수 있습니다.

작성 코드:

```typescript
// TypeScript
let nickname = 'yamoo9';

let greeting_message = `<p>
    안녕하세요 <strong>${nickname}</strong>님.
    가입을 환영합니다. :-)
  </p>
`;
```

컴파일 코드:

```javascript
// JavaScript
var nickname = 'yamoo9';

var greeting_message = "\n  <p>\n    \uC548\uB155\uD558\uC138\uC694 <strong>" + nickname + "</strong>\uB2D8.\n    \uAC00\uC785\uC744 \uD658\uC601\uD569\uB2C8\uB2E4. :-)\n  </p>\n";
```

{% embed data="{\"url\":\"https://slides.com/yamoo9/es6\#/1\",\"type\":\"video\",\"title\":\"ECMAScript 2015 \(ES6\)\",\"description\":\"ECMAScript 2015 학습용 슬라이드.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://slides.com/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://s3.amazonaws.com/media-p.slid.es/thumbnails/11b67116bd8eff286b365665fd3cb621/thumb.jpg?1512767343\",\"width\":500,\"height\":500,\"aspectRatio\":1},\"embed\":{\"type\":\"player\",\"url\":\"https://slides.com/yamoo9/es6/embed\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.2493%;\\\"><iframe src=\\\"https://slides.com/yamoo9/es6/embed\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.7778}}" %}

