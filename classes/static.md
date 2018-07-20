# 스태틱 속성, 메서드

## 정적 속성/메서드 {#static-properties}

클래스를 통해 인스턴스를 생성할 필요 없이, 클래스의 속성 또는 메서드를 사용하고자 한다면 `static` 키워드를 사용해 속성, 메서드를 정의합니다.

```typescript
class Mathmatics {

  // 스태틱 속성
  static PI:number = Math.PI;

  // 스태틱 메서드
  // circumference = 둘레(원주)
  static calcCircumference(radius:number) :number {
    return this.PI * radius * 2;
  }

  static calcCircleWidth(radius:number): number {
    return this.PI * Math.pow(radius, 2);
  }

}

// radius = 반지름
let radius = 4;

console.log('PI(원주율) = ', Mathmatics.PI);
console.log(`반지름이 ${radius}인 원의 넓이: πr² = `, Mathmatics.calcCircleWidth(radius));
console.log(`반지름이 ${radius}인 원의 둘레: 2πr = `, Mathmatics.calcCircumference(radius));
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-statics?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"type\":\"rich\",\"title\":\"ts-statics - StackBlitz\",\"description\":\"TypeScript : 스태틱 속성/메서드\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-statics?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-statics?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=0&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/classes.html\#static-properties\",\"type\":\"link\",\"title\":\"Classes · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 스태틱 속성/메서드\"}" %}

