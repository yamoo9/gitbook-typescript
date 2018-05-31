## TypeScript 린팅(Linting)

[TSLint](https://palantir.github.io/tslint/)는 린팅[^1] 도구로 TypeScript 코드의 가독성, 유지보수 및 오류를 검사 등을 분석하여 결과를 안내합니다. 설치 및 명령어 사용 방법은 다음과 같습니다.

```sh
# TSLint 개발 모듈 로컬 설치
$ npm i -D tslint

# TSLint 설정 파일 생성
$ tslint --init

# TypeScript 파일 린팅 설정
$ tslint -c tslint.json 'src/**/*.ts'
```

보다 자세한 사용법은 [TSLint command-line interface][1]을 살펴보세요.

<br>

#### 에디터 통합(Integration) 익스텐션

TSLint를 에디터에 통합하는 다양한 익스텐션 및 라이브러리를 사용할 수 있습니다.

- [TSLint - Visual Studio Code][2]
- [TSLint - Sublime Text][3]
- [TSLint - WebStorm][4]

> **NOTE.**<br>
> 익스텐션 목록에 나열되지 않은 에디터를 사용하고 있다면?<br>
> [Third-Party Tools][5] 페이지에서 해당 에디터가 TSLint 익스텐션을 제공하는지 살펴볼 수 있습니다.

<br>

---

##### 각주

[^1]: 린트(lint)는 양털에서 발견된 섬유와 보풀 중 이상이 있는 부분을 가리키는 것에서 비롯되었습니다. 하지만 컴퓨터 사이언스 분야에서는 컴퓨터 언어로 작성된 소프트웨어에서 의심되는 문제를 식별하는 프로그램을 말합니다.

<!-- 링크 -->

[1]: https://palantir.github.io/tslint/usage/cli/
[2]: https://marketplace.visualstudio.com/items?itemName=eg2.tslint
[3]: https://packagecontrol.io/packages/SublimeLinter-tslint
[4]: https://www.jetbrains.com/help/webstorm/tslint.html
[5]: https://palantir.github.io/tslint/usage/third-party-tools/

<!-- ## 참고

- [TypeScript](http://www.typescriptlang.org/)
- [TSLint](https://palantir.github.io/tslint/) -->