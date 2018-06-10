# 인덱스 시그니처 속성

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

하지만 인터페이스를 타입으로 하는 객체 리터럴의 경우는 다릅니다. 새로운 속성을 추가할 수 없다고 오류를 출력합니다. 

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

오류가 발생한 이유는 인터페이스에 정의되지 않은 동적 타입이 할당되는 것을 TypeScript는 기본적으로 오류로 보기 때문입니다. 그래서 오류 메시지를 살펴보면 알려진 속성만 지정할 수 있다고 안내하는 것입니다.

이 문제를 해결 첫번째 방법은 `tsconfig.json` 설정 파일의 `noImlictAny` 옵션 값을 `false`로 변경하는 것입니다.  하지만 TypeScript 프로그래밍 시, 암묵적으로 any 타입을 사용하는 것을 피하고자 한다면 좋은 방법이 될 수 없습니다.

```javascript
{
  "compilerOptions": {
    ...,
    "noImplicitAny": true,
    ...
  }
}
```

두번째 방법은 인터페이스에 인덱스 시그니처\(Index Signature\) 속성을 선언하는 것입니다. 이 방법은 객체의 새로운 추가 속성을 명시적으로 any 타입으로 설정한 것으로 오류를 출력하지 않습니다.

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

