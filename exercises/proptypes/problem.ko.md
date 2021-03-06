넘긴 값의 타입을 제약해 봅시다.

컴포넌트에 넘겨진 데이터는 일반 컴포넌트(버튼, 폼 필드 등)에서 만들고 의존하는 `this.props`를 통해 `render()`에서 접근할 수 있습니다.

이는 컴포넌트가 재대로 사용되고 있는지 확인하는데 도움이 됩니다.

제약은 `propTypes`을 지정해 할 수 있습니다. 개발 모드에서 `React.PropTypes`는 재대로된 데이터를 받았는지 확인하는 벨리데이터를 범위를 명시합니다.

```
React.createClass({
  propTypes: {
    name:   React.PropTypes.string.isRequired,
    id:     React.PropTypes.number.isRequired,
    width:  React.PropTypes.number.isRequired,
    height: React.PropTypes.number.isRequired,
    alt:    React.PropTypes.string
  },
  /* ... */
```
props에 잘못된 값이 들어온 경우에는 JavaScript 콘솔에 경고가 출력됩니다.


# 문제
---

`index.jsx`의 `Todo`를 다음과 같이 수정해주세요.
새로운 파일을 작성하셔도 됩니다.


```
var React = require('react');

var TodoBox = React.createClass({
  // 생략
});

var TodoList = React.createClass({
  // 생략
});

var Todo = React.createClass({
  propTypes: {
    title: React.PropTypes.number.isRequired
  },
  render: function() {
    return (
      <tr>
        <td style={{border: "1px solid black"}}>{this.props.title}</td>
        <td style={{border: "1px solid black"}}>{this.props.children}</td>
      </tr>
    );
  }
});




var TodoForm = React.createClass({
  // 생략
});

module.exports = TodoBox;
```

`index.jsx`를 수정한 다음, `learnyoureact run program.js`를 실행해 주세요.
React.js가 콘솔에 `Warning`을 출력하는 것을 볼 수 있습니다.
그 내용을 읽어, `Warning`이 나오지 않도록 `Todo`를 수정해 주세요.
`propTypes`는 반드시 사용하세요.


코드를 고쳤으면, `node program.js`를 실행해 `http://localhost:3000`으로 들어가, 실제로 HTML이 출력되는 것을 확인하세요.

재사용가능한 컴포넌트: https://facebook.github.io/react/docs/reusable-components-ko-KR.html

그런 다음, `learnyoureact verify program.js`를 실행하세요.
