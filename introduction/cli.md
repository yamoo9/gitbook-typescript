# 환경 구성 및 명령어 인터페이스

## TypeScript 환경 구성

TypeScript를 프로젝트에 사용하려면 [Node.js](https://nodejs.org)가 설치되어 있어야 합니다. 그리고 [NPM](https://npmjs.com)을 통해 개발에 필요한 모듈을 설치/관리할 수 있습니다. NPM을 사용해 \[typescript\]\[3\] 개발 모듈을 설치해봅니다.

> **NOTE.**  
>  모듈 설치는 글로벌\(global\), 로컬\(local\) 설치로 나뉘어 집니다. 권장되는 방법은 로컬 설치입니다만, 다수의 프로젝트에서 TypeScript 사용이 요구된다면 편의상 글로벌 설치할 수 있습니다.

```bash
# 글로벌 설치
# npm install --global typescript
$ npm i -g typescript

# 로컬 설치
# npm install --save-dev typescript
$ npm i -D typescript
```

## TypeScript CLI

TypeScript 파일은 `.ts` 확장자를 가집니다. 파일에 작성된 코드를 토대로 컴파일하려면 `tsc` 명령을 사용합니다.

> **NOTE.**  
>  개별 파일을 컴파일 하고자 한다면 `tsc` 명령 뒤에 파일 이름을 붙여 사용합니다.

```bash
# 명령어가 실행된 디렉토리 내 모든 *.ts 파일 컴파일
$ tsc

# 개별 파일 컴파일
$ tsc {파일.ts}
```

### ECMAScript Target

컴파일 코드 ECMAScript 버전 목표\(`--target`, `-t`\)를 설정할 수 있습니다. \(기본 값: `ES3`\)

```bash
# tsc --target 'ES5'
$ tsc -t 'ES5'
```

### Module Type

컴파일 시, 모듈 유형\(`--module`, `-m`\)을 설정할 수 있습니다.

```bash
# tsc --module 'es2015'
$ tsc -m 'es2015'
```

### Output Directory

컴파일 될 아웃풋\(출력\) 디렉토리\(`--outDir`\)를 설정할 수 있습니다.

```bash
$ tsc --outDir './dist'
```

### Output Filename

컴파일 될 아웃풋 파일 이름\(`--outFile`\)을 설정할 수 있습니다.

```bash
# 파일 이름 설정
$ tsc --outFile 'bundle.js'

# 디렉토리 + 파일 이름 설정
$ tsc --outFile './dist/bundle.js'

#
$ tsc --outFile './dist/bundle.js'
```

### Watch

워치\(관찰, 수정/저장 할 때 마다 자동 컴파일, `--watch`, `-w`\)를 설정할 수 있습니다.

```bash
# tsc --watch
$ tsc -w
```

### Help

보다 상세한 사용법을 확인하려면 도움말\(`--help`, `-h`\)을 화면에 출력해 확인할 수 있습니다.

```bash
# tsc 도움말 출력
$ tsc -h

버전 2.8.3
문법: tsc [옵션] [파일 ...]

예시: tsc hello.ts
     tsc --outFile file.js file.ts
     tsc @args.txt

옵션:
 -h, --help                                  도움말 출력
 --all                                       모든 컴파일 옵션 출력
 -v, --version                               컴파일러 버전 출력
 --init                                      'tsconfig.json' 설정 파일 생성
 -p 파일 or 디렉토리, --project 파일 or 디렉토리  설정 파일의 경로 혹은 'tsconfig.json'이 있는 디렉토리에 프로젝트 컴파일
 --pretty                                    컬러/컨텍스트 사용 오류 메시지 스타일 설정(실험 기능)
 -w, --watch                                 인풋 파일 관찰
 -t 버전, --target 버전                        ES 버전 설정 ('ES3'(기본값),'ES5','ES2015','ES2016','ES2017','ES2018','ESNEXT')
 -m 모듈유형, --module 모듈유형                  모듈유형 명시 ('none','commonjs','amd','system','umd','es2015','ESNext')
 --lib                                       컴파일에 포함될 라이브러리 명시
                                             'es5' 'es6' 'es2015' 'es7' 'es2016' 'es2017' 'es2018' 'esnext' 'dom' 'dom.iterable' 'webworker' 'scripthost' 'es2015.core' 'es2015.collection' 'es2015.generator' 'es2015.iterable' 'es2015.promise' 'es2015.proxy' 'es2015.reflect' 'es2015.symbol' 'es2015.symbol.wellknown' 'es2016.array.include' 'es2017.object' 'es2017.sharedmemory' 'es2017.string' 'es2017.intl' 'es2017.typedarrays' 'es2018.promise' 'es2018.regexp' 'esnext.array' 'esnext.asynciterable'
 --allowJs                                   JavaScript 파일 컴파일 허용
 --jsx 코드생성                                JSX 코드생성 명시: 'preserve', 'react-native', 'react'
 -d, --declaration                           '.dts' 파일 생성
 --sourceMap                                 '.map' 파일 생성
 --outFile 파일                               설정된 `*.ts` 파일들을 묶어 1개의 `js` 파일 생성
 --outDir 디렉토리                             아웃풋 디렉토리 구조 재설정
 --removeComments                            주석 제거
 --noEmit                                    아웃풋 출력하지 않음
 --strict                                    모든 엄격한 타입 검사 옵션을 활성화
 --noImplicitAny                             암시적인 'any' 타입일 경우, 식/선언에서 오류 발생
 --strictNullChecks                          엄격한 'null' 검사
 --strictFunctionTypes                       함수 타입 엄격 검사
 --strictPropertyInitialization              클래스 속성 초기화 엄격 검사
 --noImplicitThis                            'this' 참조가 암시적인 'any' 타입일 경우, 오류 발생
 --alwaysStrict                              strict 모드에서 구문 분석 후, 각 소스 파일에 "use strict" 출력
 --noUnusedLocals                            사용되지 않는 지역 변수가 있을 경우, 오류 발생
 --noUnusedParameters                        사용되지 않는 매개 변수가 있을 경우, 오류 발생
 --noImplicitReturns                         함수가 명시적으로 'return' 값을 반환하지 않을 경우, 오류 발생
 --noFallthroughCasesInSwitch                switch문에서 실패한 'case'에 대한 오류 발생
 --types                                     컴파일에 포함될 Type declaration 파일 포함
 --esModuleInterop                           네임스페이스 객체의 모든 불러오기에 대한 CommonJS, ES Modules 호환성 제공. ('암시적으로 allowSyntheticDefaultImports 설정')
 @<file>                                     명령어(Command Line)가 설정된 파일을 입력
```

\[3\]: [https://www.npmjs.com/package/typescript](https://www.npmjs.com/package/typescript)

