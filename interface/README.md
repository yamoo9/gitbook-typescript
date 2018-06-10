# 인터페이스

**인터페이스**는 JavaScript와 같은 동적 타입 언어 환경에서는 다뤄지지 않았습니다. 하지만 정적 타입 언어인 TypeScript에서는 타입 검사가 요구되므로  인터페이스를 지원합니다. 

인터페이스는 `interface` 키워드를 사용해 다음과 같이 정의합니다.

```typescript
// 인터페이스 Button 정의
interface ButtonInterface {
  onInit():void;
  onClick():void;
}
```

사용자 정의 타입\(Type Alias\)과 유사해보입니다.

```typescript
type ButtonType = {
  onInit():void;
  onClick():void;
}
```

다소 비슷해보이는 것은 사실이나 사용자 정의 타입이 할 수 없는 것을 인터페이스는 할 수 있습니다. 할 수 있는 것 중 하나는 인터페이스는 선언을 병합할 수 있다는 점입니다.

```typescript
interface ButtonInterface {
  onInit():void;
  onClick():void;
}

...

interface ButtonInterface {
  onToggle():void;
}
```

반면 사용자 정의 타입은 선언이 중복되면  오류입니다.

```typescript
type ButtonType = {
  onInit():void;
  onClick():void;
}

// [오류]
// 'ButtonType' 식별자가 중복되었습니다.
type ButtonType = {
  onToggle():void;
}
```

