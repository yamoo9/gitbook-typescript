## TypeScript 컴파일 설정 파일

매번 TypeScript 컴파일 명령어를 입력할 때마다 옵션을 추가하거나 제거하는 것은 매우 귀찮고 불편합니다.
명령어를 매번 입력하지 않고, 보다 쉽게 사용하려면 컴파일 설정 파일(`tsconfig.json`)을 만들어 사용하는 것이 편리합니다.

`tsconfig.json` 파일이 있는 위치가 TypeScript 프로젝트의 루트 디렉토리(Root Directory)로 설정됩니다.
이 파일에는 프로젝트를 컴파일 하는데 필요한 루트 파일, 컴파일러 옵션을 설정할 수 있습니다. TypeScript 프로젝트는 다음 방법 중 하나로 컴파일됩니다.

#### `tsconfig.json`을 사용할 경우

- 인풋 파일이 없는 `tsc` 명령일 경우, `tsconfig.json`에 설정된 모든 디렉토리를 체인하여 컴파일 합니다.
- 인풋 파일이 없는 `tsc` 명령일 경우, `-p` 옵션을 사용해 특정 디렉토리 내에 있는 `tsconfig.json` 또는 유효한 JSON 파일을 설정할 수 있습니다.

#### `tsconfig.json`을 사용하지 않을 경우

인풋 파일이 있는 `tsc <파일.ts>` 명령일 경우, `tsconfig.json` 파일은 무시됩니다.

> **NOTE.**<br>
> `tsconfig.json`파일에 설정된 컴파일 옵션 보다 명령어가 우선합니다. (예: `tsc -m "commonjs"`)<br>
> `tsconfig.json` 파일 설정에 대한 자세한 공부하려면 [tsconfig.json][1] 문서를 살펴보세요.

### `tsconfig.json` 생성

```sh
$ tsc --init
```

명령어를 통해 생성된 `tsconfig.json` 설정 코드는 다음과 같습니다. 컴파일러 옵션(`"compilerOptions"`)만 추가되어 있으며, 컴파일러 기본값을 사용할 경우, 각 항목을 주석처리 합니다.
컴파일 옵션의 각 설정은 번역된 주석을 참고합니다. 컴파일 설정 가능한 모든 옵션은 [Compiler Options][2]에서 살펴볼 수 있습니다.

```js
{
  "compilerOptions": {

    /* 기본 옵션
     * ------------------------------------------------------------------------------------------------------------------------------------------------ */
    "target": "es5",                          /* ECMAScript 목표 버전 설정: 'ES3'(기본), 'ES5', 'ES2015', 'ES2016', 'ES2017','ES2018' or 'ESNEXT'. */
    "module": "commonjs",                     /* 생성될 모듈 코드 설정: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', or 'ESNext'. */
    // "lib": [],                             /* 컴파일 과정에 사용될 라이브러리 파일 설정 */
    // "allowJs": true,                       /* JavaScript 파일 컴파일 허용 */
    // "checkJs": true,                       /* .js 파일 오류 리포트 설정 */
    // "jsx": "preserve",                     /* 생성될 JSX 코드 설정: 'preserve', 'react-native', or 'react'. */
    // "declaration": true,                   /* '.d.ts' 파일 생성 설정 */
    // "sourceMap": true,                     /* 소스맵 '.map' 파일 생성 설정 */
    // "outFile": "./",                       /* 복수 파일을 묶어 하나의 파일로 출력 설정 */
    // "outDir": "./dist",                    /* 출력될 디렉토리 설정 */
    // "rootDir": "./",                       /* 입력 파일들의 루트 디렉토리 설정. --outDir 옵션을 사용해 출력 디렉토리 설정이 가능 */
    // "removeComments": true,                /* 출력 시, 주석 제거 설정 */
    // "noEmit": true,                        /* 출력 방출(emit) 유무 설정 */
    // "importHelpers": true,                 /* 'tslib'로부터 헬퍼를 호출할지 설정 */
    // "downlevelIteration": true,            /* 'ES5' 혹은 'ES3' 타겟 설정 시 Iterables 'for-of', 'spread', 'destructuring' 완벽 지원 설정 */
    // "isolatedModules": true,               /* 각 파일을 별도 모듈로 변환 ('ts.transpileModule'과 유사) */

    /* 엄격한 유형 검사 옵션
     * ------------------------------------------------------------------------------------------------------------------------------------------------ */
    "strict": true,                           /* 모든 엄격한 유형 검사 옵션 활성화 */
    // "noImplicitAny": true,                 /* 명시적이지 않은 'any' 유형으로 표현식 및 선언 사용 시 오류 발생 */
    // "strictNullChecks": true,              /* 엄격한 null 검사 사용 */
    // "strictFunctionTypes": true,           /* 엄격한 함수 유형 검사 사용 */
    // "strictPropertyInitialization": true,  /* 클래스에서 속성 초기화 엄격 검사 사용 */
    // "noImplicitThis": true,                /* 명시적이지 않은 'any'유형으로 'this' 표현식 사용 시 오류 발생 */
    // "alwaysStrict": true,                  /* 엄격모드에서 구문 분석 후, 각 소스 파일에 "use strict" 코드를 출력 */

    /* 추가 검사 옵션
     * ------------------------------------------------------------------------------------------------------------------------------------------------ */
    // "noUnusedLocals": true,                /* 사용되지 않은 로컬이 있을 경우, 오류로 보고 */
    // "noUnusedParameters": true,            /* 사용되지 않은 매개변수가 있을 경우, 오류로 보고 */
    // "noImplicitReturns": true,             /* 함수가 값을 반환하지 않을 경우, 오류로 보고 */
    // "noFallthroughCasesInSwitch": true,    /* switch 문 오류 유형에 대한 오류 보고 */

    /* 모듈 분석 옵션
     * ------------------------------------------------------------------------------------------------------------------------------------------------ */
    // "moduleResolution": "node",            /* 모듈 분석 방법 설정: 'node' (Node.js) 또는 'classic' (TypeScript pre-1.6). */
    // "baseUrl": "./",                       /* 절대 경로 모듈이 아닌, 모듈이 기본적으로 위치한 디렉토리 설정 (예: './modules-name') */
    // "paths": {},                           /* 'baseUrl'을 기준으로 상대 위치로 가져오기를 다시 매핑하는 항목 설정 */
    // "rootDirs": [],                        /* 런타임 시 프로젝트 구조를 나타내는 로트 디렉토리 목록 */
    // "typeRoots": [],                       /* 유형 정의를 포함할 디렉토리 목록 */
    // "types": [],                           /* 컴파일 시 포함될 유형 선언 파일 입력 */
    // "allowSyntheticDefaultImports": true,  /* 기본 출력(default export)이 없는 모듈로부터 기본 호출을 허용 (이 코드는 단지 유형 검사만 수행) */
    "esModuleInterop": true                   /* 모든 가져오기에 대한 네임스페이스 객체 생성을 통해 CommonJS와 ES 모듈 간의 상호 운용성을 제공. 'allowSyntheticDefaultImports' 암시 */
    // "preserveSymlinks": true,              /* symlinks 실제 경로로 결정하지 않음 */

    /* 소스맵 옵션
     * ------------------------------------------------------------------------------------------------------------------------------------------------ */
    // "sourceRoot": "./",                    /* 디버거(debugger)가 소스 위치 대신 TypeScript 파일을 찾을 위치 설정 */
    // "mapRoot": "./",                       /* 디버거가 생성된 위치 대신 맵 파일을 찾을 위치 설정 */
    // "inlineSourceMap": true,               /* 하나의 인라인 소스맵을 내보내도록 설정 */
    // "inlineSources": true,                 /* 하나의 파일 안에 소스와 소스 코드를 함께 내보내도록 설정. '--inlineSourceMap' 또는 '--sourceMap' 설정이 필요 */

    /* 실험적인 기능 옵션
     * ------------------------------------------------------------------------------------------------------------------------------------------------ */
    // "experimentalDecorators": true,        /* ES7 데코레이터(decorators) 실험 기능 지원 설정 */
    // "emitDecoratorMetadata": true,         /* 데코레이터를 위한 유형 메타데이터 방출 실험 기능 지원 설정 */

  }
}
```

### include / exclude

컴파일에 포함할 디렉토리/파일 경로를 설정하거나, 제외시킬 수 있습니다. 포함, 제외될 각 항목에는 glob 패턴[^1]을 사용하여 표기할 수 있습니다.

- `*` 0 이상의 모든 문자와 일치 (디렉토리 분리 기호 제외)
- `?` 1개 문자와 일치 (디렉토리 분리 기호 제외)
- `**/` 모든 하위 디렉토리까지 포함

```js
{
  // 컴파일 포함
  "include": [
    "src/**/*"
  ],
  // 컴파일 제외
  "exclude": [
    "node_modules",
    "**/*.spec.ts"
  ],
  // 컴파일 옵션
  "compilerOptions": { ... }
}
```

<!-- 링크 -->

[1]: http://www.typescriptlang.org/docs/handbook/tsconfig-json.html
[2]: https://www.typescriptlang.org/docs/handbook/compiler-options.html
[3]: https://ko.wikipedia.org/wiki/%EA%B8%80%EB%A1%9C%EB%B8%8C_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)


<br>

---

##### 각주

[^1]: 컴퓨터 프로그래밍에서 와일드카드 문자로 여러 파일 이름의 집합을 설정할 때 사용되는 패턴입니다. ([Wiki 참고][3])
