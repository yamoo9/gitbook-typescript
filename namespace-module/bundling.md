# 모듈 번들링

## Module Bundling

모듈 사용법을 공부했지만, ES6 모듈을 모든 브라우저에서 지원하지 않아 정상 작동하지 않습니다. 그러한 이유로 모듈 번들러 사용이 대중화되었습니다. 브라우저 단에서 모듈을 사용할 수 없으니, 개발 단에서 모듈을 묶어 하나의 파일로 만들어 낼 필요가 있었던 것이죠.

이 예제에서는 [Rollup](https://rollupjs.org)을 사용해 번들링을 수행해보겠습니다. 사용할 플러그인은 [rollup-plugin-typescript2](https://www.npmjs.com/package/rollup-plugin-typescript2) 입니다. Rollup과 플러그인을 사용하기 위해서는 설치가 필요합니다. 아래 나열된 명령어를 순차적으로 실행합니다.

```bash
# package.json 파일 생성
$ npm init -y

# typescript rollup rollup-plugin-typescript2 개발 모듈 설치
$ npm i -D typescript rollup rollup-plugin-typescript2
```

설치가 완료되면 `package.json` 파일 `devDependencies` 항목에 코드가 추가됩니다.

```javascript
// package.json

"devDependencies": {
  "rollup": "^0.59.3",
  "rollup-plugin-typescript2": "^0.14.0",
  "typescript": "^2.8.3"
}
```

이어서 `rollup.config.js` 파일을 생성한 후, 다음과 같이 코드를 작성합니다.

```javascript
// rollup.config.js

import typescript from 'rollup-plugin-typescript2';

export default {
  input: './src/app.ts',
  output: {
    file: './dist/bundle.js',
    format: 'iife'
  },
  plugins: [
    typescript({
      tsconfig: 'tsconfig.json'
    })
  ]
}
```

다음으로 `package.json`에 `scripts` 항목에 `bundle` 명령을 추가합니다.

```javascript
// package.json

"scripts": {
  "bundle": "rollup -c"
}
```

마무리로 `tsconfig.json` 파일 `compilerOptions` 항목에서 `module` 값을 `ES2015`로 변경합니다.

```javascript
"compilerOptions": {
  "target": "es5",
  "module": "ES2015",
  ...
}
```

준비를 마쳤으니 명령을 실행해 모듈 번들링을 수행해봅시다. `package.json`에 등록한 NPM Script 명령을 실행합니다. 앞서 다룬 절차에서 오류가 없었다면 정상적으로 번들링이 수행될 것입니다. 오류가 발생한다면 메시지를 읽고, 문제를 해결해보세요.

```bash
$ npm run bundle

> lecture-typescript@1.0.0 bundle /Users/yamoo9/Desktop/TypeScript
> rollup -c


./module/app.ts → ./module/bundle.js...
created ./module/bundle.js in 1.3s
```

## 번들링 수행 결과

번들링 수행 결과로 생성된 `bundle.js` 코드를 살펴보면 군더더기 없는 매우 깔끔한 결과를 도출됩니다. 이제 HTML 문서에서 불러와 사용하더라도 아무런 문제가 발생하지 않을 것입니다.

번들링 코드:

```javascript
// bundle.js

(function () {
  'use strict';

  function el(selector, context) {
      if (context === void 0) { context = document; }
      return context.querySelector(selector);
  }
  function els(selector, context) {
      if (context === void 0) { context = document; }
      return context.querySelectorAll(selector);
  }
  var Dom = { el: el, els: els };

  function on(el, type, handler, is_capture) {
      if (is_capture === void 0) { is_capture = false; }
      el.addEventListener(type, handler, is_capture);
  }

  on(document, 'click', function (e) { return Dom.el('body').style.background = '#912f03'; });

}());
```

