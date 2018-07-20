# 타입 어설션

## 설명 {#desc}

TypeScript 프로그래밍을 하다 보면 **타입 어설션\(단언, Assertion\)**을 사용해야 할 순간이 오게 됩니다. 타입 어설션은 컴파일러에게 **"이 타입이 특정 타입 임을 단언합니다"**라고 말하는 것과 같습니다. 

다른 언어의 타입 캐스트\(Cast\)와 비슷하지만, 특별한 검사나 데이터 재구성을 수행하지 않습니다. 런타임 시, 영향을 미치지 않으며 **오직 컴파일 과정에서만 사용**됩니다. 타입 어설션을 처리하는 방법은 2가지 입니다. 

1번째 방법은 앵글 브라켓\(angle-bracket, `<>`\) 문법을 사용하는 것입니다.

```typescript
let assertion:any = "타입 어설션은 '타입을 단언'합니다.";

// 방법 1: assertion 변수의 타입을 string으로 단언 처리
let assertion_count:number = (<string>assertion).length;
```

2번째 방법은 `as` 문법을 사용하는 것입니다.

```typescript
let assertion:any = "타입 어설션은 '타입을 단언'합니다.";

// 방법 2: assertion 변수의 타입을 string으로 단언 처리
let assertion_count:number = (assertion as string).length;
```

{% hint style="warning" %}
**두 방법 모두 결과는 동일**합니다. 하지만 **JSX와 함께 사용하는 경우**에는 **as 문법만 허용**됩니다.
{% endhint %}

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-type-assertion?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-type-assertion - StackBlitz\",\"description\":\"TypeScript : 타입 단언\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-type-assertion?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-type-assertion?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/basic-types.html\#type-assertions\",\"type\":\"link\",\"title\":\"Basic Types · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 타입 어설션\"}" %}

{% embed data="{\"url\":\"https://developer.mozilla.org/en-US/docs/Web/API/Event/Event\",\"type\":\"link\",\"title\":\"Event\(\)\",\"description\":\"The Event\(\) constructor creates a new Event.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://developer.mozilla.org/static/img/favicon144.e7e21ca263ca.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://developer.mozilla.org/static/img/opengraph-logo.72382e605ce3.png\",\"width\":600,\"height\":600,\"aspectRatio\":1},\"caption\":\"Event 생성자\"}" %}

{% embed data="{\"url\":\"https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Creating\_and\_triggering\_events\",\"type\":\"link\",\"title\":\"Creating and triggering events\",\"description\":\"This article demonstrates how to create and dispatch DOM events. Such events are commonly called synthetic events, as opposed to the events fired by the browser itself.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://developer.cdn.mozilla.net/static/img/favicon144.a6e4162070f4.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://developer.cdn.mozilla.net/static/img/opengraph-logo.dc4e08e2f6af.png\",\"width\":600,\"height\":600,\"aspectRatio\":1},\"caption\":\"커스텀 이벤트 생성 / 실행\"}" %}



