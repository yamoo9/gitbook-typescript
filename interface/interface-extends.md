# 인터페이스 상속

클래스를 상속하는 클래스가 있듯이, 인터페이스 또한 `extends` 키워드를 사용해 인터페이스를 상속 할 수 있습니다. 

```typescript
interface ButtonInterface {
  readonly _type:string;
  width?:number;
  height?:number;
  onInit?():void;
  onClick():void;
}

// ButtonInterface를 상속하는 ToggleButtonInterface
interface ToggleButtonInterface extends ButtonInterface {
  toggle():void;
  onToggled?():void;
}

// ButtonInterface를 상속하는 CounterButtonInterface
interface CounterButtonInterface extends ButtonInterface {
  increase():void;
  decrease():void;
  onIncreased?():void;
  onDecreased?():void;
}
```

### 인터페이스 다중 상속

2개 이상의 인터페이스를 상속하는 인터페이스 구현이 가능합니다.

```typescript
interface ButtonInterface {
  readonly _type:string;
  width?:number;
  height?:number;
  onInit?():void;
  onClick():void;
}
​
interface ButtonSizeInterface {
  readonly _size:number;
  small():void;
  medium():void;
  large():void;
  onChangeSize?():void;
}
​
// ButtonInterface, ButtonSizeInterface를 다중 상속하는 ImageButtonInterface
interface ImageButtonInterface extends ButtonInterface, ButtonSizeInterface {
  readonly _url:string;
  getUrl():string;
  setUrl?(url:string):void;
  onChangeUrl?():void;
}
```

### 인터페이스를 확장한 클래스

인터페이스를 확장한 클래스는 인터페이스에 정의된 준수사항 따라 구현되어야 합니다.

```typescript
class ImageButton implements ImageButtonInterface {
  readonly _type:string;
  readonly _url:string;
  readonly _size:number;
  onClick(){}
  getUrl() { return this._url; }
  small() {}
  medium() {}
  large() {}
}
```

### 인터페이스가 지정된 객체 리터럴

클래스 방식이 아닌, 객체 리터럴 방식으로 객체를 사용하고자 할 경우, 객체를 할당 받을 변수에 인터페이스가 설정할 수 있습니다. 이 때 인터페이스에 정의된 준수 사항을 따르지 않을 경우, 오류가 발생합니다.

```typescript
// [오류]
// '{}' 형식은 'ImageButtonInterface' 형식에 할당할 수 없습니다.
// '_url' 속성이 '{}' 형식에 없습니다.
let imageButton:ImageButtonInterface = {};
```

오류를 해결하려면 인터페이스가 요구하는 사항에 맞춰 속성 및 메서드를 즉시 정의해야 합니다.

```typescript
let imageButton:ImageButtonInterface = {
  _url: '',
  _size: 14,
  _type: 'button',
  getUrl() { return this._url; },
  setUrl(url:string) { },
  small() { },
  medium() { },
  large() { },
  onClick() { },
};
```

객체를 초기 선언하는 과정이 아닌, 추후 인터페이스에 정의된 속성을 추가할 수 있도록 사용하고자 한다면 어떻게 해야 할가요? 해결 방법은 [제네릭](https://uid.gitbook.io/typescript/generics) 문법을 사용하여 변수에 할당하는 것입니다.

```typescript
// 제네릭(Generic) 문법을 사용하여 설정하면 
let imageButton = <ImageButtonInterface>{};

imageButton.small = () => { console.log('버튼 크기 small 설정') };
imageButton.large = () => { console.log('버튼 크기 large 설정') };
```

하지만 `readonly` 속성의 경우, 읽기 전용 속성으로 초기 선언과정에서 정의되어 있어야 합니다. 그렇지 않은 경우 설정할 수 없습니다.

```typescript
let imageButton = <ImageButtonInterface>{
  _type: 'button',
  _size: 14,
  _url: '',
};

imageButton.small = () => { console.log('버튼 크기 small 설정') };
imageButton.large = () => { console.log('버튼 크기 large 설정') };
```

