# 인터페이스와 함수타입

인터페이스는 함수 타입도 정의할 수 있습니다. 함수를 할당 받을 변수에 인터페이스를 설정하면 함수 매개변수, 리턴 값 타입을 명시적으로 입력하지 않아도 오류는 발생하지 않습니다. 인터페이스에 정의된 타입 값이 있기 때문입니다.

```typescript
// 인터페이스를 연결하지 않은 함수의 경우, 매개변수, 리턴 값을 설정합니다.
const factorial = (n:number): number => {
  if (n === 0) { return 0; }
  if (n === 1) { return 1; }
  return n * factorial(n - 1);
}

// 펙토리얼 함수 인터페이스 정의
interface FactorialInterface {
  (n: number): number;  
}
​
// 인터페이스를 함수 타입에 설정했기에 별도의 매개변수, 리턴 값 설정을 생략해도 됩니다.
const facto: FactorialInterface = (n) => {
  if (n === 0) { return 0; }
  if (n === 1) { return 1; }
  return n * facto(n - 1);
};
```

주의할 점은 인터페이스가 설정된 함수의 매개변수, 리턴 값 타입을 임의로 변경하면 오류가 발생된다는 점입니다. 사실 그렇게 사용할 거라면 인터페이스를 함수 타입과 함께 사용할 이유가 없을 겁니다.

```typescript
// [오류]
// '(n: number[]) => number' 형식은 'FactorialInterface' 형식에 할당할 수 없습니다.
// 'n' 및 'number' 매개 변수의 형식이 호환되지 않습니다.
// 'number' 형식은 'number[]' 형식에 할당할 수 없습니다.
const fct: FactorialInterface = (n:number[]): number => {
  if (n[0] === 0) { return 0; }
  if (n[0] === 1) { return 1; }
  return n[0] * facto(n[0] - 1);
};
```

