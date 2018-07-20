# 클래스

## ES6: Class

ES6부터 **클래스 문법을 사용**할 수 있습니다. 클래스를 정의하고, 속성을 설정하는 기본 사용법은 다음과 같습니다.

```javascript
/* 클래스 */
class Book {

  /* 생성자 */
  constructor(title, author, pages) {
    this.title  = title;
    this.author = author;
    this.pages  = pages;
  }

}

/* 인스턴스 생성 ------------------------------------------------ */

let indRevo = new Book('한 권으로 정리하는 4차 산업혁명', '최진기', 367);
console.log(indRevo); // Book {}
```

## TypeScript: Class

TypeScript의 클래스는 ES6의 클래스 문법을 넘어 강력한 기능을 제공합니다.

* access modifiers \( [속성](prop-acc-mod.md) \| [메서드](method-acc-mod.md) \)
* [inheritance](inherit.md)
* [getter / setter](getter-setter.md)
* [static](static.md)
* [abstract class](abstract-class.md)
* [singleton](singleton.md)
* [readonly](readonly.md)

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-class?embed=1&file=index.ts&hideExplorer=0&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-class - StackBlitz\",\"description\":\"TypeScript : 타입 단언\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-class?embed=1&file=index.ts&hideExplorer=0&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-class?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}



