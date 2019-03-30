名称为 Reverse Integer，给定一个数字，将数组部分反转，需要考虑到大小边界问题，假定为 32 位带符号整形，同时需要考虑到负数的问题。

我的解法是借用数组的 reverse 方法，具体如下
```js
var reverse = function(x) {
    var res = (x).toString().split('').reverse().join('')
    // 判断是不是负数，特殊处理，借用 Number 函数将字符串转为数组，会自动去除开始可能存在的 0
    if(res.charAt(res.length - 1) === '-') {
        res = Number('-' + res.substring(0, res.length - 1))
    }
    // 判断是否超出范围
    if(Math.abs(res) > 0x7FFFFFFF) {
        return 0
    }
    return res
};