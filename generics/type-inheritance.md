# 타입 변수 상속

## 타입 변수 상속

**제네릭 타입 변수는 기존의 타입 변수를 상속할 수도 있습니다.** 이를 활용하면 입력 받을 타입을 지정할 수 있습니다. 예시 코드를 살펴보면 Model 클래스는 외부에서 사용할 때 타입을 지정할 수 있습니다. Model 클래스는 `add()` 인스턴스 메서드를 가지는데 아이템을 한 번에 하나씩 밖에 추가할 수 없습니다. 

사용에 편의를 더하기 위해 Model 객체 인스턴스 생성과 동시에 여러 아이템을 동시에 추가하는 `initializeModel()` 팩토리 함수를 작성할 때, `Model<U>`를 상속 받는 타입 `T`를 활용할 수 있습니다.

```typescript
// Model 클래스
class Model<T> {
  
  constructor(private _data:T[] = []) {}
  
  add(item:T):void {
    this._data.push(item);
  }

}

// Model 초기화 팩토리 함수
function initializeModel<T extends Model<U>, U>(C: new () => T, items:U[]):T {
  const c = new C();
  items.forEach(item => c.add(item));
  return c;
}

// 사용 예시
initializeModel<Model<string>, string>(Model, ['타입', '변수', '상속']);
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-generic-type-inherit?embed=1&file=index.ts&view=editor\",\"type\":\"rich\",\"title\":\"ts-generic-type-inherit - StackBlitz\",\"description\":\"TypeScript : 제네릭 타입 변수 상속\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-generic-type-inherit?embed=1&file=index.ts&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-generic-type-inherit?embed=1&amp;file=index.ts&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/generics.html\",\"type\":\"link\",\"title\":\"Generics · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 제네릭\"}" %}

