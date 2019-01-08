# stylelint

一个强大的现代 css 检测器，可以让你在样式表中遵循一致的约定和避免错误。

------

官方文档：[https://stylelint.io/](https://stylelint.io/)
中文文档：[http://stylelint.cn/](http://stylelint.cn/)

## 安装和配置

1、vscode 插件安装

[stylelint](https://marketplace.visualstudio.com/items?itemName=shinnn.stylelint)

2、vscode 设置

```json
{
    "css.validate": false,
    "scss.validate": false,
    "less.validate": false,
    "stylelint.configOverrides": {
        "ignoreFiles": ["dist/**/*", "/**/*.md", "/**/*.js"]
    }
}
```

3、node 安装

```bash
npm install stylelint stylelint-scss --save-dev
```

4、stylelint 配置文件

在项目根目录中，新建 `.stylelintrc.js`

```javascript
module.exports = {v
    plugins: ['stylelint-scss'],
    ignoreFiles: ['dist/**/*'],
    rules: {
        'at-rule-blacklist': null, // 指定一个禁止使用的 @ 规则的黑名单
        'at-rule-empty-line-before': ['always', {except: ['inside-block'], ignoreAtRules: ['import']}], // 要求或禁止在 @ 规则之前有空行
        'at-rule-name-case': 'lower', // 指定 @ 规则名称的大小写
        'at-rule-name-newline-after': 'always-multi-line', // 要求在 @ 规则之后有一个换行符
        'at-rule-name-space-after': 'always', // 要求在 @ 规则之后有一个空格
        'at-rule-no-unknown': null, // 禁止使用未知的 @ 规则
        'at-rule-no-vendor-prefix': true, // 禁止 @ 规则使用浏览器引擎前缀
        'at-rule-semicolon-newline-after': 'always', // 要求在 @ 规则的分号之后有一个换行符
        'at-rule-semicolon-space-before': 'never', // 要求在 @ 规则的分号之前有一个空格
        'at-rule-whitelist': null, // 指定一个允许使用的 @ 规则的白名单
        'block-closing-brace-empty-line-before': 'never', // 要求或禁止在闭括号之前有空行
        'block-closing-brace-newline-after': 'always', // 在闭括号之后要求有一个换行符或禁止有空白
        'block-closing-brace-newline-before': 'always-multi-line', // 在闭括号之前要求有一个换行符或禁止有空白
        'block-closing-brace-space-after': null, // 在闭括号之后要求有一个空格或禁止有空白
        'block-closing-brace-space-before': null, // 在闭括号之前要求有一个空格或禁止有空白
        'block-no-empty': true, // 禁止出现空块
        'block-opening-brace-newline-after': 'always-multi-line', // 在开括号之后要求有一个换行符
        'block-opening-brace-newline-before': null, // 在括开号之前要求有一个换行符或禁止有空白
        'block-opening-brace-space-after': 'never-single-line', // 在开括号之后要求有一个空格或禁止有空白
        'block-opening-brace-space-before': 'always', // 在开括号之前要求有一个空格或禁止有空白
        'color-hex-case': 'lower', // 指定十六进制颜色大小写
        'color-hex-length': 'short', // 指定十六进制颜色是否使用缩写
        'color-named': 'never', // 要求 (可能的情况下) 或 禁止使用命名的颜色
        'color-no-hex': null, // 禁止使用十六进制颜色
        'color-no-invalid-hex': true, // 禁止使用无效的十六进制颜色
        'comment-empty-line-before': null, // 要求或禁止在注释之前有空行
        'comment-no-empty': true, // 禁止空注释
        'comment-whitespace-inside': null, // 要求或禁止在注释标签内有空白
        'comment-word-blacklist': null, // 指定一个不允许出现在注释中的单词的黑名单
        'custom-media-pattern': null, // 指定一个自定义媒体查询名称的匹配模式
        'custom-property-empty-line-before': null, // 要求或禁止在自定义属性之前有一行空行
        'custom-property-pattern': null, // 为自定义属性指定一个匹配模式
        'declaration-bang-space-after': 'never', // 在感叹号之后要求有一个空格或禁止有空白
        'declaration-bang-space-before': 'always', // 在感叹号之前要求有一个空格或禁止有空白
        'declaration-block-no-duplicate-properties': true, // 在声明的块中中禁止出现重复的属性
        'declaration-block-no-redundant-longhand-properties': true, // 禁止使用可以缩写却不缩写的属性
        'declaration-block-no-shorthand-property-overrides': true, // 禁止缩写属性覆盖相关普通写法属性
        'declaration-block-semicolon-newline-after': 'always', // 在声明块的分号之后要求有一个换行符或禁止有空白
        'declaration-block-semicolon-newline-before': 'never-multi-line', // 在声明块的分号之前要求有一个换行符或禁止有空白
        'declaration-block-semicolon-space-after': 'always-single-line', // 在声明块的分号之后要求有一个空格或禁止有空白
        'declaration-block-semicolon-space-before': 'never', // 在声明块的分号之前要求有一个空格或禁止有空白
        'declaration-block-single-line-max-declarations': 1, // 限制单行声明块中声明的数量
        'declaration-block-trailing-semicolon': null, // 要求或禁止在声明块中使用拖尾分号
        'declaration-colon-newline-after': 'always-multi-line', // 在冒号之后要求有一个换行符或禁止有空白
        'declaration-colon-space-after': 'always-single-line', // 在冒号之后要求有一个空格或禁止有空白
        'declaration-colon-space-before': 'never', // 在冒号之前要求有一个空格或禁止有空白
        'declaration-empty-line-before': 'never', // 要求或禁止在声明语句之前有空行
        'declaration-no-important': null, // 禁止在声明中使用 !important
        'declaration-property-unit-blacklist': null, // 指定一个在声明中禁止使用的属性和单位的黑名单
        'declaration-property-unit-whitelist': null, // 指定一个在声明中允许使用的属性和单位的白名单
        'declaration-property-value-blacklist': null, // 指定一个在声明中禁止使用的属性和值的黑名单
        'declaration-property-value-whitelist': null, // 指定一个在声明中允许使用的属性和值的白名单
        'font-family-name-quotes': 'always-where-recommended', // 指定字体名称是否需要使用引号引起来
        'font-family-no-duplicate-names': true, // 禁止使用重复的字体名称
        'font-family-no-missing-generic-family-keyword': true, // 禁止没有一般字体，比如 sans-serif，serif
        'font-weight-notation': 'named-where-possible', // 要求使用数字或命名的 (可能的情况下) font-weight 值
        'function-blacklist': null, // 指定一个禁用的函数的黑名单，比如 rgba scale 等等
        'function-calc-no-unspaced-operator': true, // 禁止在 calc 函数内使用不加空格的操作符，比如 calc(1px+2px)
        'function-comma-newline-after': 'always-multi-line', // 在函数的逗号之后要求有一个换行符或禁止有空白
        'function-comma-newline-before': 'never-multi-line', // 在函数的逗号之前要求有一个换行符或禁止有空白
        'function-comma-space-after': 'always-single-line', // 在函数的逗号之后要求有一个空格或禁止有空白
        'function-comma-space-before': 'never-single-line', // 在函数的逗号之前要求有一个空格或禁止有空白
        'function-linear-gradient-no-nonstandard-direction': true, // 根据标准语法，禁止 linear-gradient() 中无效的方向值
        'function-max-empty-lines': 0, // 限制函数中相邻的空行数量
        'function-name-case': 'lower', // 指定函数名称的大小写
        'function-parentheses-newline-inside': 'never-multi-line', // 在函数的括号内要求有一个换行符或禁止有空白
        'function-parentheses-space-inside': 'never', // 在函数的括号内要有一个空格或禁止有空白
        'function-url-no-scheme-relative': null, // 禁止使用相对协议的链接
        'function-url-quotes': 'never', // 要求或禁止 url 使用引号
        'function-url-scheme-blacklist': null, // 指定一个禁止的 url 协议的黑名单
        'function-url-scheme-whitelist': null, // 指定一个允许的 url 协议的白名单
        'function-whitelist': null, // 指定一个允许的函数的白名单
        'function-whitespace-after': 'always', // 要求或禁止在函数之后有空白
        'keyframe-declaration-no-important': true, // 禁止在 keyframe 声明中使用 !important
        // 'keyframes-name-pattern': null, // 为关键帧指定一个匹配模式
        'length-zero-no-unit': true, // 长度为 0 时，禁止使用单位
        // 'linebreaks': 'unix', // 指定 unix 或 windows 换行符
        'max-empty-lines': 1, // 限制相邻空行的数量
        'max-line-length': null, // 限制单行的长度
        'max-nesting-depth': 5, // 限制允许嵌套的深度
        'media-feature-colon-space-after': 'always', // 在 media 特性中的冒号之后要求有一个空格或禁止有空白
        'media-feature-colon-space-before': 'never', // 在 media 特性中的冒号之前要求有一个空格或禁止有空白
        'media-feature-name-blacklist': null, // 指定禁止使用的 media 特性名称的黑名单
        'media-feature-name-case': 'lower', // 指定 media 特性名称的大小写
        'media-feature-name-no-unknown': true, // 禁止使用未知的 media 特性名称
        'media-feature-name-no-vendor-prefix': true, // 禁止 media 特性名称带有浏览器引擎前缀
        'media-feature-name-whitelist': null, // 指定允许使用的 media 特性名称的白名单
        'media-feature-parentheses-space-inside': 'never', // 在 media 特性的括号内要求有一个空格或禁止有空白
        'media-feature-range-operator-space-after': 'always', // 在 media 特性的范围操作符之后要求有一个空格或禁止有空白
        'media-feature-range-operator-space-before': 'always', // 在 media 特性的范围操作符之前要求有一个空格或禁止有空白
        'media-query-list-comma-newline-after': 'always-multi-line', // 在媒体查询的逗号之后要求有一个换行符或禁止有空白
        'media-query-list-comma-newline-before': 'never-multi-line', // 在媒体查询的逗号之前要求有一个换行符或禁止有空白
        'media-query-list-comma-space-after': 'always-single-line', // 在媒体查询的逗号之后要求有一个空格或禁止有空白
        'media-query-list-comma-space-before': 'never-single-line', // 在媒体查询的逗号之前要求有一个空格或禁止有空白
        'no-descending-specificity': null, // 禁止低优先级的选择器出现在高优先级的选择器之后
        'no-duplicate-at-import-rules': true, // 禁止重复的 @import
        'no-duplicate-selectors': true, // 在一个样式表中禁止出现重复的选择器
        // 'no-empty-first-line': true, // 禁止第一行为空
        'no-empty-source': true, // 禁止空源
        'no-eol-whitespace': [true, {ignore: ['empty-lines']}], // 禁止行尾空白
        'no-extra-semicolons': true, // 禁止多余的分号
        'no-invalid-double-slash-comments': null, // 禁用 CSS 不支持的而且可能会导致意外结果的双斜线注释 (//...)
        'no-missing-end-of-source-newline': null, // 禁止缺少文件末尾的换行符
        'no-unknown-animations': true, // 禁止动画名称与 @keyframes 声明不符
        'number-leading-zero': 'never', // 要求或禁止小于 1 的小数的前导 0
        'number-max-precision': 4, // 限制小数位数
        'number-no-trailing-zeros': true, // 禁止数字中的拖尾 0
        'property-blacklist': null, // 指定一个禁止使用的属性的黑名单
        'property-case': 'lower', // 指定属性的大小写
        'property-no-unknown': true, // 禁止使用未知属性
        'property-no-vendor-prefix':[true, {ignoreProperties: ['background-clip']}], // 禁止属性使用浏览器引擎前缀
        'property-whitelist': null, // 指定一个允许使用的属性的白名单
        'rule-empty-line-before': ['always', {except: ['first-nested', 'inside-block-and-after-rule', 'inside-block']}], // 允许或禁止规则前空行
        'selector-attribute-brackets-space-inside': 'never', // 在属性选择器的方括号内要求有空格或禁止有空白
        'selector-attribute-operator-blacklist': null, // 指定一个禁止使用的属性操作符的黑名单
        'selector-attribute-operator-space-after': 'never', // 在属性选择器的操作符之后要求有一个空格或禁止有空白
        'selector-attribute-operator-space-before': 'never', // 在属性选择器的操作符之前要求有一个空格或禁止有空白
        'selector-attribute-operator-whitelist': null, // 指定允许使用的属性操作符的白名单
        'selector-attribute-quotes': 'always', // 要求或禁止属性值使用引号
        'selector-class-pattern': null, // 为类选择器指定一个匹配模式
        'selector-combinator-blacklist': null, // 指定一个禁止使用的关系选择符的黑名单
        'selector-combinator-space-after': 'always', // 在关系选择符之后要求有一个空格或禁止有空白
        'selector-combinator-space-before': 'always', // 在关系选择符之前要求有一个空格或禁止有空白
        'selector-combinator-whitelist': null, // 指定允许使用的关系选择符的白名单
        'selector-descendant-combinator-no-non-space': true, // 禁止包含选择符出现非空格字符
        'selector-id-pattern': null, // 指定一个 id 选择器的匹配模式
        'selector-list-comma-newline-after': 'always-multi-line', // 要求选择器列表的逗号之后有一个换行符或禁止在逗号之后有空白
        'selector-list-comma-newline-before': 'never-multi-line', // 要求选择器列表的逗号之前有一个换行符或禁止在逗号之前有空白
        'selector-list-comma-space-after': 'always-single-line', // 要求在选择器列表的逗号之后有一个空格，或禁止有空白
        'selector-list-comma-space-before': 'never-single-line', // 要求在选择器列表的逗号之前有一个空格，或禁止有空白
        'selector-max-attribute': 5, // 限制属性选择器的数量
        'selector-max-class': 5, // 限制类选择器的数量，比如按钮的状态 button.active.disabled.selected.hover
        'selector-max-combinators': 5, // 限制关系选择器的数量
        'selector-max-compound-selectors': 5, // 限制复合选择器的数量
        'selector-max-empty-lines': 0, // 限制选择器中相邻空行数量
        'selector-max-id': 1, // 限制 id 选择器的数量
        // 'selector-max-pseudo-class': 2, // 限制伪类选择器的数量，比如 a:first-child:hover
        'selector-max-specificity': null, // 限制选择器的优先级，格式为 "id,class,type"，依据W3C selector spec（https://drafts.csswg.org/selectors/#specificity-rules）
        'selector-max-type': 5, // 限制类型选择器的数量，比如 div a span
        'selector-max-universal': 1, // 限制通配符选择器的数量 body *
        'selector-nested-pattern': null, // 指定一个嵌套选择器的匹配模式
        'selector-no-qualifying-type': [true, {ignore: ['attribute', 'class']}], // 禁止使用类型对选择器进行限制
        'selector-no-vendor-prefix': true, // 禁止使用浏览器引擎前缀
        'selector-pseudo-class-blacklist': null, // 指定一个禁止使用的伪类选择器的黑名单
        'selector-pseudo-class-case': 'lower', // 指定伪类选择器的大小写
        'selector-pseudo-class-no-unknown': true, // 禁止使用未知的伪类选择器
        'selector-pseudo-class-parentheses-space-inside': 'never', // 在伪类选择器的括号内要求使用一个空格或禁止有空白
        'selector-pseudo-class-whitelist': null, // 指定一个允许使用的伪类选择器的白名单
        'selector-pseudo-element-blacklist': null, // 指定一个禁止使用的伪元素的黑名单
        'selector-pseudo-element-case': 'lower', // 指定伪元素的大小写
        'selector-pseudo-element-colon-notation': 'single', // 指定伪元素使用单冒号还是双冒号
        'selector-pseudo-element-no-unknown': true, // 禁止使用未知的伪元素
        'selector-pseudo-element-whitelist': null, // 指定一个允许使用的伪元素的白名单
        'selector-type-case': 'lower', // 指定类型选择器的大小写
        'selector-type-no-unknown': true, // 禁用未知的类型选择器
        'shorthand-property-no-redundant-values': true, // 禁止在简写属性中使用冗余值
        'string-no-newline': true, // 禁止在字符串中使用（非转义的）换行符
        'string-quotes': 'single', // 指定字符串使用单引号还是双引号
        'time-min-milliseconds': null, // 指定最低的毫秒数
        'unit-blacklist': null, // 指定一个禁止使用的单位的黑名单
        'unit-case': 'lower', // 指定单位的大小写
        'unit-no-unknown': true, // 禁止使用未知单位
        'unit-whitelist': null, // 指定一个所允许的单位的白名单
        'value-keyword-case': 'lower', // 指定关键字的值的大小写
        'value-list-comma-newline-after': 'always-multi-line', // 在值列表的逗号之后要求有一个换行符或禁止有空白
        'value-list-comma-newline-before': 'never-multi-line', // 在值列表的逗号之前要求有一个换行符或禁止有空白
        'value-list-comma-space-after': 'always-single-line', // 在值列表的逗号之后要求有一个空格或禁止有空白
        'value-list-comma-space-before': 'never-single-line', // 在值列表的逗号之前要求有一个空格或禁止有空白
        'value-list-max-empty-lines': 0, // 限制值列表中相邻空行数量
        'value-no-vendor-prefix': true, // 禁止给值添加浏览器引擎前缀
        'indentation': 4, // 指定缩进
        'scss/at-else-closing-brace-newline-after': null, // 要求或禁止 @else 闭括号后换行
        'scss/at-else-closing-brace-space-after': null, // @else 闭括号后要求一个空格或禁止空白
        'scss/at-else-empty-line-before': 'never', // 在 @else 之前需要一个空行或禁止空行
        'scss/at-else-if-parentheses-space-before': 'always', // @else if 括号前需要一个空格或禁止空格
        'scss/at-extend-no-missing-placeholder': true, // 禁止使用缺少占位符（%placeholder）的 @extend
        'scss/at-function-named-arguments': null, // 调用 @function 需要命名参数，比如 @include animate($duration: 2s);
        'scss/at-function-parentheses-space-before': 'never', // @function 括号之前需要或禁止一个空格
        'scss/at-function-pattern': null, // 定制 @function 命名规则
        'scss/at-if-closing-brace-newline-after': null, // @if 闭大括号之后需要或禁止换行
        'scss/at-if-closing-brace-space-after': null, // @if 闭大括号之后需要或禁止空格
        'scss/at-import-no-partial-leading-underscore': null, // @import 禁止前置下划线的名字
        'scss/at-import-partial-extension-blacklist': null, // 指定一个禁止 @import 文件名称扩展名的黑名单
        'scss/at-import-partial-extension-whitelist': null, // 指定一个允许 @import 文件名称扩展名的白名单
        'scss/at-mixin-argumentless-call-parentheses': 'always', // 调用 @mixin，如果不传参数，需要或禁止加上圆括号
        'scss/at-mixin-named-arguments': null, // 调用 @mixin 需要命名参数，比如 @include animate(2s);
        'scss/at-mixin-parentheses-space-before': 'never', // @mixin 括号之前需要或禁止一个空格
        'scss/at-mixin-pattern': null, // 定制 @mixin 命名规则
        'scss/at-rule-no-unknown': true, // 禁止使用未知的 @ 规则，用于替换 at-rule-no-unknown
        'scss/declaration-nested-properties': 'never', // 允许或禁止属性值的嵌套
        'scss/declaration-nested-properties-no-divided-groups': true, // 禁止嵌套的属性，相同的名称分成多个
        'scss/dollar-variable-colon-newline-after': 'always-multi-line', // $ 变量声明冒号之后需要换行
        'scss/dollar-variable-colon-space-after': 'always-single-line', // $ 变量声明冒号之后需要或禁止空格
        'scss/dollar-variable-colon-space-before': 'never', // $ 变量声明冒号之前需要或禁止空格
        'scss/dollar-variable-default': null, // $ 变量声明需要 !default 标识
        'scss/dollar-variable-empty-line-before': ['always', {except: ['first-nested', 'after-comment', 'after-dollar-variable']}], // $ 变量声明之前允许或禁止空行
        'scss/dollar-variable-no-missing-interpolation': true, // 如果 sass 变量是字符串，需要以插值形式（#{}）引用
        'scss/dollar-variable-pattern': null, // 定制 $ 变量命名规则
        'scss/double-slash-comment-empty-line-before': null, // 双斜线注释之前允许或禁止空行
        'scss/double-slash-comment-inline': null, // 双斜线注释是否内联
        'scss/double-slash-comment-whitespace-inside': null, // 双斜线注释的 // 后允许或禁止空格
        'scss/media-feature-value-dollar-variable': null, // 允许或禁止 @media 括号内的值为 $ 变量
        'scss/no-dollar-variables': null, // 禁止在样式表中使用 $ 变量
        'scss/no-duplicate-dollar-variables': [true, {ignoreInsideAtRules: ['if', 'else', 'for', 'each', 'while', 'mixin', 'function', 'media', 'keyframes']}], // 禁止重复的 $ 变量名
        'scss/operator-no-newline-after': true, // sass 运算符后禁止换行
        'scss/operator-no-newline-before': true, // sass 运算符前禁止换行
        'scss/operator-no-unspaced': null, // sass 运算符前后需要有空格
        'scss/partial-no-import': null, // Disallow non-CSS @imports in partial files（禁止 @import 引入局部文件）
        'scss/percent-placeholder-pattern': null, // 定制 % 占位符命名规则
        'scss/selector-no-redundant-nesting-selector': true, // 禁止多余的嵌套选择器(&)
    }
};
```