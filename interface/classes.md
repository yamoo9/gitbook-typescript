# 인터페이스와 클래스

## 클래스 이행 규칙 {#implement-rules}

인터페이스는 클래스와 비슷한데, 클래스와 달리 **정의만 할 뿐 실제 구현되지 않습니다.** 즉, 어떠한 객체를 생성 했을 때 가져야 할 속성 또는 메서드를 정의한다고 보면 됩니다. \([추상 클래스](../classes/abstract-class.md)와 유사해보입니다\)

클래스 Y9Button에 `implements` 키워드를 사용해 정의된 ButtonInterface 인터페이스를 설정할 수 있습니다. 이는 클래스가 인터페이스에 정의된 실행 규칙을 따라야 함을 선언한 것입니다. 인터페이스가 설정된 클래스에서 인터페이스가 요구하는 것을 구현하지 않을 경우, TypeScript는 컴파일 과정에서 오류를 발생 시킵니다.

```typescript
// 인터페이스 Button 정의
interface ButtonInterface {
  onInit():void;
  onClick():void;
}

// 클래스 Y9Button 인터페이스 Button 확장
class Y9Button implements ButtonInterface {

  width:number;
  height:number;
  
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }
  
  // [오류]
  // 'Y9Button' 클래스가 'Button' 인터페이스를 잘못 구현합니다.
  // 'onInit' 속성이 'Y9Button' 형식에 없습니다.

}
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-interface-class?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"type\":\"rich\",\"title\":\"ts-interface-class - StackBlitz\",\"description\":\"TypeScript : 인터페이스 vs 타입\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-interface-class?embed=1&file=index.ts&hideExplorer=1&hideNavigation=1&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-interface-class?embed=1&amp;file=index.ts&amp;hideExplorer=1&amp;hideNavigation=1&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/interfaces.html\",\"type\":\"link\",\"title\":\"Interfaces · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 인터페이스\"}" %}

