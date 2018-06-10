# enum 타입

TypeScript는 `enum` 데이터 타입을 지원합니다. **기억하기 어려운 숫자 대신 친숙한 이름으로 설정하기 위해서 활용**할 수 있습니다. 열거된 각 멤버는 별도의 값이 설정되지 않은 경우 기본적으로 `0`부터 시작합니다. 아래 코드에서 `sarha` 변수에 할당된 값은 `3`입니다. 설정된 `Team.Designer` 멤버 값이 숫자 `3`이기 때문입니다.

```typescript
enum Team {
  Manager,   // 0
  Planner,   // 1
  Developer, // 2
  Designer,  // 3
};

let sarha:number = Team.Designer; // (enum member) Team.Designer = 3
```

`enum`에 설정된 아이템에 값을 할당할 수도 있습니다. 값이 할당되지 않은 아이템은 이전 아이템의 값에 `+1`된 값이 설정됩니다.

```typescript
enum Team {
  Manager   = 101,
  Planner   = 208,
  Developer = 302,
  Designer, // 302 + 1
};

let yamoo9:number = Team.Manager; // (enum member) Team.Manager = 101
let sarha:number = Team.Designer; // (enum member) Team.Designer = 303
```

`enum` 타입의 편리한 기능으로 숫자 값을 통해 `enum` 값의 멤버 이름을 도출할 수 있다는 점입니다.

```typescript
let role:string = Team[302]; // 'Developer'
```

`enum`은 다음과 같은 JavaScript 코드로 컴파일 됩니다.

컴파일 코드:

```javascript
// JavaScript

var Team;
(function (Team) {
    Team[Team["Manager"] = 0] = "Manager";
    Team[Team["Planner"] = 208] = "Planner";
    Team[Team["Developer"] = 302] = "Developer";
    Team[Team["Designer"] = 303] = "Designer";
})(Team || (Team = {}));

var yamoo9 = Team.Manager;
var sarha = Team.Designer;
```

