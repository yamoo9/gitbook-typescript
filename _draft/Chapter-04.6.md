### Abstract Class

추상[^1] 클래스를 정의할 때는 `class` 앞에 `abstract`라고 표기합니다. 또한 추상 메서드를 정의할 때도 `abstract`를 메서드 명 앞에 붙입니다. 추상 메소드는 정의만 있을 뿐 몸체(body)가 구현되어 있지 않습니다. 몸체는 추상 클래스를 상속하는 클래스에서 해당 추상 메소드를 통해 필히 구현해야 합니다.

그리고 추상 클래스는 추상 메서드 뿐만 아니라, 실 사용이 가능한 메서드도 정의할 수 있습니다. 추상 클래스를 상속하는 클래스를 통해 생성된 인스턴스는 이 메서드를 사용할 수 있습니다.

추상 클래스는 말 그대로 추상이므로 클래스와 달리 인스턴스를 생성하지 않습니다. 생성 구문을 사용하면 오류가 발생합니다.

```ts
// 추상 클래스
abstract class Project {

  public project_name:string|null = null;
  private budget: number = 2000000000; // 예산

  // 추상 메서드 정의
  public abstract changeProjectName(name:string): void;

  public calcBudget(): number {
    return this.budget * 2;
  }

}

// [오류]
// [ts] 추상 클래스의 인스턴스를 만들 수 없습니다.
// constructor Project(): Project
let new_project = new Project();
```

Project 추상 클래스를 상속 받은 WebProject 클래스는 추상 클래스 내에 정의된 추상 메서드를 반드시 구현해야 합니다. 구현하지 않을 경우 다음과 같은 오류 메시지를 출력합니다.

```ts
// 클래스 ⇐ 추상 클래스 상속
class WebProject extends Project {
  // [오류]
  // [ts] 비추상 클래스 'WebProject'은(는) 'Project' 클래스에서 상속된
  // 추상 멤버 'changeProjectName'을(를) 구현하지 않습니다.
  // class WebProject
}
```

그러므로 추상 클래스를 상속하는 클래스는 추상 클래스에 정의된 메서드를 반드시 구현해야 합니다.

```ts
class WebProject extends Project {

  // 추상 클래스에 정이된 추상 메서드 구현
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

<br>

---

##### 각주

[^1]: 객체의 공통된 속성이나 관계 등을 뽑아내는 행위를 말합니다.