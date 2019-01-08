# eslint

ESLint 是在 ECMAScript/JavaScript 代码中识别和报告模式匹配的工具，它的目标是保证代码的一致性和避免错误。

------

官方文档：[https://eslint.org/](https://eslint.org/)
中文文档：[http://eslint.cn/](http://eslint.cn/)

## 安装和配置

1、vscode 插件安装

[eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

2、node 安装

```bash
npm install eslint eslint-plugin-react --save-dev
```

3、eslint 配置文件 `.eslintrc.js`

```javascript
module.exports = {
    parser: 'babel-eslint',
    parserOptions: {
        ecmaVersion: 7,
        sourceType: 'module',
        ecmaFeatures: {
            jsx: true,
            legacyDecorators: true
        }
    },
    env: {
        browser: true,
        node: true,
        commonjs: true,
        es6: true,
        jquery: true
    },
    root: true, // 以当前目录为根目录，不再向上查找 .eslintrc.js
    globals: {
        Backbone: true,
        _: true,
        define: true
    },
    plugins: [
        'react'
    ],
    rules: {
        // 可能的错误
        // 这些规则与 JavaScript 代码中可能的语法错误或逻辑错误有关
        'for-direction': 2, // 禁止 for 循环出现方向错误的循环，比如 for (i = 0; i < 10; i--)
        'getter-return': 0, // 强制在 getter 属性中出现一个 return 语句
        'no-await-in-loop': 0, // 禁止将 await 写在循环里，因为这样就无法同时发送多个异步请求了
        'no-compare-neg-zero': 2, // 禁止与 -0 进行比较
        'no-cond-assign': [2, 'except-parens'], // 禁止在条件语句中出现赋值操作符，除非这个赋值语句被括号包起来了
        'no-console': 0, // console 很常用，不需要禁用
        'no-constant-condition': [2, {checkLoops: false}], // 禁止在条件中使用常量表达式，但允许在循环中使用常量表达式
        'no-control-regex': 0, // 禁止在正则表达式中出现 Ctrl 键的 ASCII 表示，即禁止使用 /\x1f/，日常几乎不会遇到这种场景
        'no-debugger': 0, // 禁止使用 debugger
        'no-dupe-args': 2, // 禁止在 function 定义中出现重复的参数
        'no-dupe-keys': 2, // 禁止在对象字面量中出现重复的键
        'no-duplicate-case': 2, // 禁止重复 case 标签
        'no-empty': [2, {allowEmptyCatch: true}], // 禁止出现空代码块，允许 catch 为空代码块
        'no-empty-character-class': 0, // 禁止在正则表达式中出现空字符集
        'no-ex-assign': 2, // 禁止将 catch 的第一个参数 error 重新赋值
        'no-extra-boolean-cast': 0, // 禁止不必要的布尔类型转换
        'no-extra-parens': 0, // 禁止不必要的圆括号
        'no-extra-semi': 2, // 禁用不必要的分号
        'no-func-assign': 2, // 禁止对 function 声明重新赋值
        'no-inner-declarations': 0, // 禁止 function 和 var 声明出现在嵌套的语句块中
        'no-invalid-regexp': 0, // 禁止 RegExp 构造函数中存在无效的正则表达式字符串
        'no-irregular-whitespace': [2, { // 禁止使用特殊空白符（比如全角空格）
            skipStrings: true, // 允许在字符串字面量中出现任何空白字符
            skipComments: false, // 允许在注释中出现任何空白字符
            skipRegExps: true, // 允许在正则表达式中出现任何空白字符
            skipTemplates: true // 允许在模板字面量中出现任何空白字符
        }],
        'no-obj-calls': 2, // 禁止将 Math, JSON 或 Reflect 直接作为函数调用
        'no-prototype-builtins': 0, // 禁止直接使用 Object.prototypes 的内置属性，不过 hasOwnProperty 比较常用
        'no-regex-spaces': 0, // 禁止正则表达式字面量中出现多个空格
        'no-sparse-arrays': 0, // 禁用稀疏数组，比如 var items = [,,];
        'no-template-curly-in-string': 2, // 禁止在普通字符串中出现模版字符串里的变量形式，比如 'Hello ${name}!'
        'no-unexpected-multiline': 2, // 禁止使用令人困惑的多行表达式
        'no-unreachable': 2, // 禁止在 return, throw, break 或 continue 之后还有代码
        'no-unsafe-finally': 2, // 禁止在 finally 中出现 return, throw, break 或 continue
        'no-unsafe-negation': 0, // 禁止对关系运算符的左操作数使用否定操作符，比如 if (!key in object)
        'use-isnan': 2, // 必须使用 isNaN(foo) 而不是 foo === NaN
        'valid-jsdoc': 0, // 强制使用有效的 JSDoc 注释
        'valid-typeof': 2, // 强制 typeof 表达式与有效的字符串进行比较
        // 最佳实践
        // 这些规则是关于最佳实践的，帮助你避免一些问题
        'accessor-pairs': 0, // setter 必须有对应的 getter，getter 可以没有对应的 setter
        'array-callback-return': 0, // 数组的方法除了 forEach 之外，回调函数必须有返回值
        'block-scoped-var': 2, // 将 var 定义的变量视为块作用域，禁止在块外使用
        'class-methods-use-this': 0, // 在类的非静态方法中，必须存在对 this 的引用，太严格了
        'complexity': 0, // 禁止函数的循环复杂度超过 20
        'consistent-return': 0, // 禁止函数在不同分支返回不同类型的值
        'curly': [2, 'multi-line', 'consistent'], // 要求遵循大括号约定，允许在单行中省略大括号，而if、else if、else、for、while 和 do，在其他使用中依然会强制使用大括号
        'default-case': 2, // 要求 Switch 语句中有 Default 分支
        'dot-location': [2, 'property'], // 链式调用的时候，点号必须放在第二行开头处，禁止放在第一行结尾处
        'dot-notation': 2, // 禁止出现 foo['bar']，必须写成 foo.bar
        'eqeqeq': [1, 'always', {null: 'ignore'}], // 必须使用 === 或 !==，禁止使用 == 或 !=，与 null 比较时除外
        'guard-for-in': 0, // 要求 for-in 循环中有一个 if 语句
        'no-alert': 0, // 禁用 alert、confirm 和 prompt
        'no-caller': 2, // 禁止使用 caller 或 callee
        'no-case-declarations': 0, // switch 的 case 内有变量定义的时候，必须使用大括号将 case 内变成一个代码块
        'no-div-regex': 0, // 禁止使用看起来像除法的正则表达式，有代码高亮的话，在阅读这种代码时，也完全不会产生歧义或理解上的困难
        'no-else-return': 0, // 禁止 if 语句中 return 语句之后有 else 块
        'no-empty-function': 2, // 禁止出现空函数
        'no-empty-pattern': 2, // 禁止解构中出现空 {} 或 []
        'no-eq-null': 0, // 禁止与 null 进行比较
        'no-eval': 2, // 禁用 eval()
        'no-extend-native': 0, // 禁止扩展原生类型
        'no-extra-bind': 0, // 禁止不必要的 .bind() 调用
        'no-extra-label': 2, // 禁止出现没必要的 label
        'no-fallthrough': 2, // switch 的 case 内必须有 break, return 或 throw
        'no-floating-decimal': 0, // 表示小数时，禁止省略 0，比如 .5
        'no-global-assign': 2, // 禁止对原生对象或只读的全局对象进行赋值
        'no-implicit-coercion': 0, // 禁止使用较短的符号实现类型转换，比如 !!, ~
        'no-implicit-globals': 0, // 禁止在全局作用域下定义变量或申明函数
        'no-implied-eval': 0, // 禁止在 setTimeout 或 setInterval 中传入字符串，比如 setTimeout('alert('Hi!')', 100);
        'no-invalid-this': 0, // 禁止 this 关键字出现在类和类对象之外
        'no-iterator': 2, // 禁止使用 __iterator__
        'no-labels': 2, // 禁止使用 label
        'no-lone-blocks': 0, // 禁用不必要的嵌套块
        'no-loop-func': 0, // 禁止在循环内的函数中出现循环体条件语句中定义的变量
        'no-magic-numbers': 0, // 禁用魔术数字
        'no-multi-spaces': [2, { // 禁止出现多个空格
            exceptions: {
                Property: false
            },
            ignoreEOLComments: true
        }],
        'no-multi-str': 2, // 禁止使用 \ 来换行字符串
        'no-new': 0, // 禁止直接 new 一个类而不赋值
        'no-new-func': 0, // 禁止使用 new Function
        'no-new-wrappers': 2, // 禁止使用 new 来生成 String, Number 或 Boolean
        'no-octal': 2, // 禁止使用 0 开头的数字表示八进制数
        'no-octal-escape': 2, // 禁止使用八进制的转义符
        'no-param-reassign': 0, // 禁止对函数的参数重新赋值
        'no-proto': 0, // 禁止使用 __proto__，使用 getPrototypeOf 方法替代
        'no-redeclare': 2, // 禁止重复定义变量
        'no-restricted-properties': 0, // 禁止使用指定的对象属性
        'no-return-assign': [2, 'always'], // 禁止在 return 语句里赋值
        'no-return-await': 0, // 禁止在 return 语句里使用 await
        'no-script-url': 0, // 禁止出现 location.href = 'javascript:void(0)';
        'no-self-assign': 2, // 禁止自身赋值
        'no-self-compare': 2, // 禁止自身比较
        'no-sequences': 0, // 禁止使用逗号操作符
        'no-throw-literal': 0, // 禁止 throw 字面量，必须 throw 一个 Error 对象
        'no-unmodified-loop-condition': 0, // 循环内必须对循环条件的变量有修改
        'no-unused-expressions': 0, // 禁止无用的表达式
        'no-unused-labels': 2, // 禁止出现没用的 label
        'no-useless-call': 0, // 禁止出现没必要的 call 或 apply
        'no-useless-concat': 2, // 禁止出现没必要的字符串连接
        'no-useless-escape': 0, // 禁止出现没必要的转义
        'no-useless-return': 0, // 禁止没必要的 return
        'no-void': 2, // 禁止使用 void
        'no-warning-comments': 0, // 禁止注释中出现 TODO 和 FIXME
        'no-with': 0, // 禁止使用 with
        'prefer-promise-reject-errors': 0, // Promise 的 reject 中必须传入 Error 对象，而不是字面量
        'radix': 0, // parseInt 必须传入第二个参数
        'require-await': 0, // 禁止使用不带 await 表达式的 async 函数
        'vars-on-top': 0, // 要求将变量声明放在它们作用域的顶部
        'wrap-iife': [2, 'inside', {functionPrototypeMethods: true}], // 立即执行的函数必须符合如下格式 (function () { alert('Hello') })()
        'yoda': 0, // 要求或者禁止 Yoda 条件，比如 if (foo === 5) 而不是 if (5 === foo)
        // 严格模式
        // 该规则与使用严格模式和严格模式指令有关
        'strict': 0, // 要求或禁止使用严格模式指令
        // 变量
        // 这些规则与变量申明有关
        'init-declarations': 0, // 变量必须在定义的时候赋值
        'no-catch-shadow': 0, // 禁止 catch 的参数名与定义过的变量重复
        'no-delete-var': 0, // 禁止删除变量
        'no-label-var': 2, // 禁止 label 名称与定义过的变量重复
        'no-restricted-globals': 0, // 禁止使用指定的全局变量
        'no-shadow': 0, // 禁止变量名与上层作用域内的定义过的变量重复，很多时候函数的形参和传参是同名的
        'no-shadow-restricted-names': 2, // 禁止使用保留字作为变量名
        'no-undef': [2, {typeof: false}], // 禁止使用未定义的变量
        'no-undef-init': 2, // 禁止将 undefined 赋值给变量
        'no-undefined': 1, // 禁止对 undefined 重新赋值，可以通过 typeof 来判断该变量是否是 undefined
        'no-unused-vars': [1, { // 定义过的变量必须使用
            vars: 'all',
            args: 'none',
            caughtErrors: 'none',
            ignoreRestSiblings: true
        }],
        'no-use-before-define': [2, { // 变量必须先定义后使用
            functions: false,
            classes: false,
            variables: false
        }],
        // Node.js 和 CommonJS
        // 这些规则是关于 Node.js 或在浏览器中使用 CommonJS 的
        'callback-return': 0, // callback 之后必须立即 return
        'global-require': 0, // 强制在模块顶部调用 require()
        'handle-callback-err': 0, // 强制回调错误处理
        'no-buffer-constructor': 2, // 禁止直接使用 Buffer
        'no-mixed-requires': 0, // 禁止 require 调用与普通变量声明混合使用
        'no-new-require': 2, // 不允许 new require
        'no-path-concat': 2, // 禁止对 __dirname 或 __filename 使用字符串连接
        'no-process-env': 0, // 禁用 process.env
        'no-process-exit': 0, // 禁用 process.exit()
        'no-restricted-modules': 0, // 禁用通过 require 加载的指定模块
        'no-sync': 0, // 禁止使用同步方法
        // 风格问题
        // 这些规则与代码风格有关，所以是非常主观的
        'array-bracket-newline': 0, // 配置数组的中括号内前后的换行格式
        'array-bracket-spacing': [2, 'never'], //数组的括号内的前后禁止有空格
        'array-element-newline': 0, // 强制数组元素间出现换行
        'block-spacing': [2, 'never'], // 禁止或强制在代码块中开括号前和闭括号后有空格
        'brace-style': [2, '1tbs', {allowSingleLine: true}], // if 与 else 的大括号风格必须一致
        'camelcase': 0, // 要求使用骆驼拼写法
        'capitalized-comments': 0, // 注释的首字母必须大写
        'comma-dangle': 0, // 对象的最后一个属性末尾必须有逗号
        'comma-spacing': [2, { // 逗号前禁止有空格，逗号后必须要有空格
            'before': false,
            'after': true
        }],
        'comma-style': [2, 'last'], // 禁止在行首写逗号
        'computed-property-spacing': [2, 'never'], // 禁止在计算属性内使用空格
        'consistent-this': 0, // 限制 this 的别名
        'eol-last': 0, // 文件最后一行必须有一个空行
        'func-call-spacing': [2, 'never'], // 函数名和执行它的括号之间禁止有空格
        'func-name-matching': 0, // 函数赋值给变量的时候，函数名必须与变量名一致
        'func-names': 0, // 函数必须有名字
        'func-style': 0, // 强制 function 声明或表达式的一致性
        'function-paren-newline': 0, // 强制在函数括号内使用一致的换行
        'id-blacklist': 0, // 禁止使用指定的标识符
        'id-length': 0, // 限制变量名长度
        'id-match': 0, // 限制变量名必须匹配指定的正则表达式
        'implicit-arrow-linebreak': 0, // 强制隐式返回的箭头函数体的位置
        'indent': [2, 4, { // 一个缩进必须用四个空格替代
            SwitchCase: 1,
            ObjectExpression: 1,
            flatTernaryExpressions: true
        }],
        'jsx-quotes': [2, 'prefer-double'], // 强制在 jsx 属性中使用一致的单引号或双引号
        'key-spacing': [2, { // 对象字面量中冒号前面禁止有空格，后面必须有空格
            beforeColon: false,
            afterColon: true,
            mode: 'strict',
        }],
        'keyword-spacing': [2, { // 关键字前后必须有空格
            before: true,
            after: true
        }],
        'line-comment-position': 0, // 强制单行注释的位置
        'linebreak-style': 0, // 强制使用一致的换行符风格 LF 或 CRLF
        'lines-around-comment': 0, // 强制注释周围有空行
        'max-depth': 0, // 强制块语句的最大可嵌套深度
        'max-len': 0, // 强制行的最大长度，交给编辑器来做吧
        'max-lines': 0, // 强制文件的最大行数
        'max-nested-callbacks': [2, 5], // 强制回调函数最大嵌套深度
        'max-params': 0, // 限制函数定义中最大参数个数
        'max-statements': 0, // 限制函数块中的语句的最大数量
        'max-statements-per-line': 0, // 强制每一行中所允许的最大语句数量
        'multiline-comment-style': 0, // 强制对多行注释使用特定风格
        'multiline-ternary': 0, // 要求或禁止在三元操作数中间换行
        'new-cap': [2, { // 要求构造函数首字母大写
            newIsCap: true,
            capIsNew: false,
            properties: true
        }],
        'new-parens': 2, // 要求调用无参构造函数时带括号
        'newline-per-chained-call': 0, // 要求方法链中每个调用都有一个换行符
        'no-array-constructor': 0, // 禁止使用 Array 构造函数
        'no-bitwise': 0, // 禁止使用按位操作符
        'no-continue': 0, // 禁用 continue
        'no-inline-comments': 0, // 禁止使用内联注释
        'no-lonely-if': 0, // 禁止 if 语句作为唯一语句出现在 else 语句块中
        'no-mixed-operators': 0, // 禁止混合使用不同的操作符
        'no-mixed-spaces-and-tabs': 2, // 禁止使用 空格 和 tab 混合缩进
        'no-multi-assign': 0, // 禁止连续赋值，比如 a = b = c = 5
        'no-multiple-empty-lines': 0, // 不允许多个空行
        'no-negated-condition': 0, // 禁用否定表达式
        'no-nested-ternary': 0, // 禁止使用嵌套的三元表达式
        'no-new-object': 0, // 禁止使用 Object 构造函数
        'no-plusplus': 0, // 禁止使用一元操作符 ++ 和 --
        'no-restricted-syntax': 0, // 禁止使用特定的语法
        'no-tabs': 0, // 禁止使用 tabs
        'no-ternary': 0, // 禁止使用三元操作符
        'no-trailing-spaces': 2, // 禁止行尾有空格
        'no-underscore-dangle': 0, // 禁止变量名出现下划线
        'no-unneeded-ternary': 0, // 禁止可以表达为更简单结构的三元操作符
        'no-whitespace-before-property': 2, // 禁止属性前有空白
        'nonblock-statement-body-position': [2, 'beside', { // 禁止 if 后面不加大括号而写两行代码
            overrides: {
                while: 'below'
            }
        }],
        'object-curly-newline': [2, { // 强制在花括号内使用一致的换行符
            multiline: true,
            consistent: true
        }],
        'object-curly-spacing': [2, 'never', { // 强制在花括号中使用一致的空格
            arraysInObjects: false,
            objectsInObjects: false
        }],
        'object-property-newline': 0, // 强制将对象的属性放在不同的行上
        'one-var': 0, // 禁止变量申明时用逗号一次申明多个
        'one-var-declaration-per-line': 0, // 变量申明必须每行一个
        'operator-assignment': 0, // 要求或禁止尽可能地简化赋值操作
        'operator-linebreak': 0, // 强制操作符使用一致的换行符风格
        'padded-blocks': 0, // 要求或禁止块内填充
        'padding-line-between-statements': 0, // 要求或禁止在语句间填充空行
        'quote-props': 0, // 要求对象字面量属性名称使用引号
        'quotes': [2, 'single', { // 强制使用一致的反勾号、双引号或单引号
            avoidEscape: true,
            allowTemplateLiterals: true
        }],
        'require-jsdoc': 0, // 要求使用 jsdoc 注释
        'semi': [2, 'always', {omitLastInOneLineBlock: true}], // 结尾必须有分号
        'semi-spacing': [2, { // 一行有多个语句时，分号前面禁止有空格，分号后面必须有空格
            before: false,
            after: true
        }],
        'semi-style': 0, // 分号必须写在行尾，禁止在行首出现
        'sort-keys': 0, // 要求对象属性按序排列
        'sort-vars': 0, // 变量排序
        'space-before-blocks': [2, 'always'], // if, function 等的大括号之前必须要有空格，比如 if (a) {
        'space-before-function-paren': [2, { // 强制在 function 的左括号之前使用一致的空格
            anonymous: 'never',
            named: 'never',
            asyncArrow: 'always'
        }],
        'space-in-parens': [2, 'never'], // 小括号内的首尾禁止有空格
        'space-infix-ops': 0, // 操作符左右必须有空格，比如 let sum = 1 + 2;
        'space-unary-ops': [2, { // new, typeof 等后面必须有空格，++, -- 等禁止有空格
            words: true,
            nonwords: false
        }],
        'spaced-comment': 0, // 注释的斜线或 * 后必须有空格
        'switch-colon-spacing': [2, { // case 的冒号前禁止有空格，冒号后必须有空格
            after: true,
            before: false
        }],
        'template-tag-spacing': 0, // 模版字符串的 tag 之后禁止有空格，比如 tag`Hello World`
        'unicode-bom': 0, // 文件开头禁止有 BOM
        'wrap-regex': 0, // 要求正则表达式被包裹起来
        // ECMAScript 6
        // 这些规则与 ES6（即通常所说的 ES2015）有关
        'arrow-body-style': 0, // 箭头函数能够省略 return 的时候，必须省略，比如必须写成 () => 0，禁止写成 () => { return 0 }
        'arrow-parens': 0, // 要求箭头函数的参数使用圆括号
        'arrow-spacing': [2, { // 箭头函数的箭头前后必须有空格
            before: true,
            after: true
        }],
        'constructor-super': 2, // constructor 中必须有 super
        'generator-star-spacing': 0, // generator 的 * 前面禁止有空格，后面必须有空格
        'no-class-assign': 2, // 禁止对定义过的 class 重新赋值
        'no-confusing-arrow': 0, // 禁止出现难以理解的箭头函数，比如 let x = a => 1 ? 2 : 3
        'no-const-assign': 2, // 禁止对使用 const 定义的常量重新赋值
        'no-dupe-class-members': 2, // 不允许类成员中有重复的名称
        'no-duplicate-imports': 2, // 禁止重复导入
        'no-new-symbol': 0, // 禁止使用 new 来生成 Symbol
        'no-restricted-imports': 0, // 禁止 import 指定的模块
        'no-this-before-super': 2, // 禁止在 super 被调用之前使用 this 或 super
        'no-useless-computed-key': 2, // 禁止在对象中使用不必要的计算属性，比如 let a = { ['0']: 0 };
        'no-useless-constructor': 0, // 禁止出现没必要的 constructor，比如 constructor(value) { super(value) }
        'no-useless-rename': 0, // 禁止解构时出现同样名字的的重命名，比如 let { foo: foo } = bar;
        'no-var': 0, // 要求使用 let 或 const 而不是 var
        'object-shorthand': 0, // 要求对象字面量简写语法，比如 a = {b} 而不是 a = {b: b}
        'prefer-arrow-callback': 0, // 必须使用箭头函数作为回调
        'prefer-const': 0, // 申明后不再被修改的变量必须使用 const 来申明
        'prefer-destructuring': 0, // 优先使用数组和对象解构
        'prefer-numeric-literals': 0, // 禁用 parseInt() 和 Number.parseInt()，使用二进制，八进制和十六进制字面量
        'prefer-rest-params': 0, // 必须使用 ...args 而不是 arguments
        'prefer-spread': 0, // 建议使用扩展运算符而非 .apply()
        'prefer-template': 0, // 必须使用模版字符串而不是字符串连接
        'require-yield': 0, // generator 函数内必须有 yield
        'rest-spread-spacing': [2, 'never'], // ... 的后面禁止有空格
        'sort-imports': 0, // import 必须按规则排序
        'symbol-description': 0, // 创建 Symbol 时必须传入参数
        'template-curly-spacing': [2, 'never'], // ${name} 内的首尾禁止有空格
        'yield-star-spacing': 0, // yield* 后面必须要有空格
        'react/boolean-prop-naming': 0,     // 布尔值类型的 propTypes 的 name 必须为 is 或 has 开头  @off 不强制要求写 propTypes
        'react/no-direct-mutation-state': 2,  // 禁止直接修改 this.state
        'react/require-render-return': 2,     // render 方法中必须有返回值
        'react/jsx-key': 2,                   // 数组中的 jsx 必须有 key
        'react/jsx-no-duplicate-props': 2     // 禁止出现重复的 props
    }
};
```