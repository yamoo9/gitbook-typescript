# tuple 타입

## 설명 {#desc}

`tuple`은 JavaScript에서는 지원하지 않는 데이터 타입이지만, TypeScript에서는 **배열 타입을 보다 특수한 형태로 사용할 수 있는** [**`tuple`**](https://namu.wiki/w/%ED%8A%9C%ED%94%8C) **타입을 지원**합니다. `tuple`에 명시적으로 지정된 형식에 따라 아이템 순서를 설정해야 되고, 추가되는 아이템 또한 `tuple`에 명시된 타입만 사용 가능합니다.

```typescript
let book__name_price:[string, number] = ['카밍 시그널', 13320];

// [오류]
// [ts] '[number, string]' 형식은 '[string, number]' 형식에 할당할 수 없습니다.
//      'number' 형식은 'string' 형식에 할당할 수 없습니다.
// let book__name_price: [string, number]
book__name_price = [13320, '카밍 시그널'];

// [오류]
// [ts] 'false' 형식의 인수는 'string | number' 형식의 매개 변수에 할당될 수 없습니다.
book__name_price.push(false);
```

{% hint style="info" %}
### tuple의 발음

튜플? 터플? 투플? 뭘로 발음해야 할까요?   
3개 모두 허용되지만, **터플 발음을 권장**하고 싶습니다.

[tuple의 발음 문제](https://groups.google.com/forum/#!topic/pythonkrdoc/ZS4Lyf6deAQ)를 참고하여 읽어보세요.
{% endhint %}

## 실습 {#practice}

학습한 내용을 아래 에디터에 직접 입력해 확인해봅니다.

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-tuple?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-tuple - StackBlitz\",\"description\":\"TypeScript : 터플 데이터 유형\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-tuple?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-tuple?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/basic-types.html\#tuple\",\"type\":\"link\",\"title\":\"Basic Types · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - Tuple 데이터 타입\"}" %}

