# 데코레이터 구성

데코레이터는 하나 이상 연결해 사용할 수 있습니다. 멀티 데코레이터는 수평 또는 수직 나열하여 사용할 수 있습니다.

{% code-tabs %}
{% code-tabs-item title="수평 나열" %}
```typescript
@Size @Color class Button {}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="수직 나열" %}
```typescript
@Size
@Color
class Button {}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 실행흐름\(평가/호출\)

데코레이터의 실행 흐름은 다음 순으로 처리됩니다.

1. 각 데코레이터 표현식은 위에서 아래 방향으로 평가됩니다.
2. 결과는 아래에서 위로 함수를 호출합니다.



데코레이터 팩토리를 사용해 멀티 데코레이터의 실행 흐름을 살펴보는 것이 이해가 빠를 겁니다.

```typescript
function Size() {
  console.log('Size(): 평가됨');
  return function(target:any, prop:string, desc:PropertyDescriptor){
    console.log('Size(): 실행됨')
  }
}
​
function Color() {
  console.log('Color(): 평가됨');
  return function(target:any, prop:string, desc:PropertyDescriptor){
    console.log('Color(): 실행됨')
  }
}
​
class Button {

  @Size()
  @Color()
  isPressed() {}

}
```

console에 출력되는 결과는 다음과 같습니다.

{% code-tabs %}
{% code-tabs-item title="Console" %}
```bash
Size(): 평가됨
Color(): 평가됨
Color(): 실행됨
Size(): 실행
```
{% endcode-tabs-item %}
{% endcode-tabs %}

