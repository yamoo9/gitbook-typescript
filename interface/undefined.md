# 인터페이스 옵션 속성

인터페이스는 클래스와 흡사해 보이지만, 사용 목적이 다릅니다. 인터페이스는 객체 인스턴스를 생성 할 수 없으므로 타입 검사가 사용 목적이 됩니다. 인터페이스를 설정한 클래스는 인터페이스에 정의된, 즉 요구된 사항을 준수해야 합니다.

```typescript
interface ButtonInterface {
  onInit():void;
  onClick():void;
}

class ButtonComponent extends ButtonInterface {

  onInit() { console.log('버튼 컴포넌트 초기화') }
  onClick() { console.log('버튼 클릭') }

}
```

하지만 클래스는 설정된 인터페이스에 정의된 속성 또는 메서드를 반드시 사용하지 않고, 필요에 따라 선택적으로 사용하고 싶을 수도 있을 겁니다. 이 경우 옵션\(Optional\) 속성 설정을 통해 사용자가 선택적으로 사용하게 설정할 수 있습니다.

옵션 속성을 설정하는 방법은 간단합니다. 속성 이름 뒤에 `?`를 붙이면 옵션 속성이 됩니다.

```typescript
interface ButtonInterface {
  // 속성 이름 뒤에 ? 기호가 붙으면 옵션 속성이 됩니다.
  onInit?():void;
  onClick():void;
}

class ButtonComponent extends ButtonInterface {

  // onInit 메서드가 설정되지 않아도 오류를 발생하지 않습니다.

  onClick() { console.log('버튼 클릭') }

}
```

