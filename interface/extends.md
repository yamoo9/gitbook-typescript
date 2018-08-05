# 인터페이스 확장

## 확장 {#inheritance}

클래스를 상속하는 클래스가 있듯이, 인터페이스 또한 **`extends` 키워드를 사용해 인터페이스를 확장 할 수 있습니다.** 

```typescript
interface ButtonInterface {
  readonly _type:string;
  width?:number;
  height?:number;
  onInit?():void;
  onClick():void;
}

// ButtonInterface를 확장하는 ToggleButtonInterface
interface ToggleButtonInterface extends ButtonInterface {
  toggle():void;
  onToggled?():void;
}

// ButtonInterface를 확장하는 CounterButtonInterface
interface CounterButtonInterface extends ButtonInterface {
  increase():void;
  decrease():void;
  onIncreased?():void;
  onDecreased?():void;
}
```

**실습**

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-extends?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-extends - StackBlitz\",\"description\":\"TypeScript : 인터페이스 상속\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-extends?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-extends?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

### 인터페이스 다중 확장

2개 이상의 인터페이스를 확장하는 인터페이스 구현이 가능합니다. 콤마\(`,`\)를 사용하여 다중 확장 설정이 가능합니다.

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
// ButtonInterface, ButtonSizeInterface를 다중 확장하는 ImageButtonInterface
interface ImageButtonInterface extends ButtonInterface, ButtonSizeInterface {
  readonly _url:string;
  getUrl():string;
  setUrl?(url:string):void;
  onChangeUrl?():void;
}
```

**실습**

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-multi-extends?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-multi-extends - StackBlitz\",\"description\":\"TypeScript : 인터페이스 다중 상속\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-multi-extends?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-multi-extends?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

### 인터페이스를 확장한 클래스

인터페이스를 확장한 클래스는 인터페이스에 정의된 준수사항 따라 구현되어야 합니다. 콤마\(`,`\)를 사용하여 다중 인터페이스 확장도 가능합니다.

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

**실습**

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-classes?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-classes - StackBlitz\",\"description\":\"TypeScript : 인터페이스 확장 클래스\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-classes?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-classes?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

### 인터페이스가 지정된 객체 리터럴

클래스 방식이 아닌 객체 리터럴 방식으로 객체를 사용하고자 할 경우, 객체를 할당 받을 변수에 인터페이스를 설정할 수 있습니다. 이 때 인터페이스에 정의된 준수 사항을 따르지 않을 경우, 오류가 발생합니다.

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
// 제네릭(Generic) 문법을 사용하여 설정하면 선언 과정에서 오류가 발생하지 않습니다.
let imageButton = <ImageButtonInterface>{};

imageButton.small = () => { console.log('버튼 크기 small 설정') };
imageButton.large = () => { console.log('버튼 크기 large 설정') };
```

하지만 [`readonly`](undefined.md) 속성의 경우, 읽기 전용 속성으로 초기 선언과정에서 정의되어 있어야 합니다. 그렇지 않은 경우 설정할 수 없습니다.

```typescript
let imageButton = <ImageButtonInterface>{
  _type: 'button',
  _size: 14,
  _url: '',
};

imageButton.small = () => { console.log('버튼 크기 small 설정') };
imageButton.large = () => { console.log('버튼 크기 large 설정') };
```

**실습**

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-object-generic?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-object-generic - StackBlitz\",\"description\":\"TypeScript : 인터페이스 <제네릭>객체 리터럴\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-object-generic?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-object-generic?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/interfaces.html\#interfaces-extending-classes\",\"type\":\"link\",\"title\":\"Interfaces · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 클래스 인터페이스 확장\"}" %}

