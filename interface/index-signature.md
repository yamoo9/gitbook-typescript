# 인덱스 시그니처 속성

![](../.gitbook/assets/image%20%285%29.png)

## 시그니처 {#signature}

인터페이스는 클래스에 설정 되었을 때 주어진 요구사항을 준수한다면? 클래스에 인터페이스에 정의되지 않은 새로운 속성이 추가되어도 오류를 발생시키지 않습니다.

```typescript
interface ButtonInterface {
  onInit?():void;
  onClick():void;
}

class ButtonComponent implements ButtonInterface {
​
  type:string = 'button';
  disabled:boolean = false;

  constructor() {}
​
  onClick() { console.log('버튼 클릭') }

}
```

하지만 인터페이스를 타입으로 하는 **객체 리터럴의 경우는 다릅니다. 새로운 속성을 추가할 수 없다고 오류를 출력합니다.** 

```typescript
interface ButtonInterface {
  onInit?():void;
  onClick():void;
}

const button:ButtonInterface = {

  // [오류]
  // '{ type: string; disabled: boolean; onClick(): void; }' 형식은 
  // 'ButtonInterface' 형식에 할당할 수 없습니다. 개체 리터럴은 알려진 속성만 
  // 지정할 수 있으며 'ButtonInterface' 형식에 'type'이(가) 없습니다.
  type: 'button',
  disabled: false,
  onClick() { console.log('버튼 클릭') }
  
};
```

오류가 발생한 이유는 **인터페이스에 정의되지 않은 동적 타입이 할당되는 것을 TypeScript는 기본적으로 오류로 보기 때문입니다.** 그래서 오류 메시지를 살펴보면 알려진 속성만 지정할 수 있다고 안내하는 것입니다.

이 문제를 해결 첫번째 방법은 `tsconfig.json` 설정 파일의 `noImlictAny` 옵션 값을 `false`로 변경하는 것입니다.  하지만 TypeScript 프로그래밍 시, 암묵적으로 any 타입을 사용하는 것을 피하고자 한다면 좋은 방법이 될 수 없습니다.

```javascript
{
  "compilerOptions": {
    ...,
    "noImplicitAny": false, // 권장되지 않음
    ...
  }
}
```

두번째 방법은 **인터페이스에 인덱스 시그니처\(Index Signature\) 속성을 선언**하는 것입니다. 이 방법은 객체의 새로운 추가 속성을 명시적으로 `any` 타입으로 설정한 것으로 오류를 출력하지 않습니다.

```typescript
interface ButtonInterface {
  onInit?():void;
  onClick():void;
  // 인덱스 시그니처
  [prop:string]: any;
}

const button:ButtonInterface = {
  type: 'button',
  disabled: false,
  onClick() { console.log('버튼 클릭') }
};
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-signature?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-signature - StackBlitz\",\"description\":\"TypeScript : 인터페이스 시그니처\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-signature?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-signature?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/interfaces.html\#excess-property-checks\",\"type\":\"link\",\"title\":\"Interfaces · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 동적 추가 속성 검사\"}" %}

