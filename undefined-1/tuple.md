# tuple 타입

`tuple`은 JavaScript에서는 지원하지 않는 데이터 타입이지만, TypeScript에서는 배열 타입을 보다 특수한 형태로 사용할 수 있는 `tuple` 타입을 지원합니다. `tuple`에 명시적으로 지정된 형식에 따라 아이템 순서를 설정해야 되고, 추가되는 아이템 또한 `tuple`에 명시된 타입만 사용 가능합니다.

```typescript
let book__name_price:[string, number] = ['카밍 시그널', 13320];

// [오류]
// [ts] '[number, string]' 형식은 '[string, number]' 형식에 할당할 수 없습니다.
//      'number' 형식은 'string' 형식에 할당할 수 없습니다.
// let book__name_price: [string, number]
book__name_price = [13320, '카밍 시그널'];

// [오류]
// [ts] 'false' 형식의 인수는 'string | number' 형식의 매개 변수에 할당될 수 없습니다.
book__name_price.push(false);
```

## 각주

