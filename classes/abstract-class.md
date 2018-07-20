# 추상 클래스

![](../.gitbook/assets/image%20%282%29.png)

## 추상화 {#abstraction}

추상 클래스를 정의할 때는 `class` 앞에 `abstract`라고 표기합니다. 또한 추상 메서드를 정의할 때도 `abstract`를 메서드 이름 앞에 붙입니다. 추상 메소드는 **정의만 있을 뿐 몸체\(body\)가 구현되어 있지 않습니다**. 몸체는 추상 클래스를 상속하는 클래스에서 해당 추상 메소드를 통해 필히 구현해야 합니다.

그리고 추상 클래스는 추상 메서드 뿐만 아니라, 실 사용이 가능한 메서드도 정의할 수 있습니다. 추상 클래스를 상속하는 클래스를 통해 생성된 인스턴스는 이 메서드를 사용할 수 있습니다. 추상 클래스는 말 그대로 추상이므로 클래스와 달리 인스턴스를 생성하지 않습니다. 생성 구문을 사용하면 오류가 발생합니다.

```typescript
// 추상 클래스
abstract class Project {

  public project_name:string|null = null;
  private budget:number = 2000000000; // 예산

  // 추상 메서드 정의
  public abstract changeProjectName(name:string): void;

  // 실제 메서드 정의
  public calcBudget(): number {
    return this.budget * 2;
  }

}

// [오류]
// [ts] 추상 클래스의 인스턴스를 만들 수 없습니다.
// constructor Project(): Project
let new_project = new Project();
```

Project 추상 클래스를 상속 받은 WebProject 클래스는 **추상 클래스 내에 정의된 추상 메서드를 반드시 구현**해야 합니다. 구현하지 않을 경우 다음과 같은 오류 메시지를 출력합니다.

```typescript
// 클래스 ⟸ 추상 클래스 상속
class WebProject extends Project {
  // [오류]
  // [ts] 비추상 클래스 'WebProject'은(는) 'Project' 클래스에서 상속된
  // 추상 멤버 'changeProjectName'을(를) 구현하지 않습니다.
  // class WebProject
}
```

그러므로 **추상 클래스를 상속하는 클래스는 추상 클래스에 정의된 메서드를 반드시 구현**해야 합니다.

```typescript
class WebProject extends Project {

  // 추상 클래스에 정의된 추상 메서드 구현
  changeProjectName(name:string): void {
    this.project_name = name;
  }

}


/* 인스턴스 생성 ------------------------------------------------ */

let new_project = new WebProject();

console.log(new_project.project_name); // null

new_project.changeProjectName('CJ 올리브 네트웍스 웹사이트 개편');

console.log(new_project.project_name); // 'CJ 올리브 네트웍스 웹사이트 개편'
```

## 실습 {#practice}

{% embed data="{\"url\":\"https://stackblitz.com/edit/ts-abstract-class?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"type\":\"rich\",\"title\":\"ts-abstract-class - StackBlitz\",\"description\":\"TypeScript : 추상 클래스\",\"icon\":{\"type\":\"icon\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://c.staticblitz.com/assets/icon-664493542621427cc8adae5e8f50d632f87aaa6ea1ce5b01e9a3d05b57940a9f.png\",\"aspectRatio\":0},\"embed\":{\"type\":\"reader\",\"url\":\"https://stackblitz.com/edit/ts-abstract-class?embed=1&file=index.ts&hideExplorer=0&hideNavigation=0&view=editor\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 53.6913%;\\\"><iframe src=\\\"https://stackblitz.com/edit/ts-abstract-class?embed=1&amp;file=index.ts&amp;hideExplorer=0&amp;hideNavigation=0&amp;view=editor\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen></iframe></div>\",\"aspectRatio\":1.8625}}" %}

## 참고 {#reference}

{% embed data="{\"url\":\"https://www.typescriptlang.org/docs/handbook/classes.html\#abstract-classes\",\"type\":\"link\",\"title\":\"Classes · TypeScript\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.typescriptlang.org/assets/images/icons/android-chrome-192x192.png\",\"width\":192,\"height\":192,\"aspectRatio\":1},\"caption\":\"TypeScript - 추상 클래스\"}" %}

