# never 타입

`never`는 일반적으로 함수의 리턴 타입으로 사용됩니다. 함수의 리턴 타입으로 `never`가 사용될 경우, 항상 오류를 출력하거나 리턴 값을 절대로 내보내지 않음을 의미합니다. 이는 무한 루프\(loop\)에 빠지는 것과 같습니다.

```typescript
function invalid(message:string): never {
  throw new Error(message);
}

function infiniteAnimate(): never {
  while ( true ) { infiniteAnimate(); }
}
```

