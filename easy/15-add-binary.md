名为二进制求和，给定两个二进制字符串，求他们的和。我给出的代码，虽然有点长，但是性能还算 OK，打败了 82% 的用户。
```js
var addBinary = function(a, b) {
    var lengthA = a.length;
    var lengthB = b.length;
    var delta = Math.abs(lengthA - lengthB);
    var maxLength = Math.max(lengthA, lengthB);
    var bigOne = lengthA > lengthB ? a : b;
    var smallOne = lengthA > lengthB ? b : a;
    var res = '';
    var remain = 0;
    for(var i = maxLength - 1; i >= 0; i--) {
        var num1 = bigOne[i];
        var num2 = i - delta >= 0 ? smallOne[i - delta] : 0;
        var temp = Number(num1) + Number(num2) + remain;
        if(temp > 1) {
            temp = temp === 2 ? 0 : 1;
            remain = 1;
        } else {
            remain = 0;
        }
        res = temp + res;
    }
    if(remain === 1) {
        res = 1 + res;
    }
    return res;
};
```