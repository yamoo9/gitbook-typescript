# 속성 with 접근 제어자

## 접근 제어 속성 설정 {#setting-acc-mod-properties}

TypeScript의 클래스 문법은 ES6의 기능을 포함하면서 보다 강력한 기능을 제공합니다. **접근 제어자\(access modifiers\)를 통해 접근 가능한 범위를 설정**할 수 있고, **각 속성에 데이터 타입을 지정**할 수 있습니다.

```typescript
class Book {

  // 제목
  // public: 클래스 외부에서 접근 가능
  public title:string;

  // 저자
  // public은 기본 값으로 생략 가능합니다.
  author:string;

  // 제조 공장
  // private: Book 클래스 내부에서만 접근 가능
  private _manufacturing_plant:string;

  // 종이 유형
  // protected: Book 클래스를 포함한 서브 클래스에서만 접근 가능
  protected paper_type:string;

  // constructor() 매개변수 앞에
  // public, private, protected를 사용하면
  // Book 클래스의 타입(type)을 별도 선언하지 않아도 됩니다.
  constructor(title:string, author:string, public pages:number) {
    this.title = title;
    this.author = author;
    this.pages = pages;
  }

}

/* 인스턴스 생성 ------------------------------------------------ */

let indRevo = new Book('한 권으로 정리하는 4차 산업혁명', '최진기', 367);
console.log(indRevo); // Book {}
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-access-modifiers-props?embed=1&file=index.ts&hideExplorer=0&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-access-modifiers-props - StackBlitz\",\"description\":\"TypeScript : 클래스 속성 접근 제어자\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-access-modifiers-props?embed=1&file=index.ts&hideExplorer=0&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-access-modifiers-props?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/classes.html\#public-private-and-protected-modifiers\",\"type\":\"link\",\"title\":\"Classes · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript 클래스 접근 제어자\"}" %}

