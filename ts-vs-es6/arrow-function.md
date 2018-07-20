# 화살표 함수

ES6부터 **식\(Expression\)에 한해 화살표 함수식을 활용**할 수 있습니다. TypeScript 또한 화살표 함수식을 사용할 수 있고, 더 나아가 매개변수, 리턴 타입을 명시적으로 선언해 컴파일 과정에서 타입 검사를 수행해 사전에 문제를 방지할 수 있습니다.

**작성 코드:**

{% code-tabs %}
{% code-tabs-item title="TypeScript" %}
```typescript
let corsURL = (url:string): string => `https://crossorigin.me/${url}`;

corsURL('http://yamoo9.herokuapp.com/rest/ediya-menu');
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**컴파일 코드:**

{% code-tabs %}
{% code-tabs-item title="JavaScript" %}
```javascript
var corsURL = function (url) {
  return "https://crossorigin.me/" + url;
};

corsURL('http://yamoo9.herokuapp.com/rest/ediya-menu');
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% embed data="{\"url\":\"https://slides.com/yamoo9/es6\#/1\",\"type\":\"video\",\"title\":\"ECMAScript 2015 \(ES6\)\",\"description\":\"ECMAScript 2015 학습용 슬라이드.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://slides.com/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://s3.amazonaws.com/media-p.slid.es/thumbnails/11b67116bd8eff286b365665fd3cb621/thumb.jpg?1512767343\",\"width\":500,\"height\":500,\"aspectRatio\":1},\"embed\":{\"type\":\"player\",\"url\":\"https://slides.com/yamoo9/es6/embed\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.2493%;\\\"><iframe src=\\\"https://slides.com/yamoo9/es6/embed\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.7778}}" %}

