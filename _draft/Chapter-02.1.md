#### Number / String / Boolean 타입

원시 데이터 타입(Primitive Data Types)[^1]인 `number`, `string`, `boolean`을 명시적으로 설정한 변수 선언은 다음과 같이 작성합니다.

```ts
// 명시적으로 number 타입을 설정
let product_id:number = 124981;

// 명시적으로 string 타입을 설정
let product_name:string = 'VR 글래스';

// 명시적으로 boolean 타입을 설정
let is_waterprofing:boolean = false;
```

설정된 데이터 타입이 아닌, 데이터 타입을 할당하려 할 경우 TypeScript는 컴파일 과정에서 다음과 같은 오류 메시지를 출력해 사용자에게 알립니다.

```ts
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

<!-- 링크 -->

[1]: http://www.typescriptlang.org/docs/handbook/basic-types.html
[2]: http://www.typescriptlang.org/docs/handbook/variable-declarations.html
[3]: https://ko.wikipedia.org/wiki/%EC%9B%90%EC%8B%9C_%EC%9E%90%EB%A3%8C%ED%98%95

<br>

---

##### 각주

[^1]: 원시 자료형은 컴퓨터 과학에서 프로그래밍 언어가 제공하는 자료형 중 하나로 원시형은 또한 내장형이나 기본형으로도 불립니다. [Wiki 참고][3]