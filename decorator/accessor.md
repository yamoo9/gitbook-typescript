# 접근 제어자 데코레이터

접근 제어자 데코레이터는 접근 제어자 앞에 사용됩니다. 접근 제어자 데코레이터는 접근 제어자에 대한 선언 확인, 수정, 교체하는데 사용될 수 있습니다. 접근 제어자 데코레이터 함수가 전달 받는 인자는 총 3가지로 다음과 같습니다.

1. target: `any`
2. prop: `string`
3. descriptor: `PropertyDescriptor`

접근 제어자 데코레이터 사용 예시를 살펴보겠습니다. 속성 기술자의 `configurable` 속성 값을 `false`로 설정한 접근 제어자 속성은 외부에서 제거할 수 없습니다.

```typescript
// Configurable 데코레이터 팩토리
function Configurable(remove:boolean) {
  // Configurable 데코레이터
  return function (t:any, k:string, d:PropertyDescriptor){
    d.configurable = remove;
  }
}

// Rectangle 클래스
class Rectangle {
  
  private _width:number;
  private _height:number;
  
  constructor(w:number, h:number, public color:string = '#000') {
    this._width = w;
    this._height = h;
  }
  
  // 접근 제어자 데코레이트 사용
  @Configurable(false)
  get width() {
    return this._width;
  }

  @Configurable(false)
  get height() {
    return this._height;
  }
  
}
```

생성된 객체 인스턴스의 접근 제어자 속성\(`configurable: false` 설정\)을 제거하려 시도하면 오류가 발생합니다.

```typescript
// Rectangle 객체 인스턴스 생성
const rect = new Rectangle(400, 210);

// 속성 제거 가능
delete rect.color;

// [오류]
// delete 연산자의 피연산자는 읽기 전용 속성일 수 없습니다.
delete rect.width;
```

