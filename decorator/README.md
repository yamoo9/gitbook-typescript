# 데코레이터

데코레이터\(Decorator\)는 [ECMAScript에 새롭게 제안된 기능](https://github.com/tc39/proposal-decorators#decorators)이며, TypeScript의 실험적 기능으로 클래스 선언과 멤버에 대한 주석\(annotations\)과 메타 프로그래밍 구문을 모두 추가 할 수있는 방법을 제공합니다.

### 데코레이터 사용을 위한 설정

데코레이터를 TypeScript에서 사용하려면 `tsconfig.json` 설정 `experimentalDecorators` 값을 `true`로 설정해야 합니다. 환경 설정 없이 데코레이터를 사용하려면 컴파일 과정에서 오류 메시지를 출력합니다.

{% code-tabs %}
{% code-tabs-item title="tsconfig.json" %}
```javascript
{
  "compilerOptions": {
  ...  
  "experimentalDecorators": true,
  ...
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
데코레이터는 차후 릴리스 시, 변경 될 수있는 실험 기능입니다.
{% endhint %}



### 참고

{% embed data="{\"url\":\"https://github.com/tc39/proposal-decorators\#decorators\",\"type\":\"link\",\"title\":\"tc39/proposal-decorators\",\"description\":\"proposal-decorators - Decorators for ES6 classes\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars3.githubusercontent.com/u/1725583?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1},\"caption\":\"ECMAScript TC39 - 클래스 데코레이터 제안입니다.\"}" %}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/decorators.html\",\"type\":\"link\",\"title\":\"\\r\\n    \\r\\n      Decorators · TypeScript\\r\\n    \\r\\n  \",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript 핸드북 - 데코레이터에 대한 사용법입니다.\"}" %}

