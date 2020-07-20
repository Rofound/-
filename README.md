# 分组解析算法
用于解析一行行有规则的数据，将每一行做为最小单元

```javascript
var str = `
valid-typeof
强制 typeof 表达式与有效的字符串进行比较
true
block-scoped-var
强制把变量的使用限制在其定义的作用域范围内
True
curly
强制所有控制语句使用一致的括号风格
True
default-case
要求 switch 语句中有 default 分支
multi-line
eqeqeq
要求使用 === 和 !==
True
no-alert
禁用 alert、confirm 和 prompt
process.env.NODE_ENV=== 'production' ? 2 : 1
no-caller
禁用 arguments.caller 或 arguments.callee
False
no-case-declarations
不允许在 case 子句中使用词法声明
true
no-empty-function
禁止出现空函数
true
no-eq-null
禁止在没有类型检查操作符的情况下与 null 进行比较
True(和eqeqeq相同)
no-eval
禁用 eval()
True（性能优化问题）
no-extra-bind
禁止不必要的 .bind() 调用
false
no-extra-label
禁用不必要的标签
True
no-fallthrough
禁止 case 语句落空
True
no-floating-decimal
禁止数字字面量中使用前导和末尾小数点
True
no-global-assign
禁止对原生对象或只读的全局对象进行赋值
True
no-implicit-coercion
禁止使用短符号进行类型转换
True
no-implied-eval
禁止使用类似 eval() 的方法
True
no-invalid-this
禁止 this 关键字出现在类和类对象之外
True
no-iterator
禁用 __iterator__ 属性
没用过，无所谓
no-labels
禁用标签语句
False
no-loop-func
禁止在循环语句中出现包含不安全引用的函数声明
True
no-multi-spaces
禁止使用多个空格
True
no-multi-str
禁止使用多行字符串
True
no-new
禁止使用 new 以避免产生副作用
True
no-octal
禁用八进制字面量
True
no-octal-escape
禁止在字符串中使用八进制转义序列
True
no-param-reassign
禁止对 function 的参数进行重新赋值
True
no-proto
禁用 __proto__ 属性
True
no-redeclare 
禁止多次声明同一变量
True
no-return-assign
禁止在 return 语句中使用赋值语句
always
no-return-await
禁用不必要的 return await
True（待研究）
no-self-assign
禁止自我赋值
True
no-self-compare
禁止自身比较
True
no-sequences
禁用逗号操作符
True
no-unmodified-loop-condition
禁用一成不变的循环条件
True
no-unused-labels
禁用出现未使用过的标签
True
no-useless-catch
禁止不必要的 catch 子句
True
no-useless-escape
禁用不必要的转义字符
True
no-with
禁用 with 语句
True
radix
强制在 parseInt() 使用基数参数
True
require-await
禁止使用不带 await 表达式的 async 函数
True
no-delete-var
禁止删除变量
False
no-shadow
禁止变量声明与外层作用域的变量同名
False
no-shadow-restricted-names
禁止将标识符定义为受限的名字
True
no-undef
禁用未声明的变量，除非它们在 /*global */ 注释中被提到
True
no-unused-vars
禁止出现未使用过的变量
True
no-use-before-define
禁止在变量定义之前使用它们
True
camelcase
强制使用骆驼拼写法命名约定
True
comma-spacing
强制在逗号前后使用一致的空格
True（禁止逗号前使用，强制在逗号后使用空格）
consistent-this
当获取当前执行环境的上下文时，强制使用一致的命名
True，_this
func-call-spacing
要求或禁止在函数标识符和其调用之间有空格
True(例如：a())
jsx-quotes
强制在 JSX 属性中一致地使用双引号或单引号
True(双引号)
key-spacing
强制在对象字面量的属性中键和值之间使用一致的间距
True（冒号后加空格，前面不加）
keyword-spacing
强制在关键字前后使用一致的空格
True
lines-around-comment
要求在注释周围有空行
True
lines-between-class-members
要求或禁止类成员之间出现空行
True
max-depth
强制可嵌套的块的最大深度
True，4层
multiline-comment-style
强制对多行注释使用特定风格
True，默认
multiline-ternary
要求或禁止在三元操作数中间换行
True，never
no-lonely-if
禁止 if 作为唯一的语句出现在 else 语句中
False
no-mixed-operators
禁止混合使用不同的操作符
True
no-mixed-spaces-and-tabs
禁止空格和 tab 的混合缩进
True
no-multi-assign
禁止连续赋值
True
no-nested-ternary
禁用嵌套的三元表达式
False
object-curly-newline
强制大括号内换行符的一致性
True，"multiline": true
object-property-newline 
强制将对象的属性放在不同的行上
False（与上一个冲突）
quotes
强制使用一致的反勾号、双引号或单引号
True
semi-style
强制分号的位置
False
space-in-parens
强制在圆括号内使用一致的空格
True
switch-colon-spacing
强制在 switch 的冒号左右有空格
True
arrow-body-style
要求箭头函数体使用大括号（always）
True
no-const-assign
禁止修改 const 声明的变量
True
no-dupe-class-members 
禁止类成员中出现重复的名称
True
prefer-template
要求使用模板字面量而非字符串连接
True`

var arr = str.split('\n')
console.log(arr)
function calc(total, ele, index, that) {
    if (index === 0) {
        return ''
    }
    var res = total
    if ((index % 3 === 2)) {
        res = `${res}: #{value},// ${ele}\n`
    }
    else if ((index % 3 === 0)) {
        if (/True|true/.test(ele)) {
            ele = `[2]`
        }
        res = res.replace(/#{value}/, ele)
    } 
    else if ((index % 3 === 1)) {
        res = `${res}'${ele}'`        
    } 
    
    return res
}

// main
// var result = arr.reduce(calc, '')
// copy(result)
// console.log(result)

function reduce2(lineArr) {
    var result = []
    function calcByGroup(ele, index, that) {
        if (index === 0) {
            return ''
        }
        if (index % 3 === 0) {
            var value = that[index]
            var comment = that[index - 1]
            var key = that[index - 2]
            result.push({
                value,
                comment,
                key
            })
        }
    }
    function getStrByTemplate(total, ele, index, that) {
        var {key, comment, value} = ele
        if (/True|true/.test(value)) {
            value = `[2]`
        }
        var result = `${total}'${key}': ${value}, //${comment}\n`
        return result
    }
    lineArr.forEach(calcByGroup)
    return result.reduce(getStrByTemplate, '')
}

// main
result = reduce2(arr)
copy(result)
console.log(result)
```
