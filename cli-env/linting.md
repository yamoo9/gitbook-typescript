# 린팅

## TSLint 설치 {#install-tslint}

[TSLint](https://palantir.github.io/tslint/)는 린팅 도구로 TypeScript 코드의 가독성, 유지보수 및 오류를 검사 등을 분석하여 결과를 안내합니다. 설치 및 명령어 사용 방법은 다음과 같습니다. 보다 자세한 사용법은 [TSLint command-line interface](https://palantir.github.io/tslint/usage/cli/)을 살펴보세요.

```bash
# TSLint 개발 모듈 로컬 설치
$ npm i -D tslint

# TSLint 설정 파일 생성
$ tslint --init

# TypeScript 파일 린팅 설정
$ tslint -c tslint.json 'src/**/*.ts'
```

{% hint style="info" %}
[TSLint 구성하기 보다 에디터에 확장을 설치하면 보다 손쉽게 린팅 할 수 있습니다.](ide-editors.md#visual-studio-code-extensions)
{% endhint %}

## 에디터 통합\(Integration\) 익스텐션 {#integration-editors}

TSLint를 에디터에 통합하는 다양한 익스텐션 및 라이브러리를 사용할 수 있습니다.

* [TSLint - Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=eg2.tslint)
* [TSLint - Sublime Text](https://packagecontrol.io/packages/SublimeLinter-tslint)
* [TSLint - WebStorm](https://www.jetbrains.com/help/webstorm/tslint.html)

{% hint style="info" %}
익스텐션 목록에 나열되지 않은 에디터를 사용하고 있다면? [Third-Party Tools](https://palantir.github.io/tslint/usage/third-party-tools/)  페이지에서 해당 에디터가 TSLint 익스텐션을 제공하는지 살펴볼 수 있습니다.
{% endhint %}

