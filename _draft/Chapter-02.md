## Types

TypeScript 파일(`*.ts`)에 코드를 다음과 같이 작성하고 컴파일 하면 오류를 출력합니다.

```ts
let milk_chocolate = '밀크 초콜릿';
milk_chocolate = 2018;

/*
  오류 출력:
    [ts] '2018' 형식은 'string' 형식에 할당할 수 없습니다.
    let milk_chocolate: string
*/
```

발생한 오류를 살펴보면 **초기 할당된 값의 타입이 문자(string) 값인데 반해 나중에 재 할당된 값의 타입이 숫자(number) 값인 것에 대한 오류라고 안내**하고 있습니다.
TypeScript는 JavaScript와 달리 엄격하게 [타입을 관리하는 언어][1]이기 때문에 이와 같은 오류를 출력한 것입니다.

### 명시적 타입 설정

TypeScript는 변수를 [선언할 때 타입을 명시적으로 할당][2] 할 수 있습니다. TypeScript는 JavaScript를 포함하는 수퍼셋(Superset)이므로 JavaScript가 지원하는 데이터 타입을 모두 사용 가능합니다.

- null
- undefined
- number
- string
- boolean
- array
- function
- object
- Symbol