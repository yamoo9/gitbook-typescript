# 제네릭

## 제네릭이란? {#is}

제네릭\(Generics\)은 **클래스 또는 함수에서 사용할 타입\(Type\)을, 그 클래스나 함수를 사용할 때 결정하는 프로그래밍 기법을 말합니다.** JavaScript와 같은 동적 타입 언어만 주로 다루던 개발자에게는 생소한 개념입니다. 하지만 TypeScript는 정적 타입 언어라 제네릭을 지원합니다.

## 제네릭이 왜 필요할까? {#why-needs}

TypeScript로 구현한 Model 클래스는 일반적으로 특정 데이터 타입을 규정하지 않고, 어떤 타입이든 아이템으로 추가하거나, 추출할 수 있습니다.

```typescript
class Model {
  
  private _data: any[] = [];
  
  constructor(data:any[]) {
    this._data = data;
  }
  
  get data():any { 
    return this._data; 
  }
  
  add(item:any):void { 
    this._data.push(item); 
  }
  
  remove(index:number):void { 
    this._data.splice(index, 1); 
  }
  
  item(index:number):any { 
    return this._data[index]; 
  }
  
  clear():void { 
    this._data = []; 
  }
  
}
```

하지만 **특정 데이터 타입을 규정한 Model 클래스를 사용하고자 할 수도 있을 겁니다.** 이런 경우 **클래스 상속을 이용한 새로운 클래스를 생성해 문제를 해결**할 수 있습니다. 예를 들어 객체 타입만 데이터로 추가할 수 있도록 하기 위한 ObjectModel 클래스를 정의한다면 다음과 같이 구성합니다.

```typescript
class ObjectModel extends Model {
​
  constructor(data:object[]=[]) { 
    super(data); 
  }
  
  add(item:object):void { 
    super.add(item); 
  }
​
}
```

하지만 클래스 상속을 사용하면 별도의 자료 타입을 받고자 하는 클래스를 추가해야 하고 중복되는 코드를 양산하기에 불편합니다. 바로 이런 경우에 유용하게 사용할 수 있는 것이 제네릭 입니다.

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-generic-why-needs?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-generic-why-needs - StackBlitz\",\"description\":\"TypeScript :제네릭이 필요한 이\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-generic-why-needs?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-generic-why-needs?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/generics.html\",\"type\":\"link\",\"title\":\"Generics · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 제네릭\"}" %}

