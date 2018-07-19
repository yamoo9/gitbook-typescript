# primitive 타입

원시 데이터 타입 `number`, `string`, `boolean`을 명시적으로 설정한 변수 선언은 다음과 같이 작성합니다.

```typescript
// 명시적으로 number 타입을 설정
let product_id:number = 124981;

// 명시적으로 string 타입을 설정
let product_name:string = 'VR 글래스';

// 명시적으로 boolean 타입을 설정
let is_waterprofing:boolean = false;
```

설정된 데이터 타입이 아닌, 데이터 타입을 할당하려 할 경우 TypeScript는 컴파일 과정에서 다음과 같은 오류 메시지를 출력해 사용자에게 알립니다.

```typescript
// [오류]
// [ts] '"p9023412"' 형식은 'number' 형식에 할당할 수 없습니다.
// let product_id: number
product_id = 'p9023412';

// [오류]
// [ts] '() => void' 형식은 'string' 형식에 할당할 수 없습니다.
// let product_name: string
product_name = function(){};

// [오류]
// [ts] '() => void' 형식은 'string' 형식에 할당할 수 없습니다.
// let product_name: string
is_waterprofing = 0;
```

