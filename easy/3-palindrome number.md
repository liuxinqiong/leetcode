名称为 palindrome number，大概意思就是说判断一个数是不是顺着读，倒着读结果是一样的。

脑海里的第一个想法就是借用数组的 reverse 函数，因此代码如下
```js
var isPalindrome = function(x) {
    var reverseInterge = Number((x).toString().split('').reverse().join(''))
    return reverseInterge === x
};
```

洋洋洒洒写下来，一顿提交后，运行速度好像不是太理想，占用内存也比较大，难道是我借用数组的原因，于是不用数组写了如下的代码
```js
var isPalindrome = function(x) {
    var xString = (x).toString()
    var len = xString.length
    var res = ''
    for(var i = len - 1; i >=0; i--) {
        res += xString[i]
    }
    return x === Number(res)
}
```

代码提交后，也是没啥大问题的，可惜的是，我发现运行时间和占用内存和第一个方法差别不大。