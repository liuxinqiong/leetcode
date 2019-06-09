名为 Roman to Integer，将罗马数组转换成普通数组，其实非常简单，只是有几种特殊情况需要判断一下。我的答案如下
```js
// map 将字符快速转数字
var map = {
    I: 1,
    V: 5,
    X: 10,
    L: 50,
    C: 100,
    D: 500,
    M: 1000
};
// 判断是否属于减法情况
var isSubCase = function(prevChar, curChar) {
    var bool = false
    if((prevChar === 'I' && (curChar === 'V' || curChar === 'X') || 
        prevChar === 'X' && (curChar === 'L' || curChar === 'C') ||
        prevChar === 'C' && (curChar === 'D' || curChar === 'M'))) {
        bool = true
    }
    return bool
}
var romanToInt = function(s) {
    var len = s.length
    var res = 0
    var prevChar
    for(var i = 0; i < len; i++) {
        var curChar = s[i]
        if(prevChar && isSubCase(prevChar, curChar)) {
            res += map[curChar] - 2 * map[prevChar]
        } else {
            res += map[curChar]
        }
        prevChar = curChar
    }
    return res
};
```