# 제네릭과 클래스

## 클래스 × 제네릭 {#generic}

클래스 정의 시, 제네릭을 사용하면 클래스를 사용해 객체를 생성할 때 사용자가 타입을 지정해 사용할 수 있습니다. 사용 방법은 클래스 이름 뒤에 `<T>`를 붙입니다. `T`는 관용적인 식별자로 다른 이니셜을 사용해도 무방합니다.

```typescript
class Model<T> {
  
  private _data:T[] = [];
  
  constructor(data:T[]=[]) {
    this._data = data;
  }
  
  get data():T[] { 
    return this._data; 
  }
  
  add(item:T):void { 
    this._data.push(item); 
  }
  
  remove(index:number):void { 
    this._data.splice(index, 1); 
  }
  
  item(index:number):T { 
    return this._data[index]; 
  }
  
  clear():void { 
    this._data = []; 
  }
  
}
```

사용 예시로 문자 데이터만 허용하는 Model 객체 인스턴스를 사용하고자 한다면, 클래스를 통해 객체를 생성하는 코드에 제네릭 타입 변수 값을 `<string>` 으로 설정해 사용합니다. 설정된 타입이 아닌 다른 타입이 아이템이 사용 되면 컴파일 과정에서 오류 메시지를 출력합니다. 즉, 클래스 사용 과정에서 사용자가 설정한 타입만 사용할 수 있도록 제한합니다.

```typescript
const stringModel = new Model<string>();

stringModel.add('흔들의자');

// [오류]
// '2018' 형식의 인수는 'string' 형식의 매개 변수에 할당될 수 없습니다.
stringModel.add(2018);
```

하지만 TypeScript 프로그래밍 과정에서 부득이하게 정해진 타입이 아닌, 경우를 사용해야 하는 경우가 종종 발생합니다. 이런 경우 [타입 어설션](../types/type-assertions.md) 문법을 사용해 컴파일 과정의 타입 검사를 우회할 수 있습니다만, 꼭 필요한 경우에만 사용하는 것이 좋습니다.

```typescript
stringModel.add(2018 as any);

// 또는

stringModel.add(<any>2018);
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-generic-class?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-generic-class - StackBlitz\",\"description\":\"TypeScript :제네릭이 필요한 이\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-generic-class?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-generic-class?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/generics.html\#generic-classes\",\"type\":\"link\",\"title\":\"Generics · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 제네릭 × 클래스\"}" %}

