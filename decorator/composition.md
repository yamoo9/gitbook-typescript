# 데코레이터 구성

## 멀티 데코레이터  {#multi-decorators}

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

## 실행흐름\(평가/호출\) {#excute-flow}

데코레이터의 실행 흐름은 다음 순으로 처리됩니다.

1. 각 데코레이터 표현식은 위에서 아래 방향\(⬇︎\)으로 평가됩니다. 
2. 결과는 아래에서 위로\(⬆︎\) 함수를 호출합니다.

데코레이터 팩토리를 사용해 멀티 데코레이터의 실행 흐름을 살펴보는 것이 이해가 빠를 겁니다.

```typescript
// Size 데코레이터 팩토리
function Size() {
  console.log('Size(): 평가됨');
  // Size 데코레이터
  return function(target:any, prop:string, desc:PropertyDescriptor){
    console.log('Size(): 실행됨')
  }
}
​
// Color 데코레이터 팩토리
function Color() {
  console.log('Color(): 평가됨');
  // Color 데코레이터
  return function(target:any, prop:string, desc:PropertyDescriptor){
    console.log('Color(): 실행됨')
  }
}
​
// Button 클래스 정의
class Button {

  // 메서드에 멀티 데코레이터 적용
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

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-decorator-composition?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"type\":\"rich\",\"title\":\"ts-decorator-composition - StackBlitz\",\"description\":\"TypeScript : 데코레이터 구성\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-decorator-composition?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-decorator-composition?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/decorators.html\",\"type\":\"link\",\"title\":\"Decorators · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 데코레이터\"}" %}

