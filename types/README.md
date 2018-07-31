# 타입

## 타입이란? {#type-is}

TypeScript 파일\(`*.ts`\)에 코드를 다음과 같이 작성하고 컴파일 하면 오류를 출력합니다.

```typescript
let milk_chocolate = '밀크 초콜릿';
milk_chocolate = 2018;

/*
  오류 출력:
    [ts] '2018' 형식은 'string' 형식에 할당할 수 없습니다.
    let milk_chocolate: string
*/
```

발생한 오류를 살펴보면 **초기 할당된 값의 타입이 문자\(string\) 값인데 반해 나중에 재 할당된 값의 타입이 숫자\(number\) 값인 것에 대한 오류라고 안내**하고 있습니다. **TypeScript**는 JavaScript와 달리 **엄격하게 타입을 관리하는 언어**이기 때문에 이와 같은 오류를 출력한 것입니다.

반면 변수 선언만 있고, 동시에 값을 할당하는 구문이 없을 경우, TypeScript는 타입이 다른 값을 할당 해도 오류를 출력하지 않습니다. 이유는 선언된 `coffee_type` 변수를 [`any`](any.md) 타입으로 처리하기 때문입니다.

```typescript
let coffee_type; // `any` 타입

coffee_type = '콜드브루';
coffee_type = 9112304129312;
```

## 명시적 타입 설정 {#set-explicit-types}

TypeScript는 **변수를 선언할 때 타입을 명시적\(Explicit\)으로 할당** 할 수 있습니다. TypeScript는 JavaScript를 포함하는 수퍼셋\(Superset\)이므로 JavaScript가 지원하는 데이터 타입을 모두 사용 가능합니다. 뿐만 아니라 [클래스](../classes/), [인터페이스](../interface/) 등을 타입으로 설정할 수도 있습니다.

* null
* undefined
* number
* string
* boolean
* array
* function
* object
* Symbol

`any` 타입을 사용한다면 굳이 TypeScript를 쓸 이유가 없습니다. JavaScript는 기본이 `any` 타입을 사용하기 때문입니다. 그러므로 TypeScript를 사용한다면 다음과 같이 타입을 명시적으로 설정하는 것을 권장합니다. **타입을 지정하면 잘못된 타입이 할당 되었을 때 오류를 사용자에게 알려주므로 매우 유용**합니다.

```typescript
let coffee_type:string;

coffee_type = '콜드브루';

coffee_type = 9112304129312;
/*
  [ts] '9120304123' 형식은 'string' 형식에 할당할 수 없습니다.
  let coffee_type: string
*/
```

## 타입 설정을 하는 이유? {#why-setting-types}

"도로 차선" 예시를 들어봅시다. 각 차로에 제한을 두지 않고 자유롭게 차로를 이용할 수 있다면 편할 겁니다. 하지만 자유로운 만큼 사고가 발생할 확률 또한 커집니다. 하지만 각 차로에 접근 가능한 차량에 제한을 둠에 따라, 다소 제약이 따르긴 하지만 사고를 미연에 방지할 수 있습니다.

![](../.gitbook/assets/image%20%287%29.png)

마찬가지로 프로그래밍 작성 시, 타입 지정이 없다면 편하게 코드를 짤 수 있지만 작성한 코드에 문제가 발생할 확률이 높습니다. 반면 **타입을 지정하게 되면 잘못된 것을 사전에 확인할 수 있어 미연에 사고를 방지할 수 있어 유용**합니다.

