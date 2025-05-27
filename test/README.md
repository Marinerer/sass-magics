# unit test

> `sass-true` + `jest`


## sass-true

[docs](https://www.oddbird.net/true/docs/)

- `true.assert()` 定义 CSS 输出断言, 它是一个包装器mixin，且包含一个 `output()` 块和一个 `expect()` 块作为嵌套内容。
- `true.output(bool)` 块会生成一个 `.test-output` 样式块，用于包裹测试的样式。
- `true.expect(bool)` 块会生成一个 `.test-output` 样式块，用于包裹测试的期望样式。
- 使用 `output(false)` 和 `expect(false)` 可以 禁用 sass-true 默认的 .test-output 包裹类


### 返回值

- `assert-true`, 同 `is-truthy`
- `assert-false`, 同 `is-falsy`
- `assert-unequal` 同 `is-equal`
- `assert-unequal`, 同`not-equal`

```scss
@include true.test('Non-empty strings are truthy') {
  @include true.assert-true('Hello World');
}

@include true.test('Empty strings are falsey') {
  @include true.assert-false('');
}

@include true.test('Division works as expected in Sass') {
  @include true.assert-equal(math.div(8, 2), 4);
}

@include true.test('Strings and numbers are not the same') {
  @include true.assert-unequal(1em, '1em');
}
```


### 输出
- `assert`
  - `output`
  - `expect`

```scss
@include true.assert('desciprtion') {
  @include true.output {
    width: 14em + 2;
  }
  @include true.expect {
    width: 16em;
  }
}
```