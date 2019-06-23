Plus One，给定一个非负整数数组用来表示一个整数，返回加 1 后的数组表示，需要考虑的地方就是超过最大数字的情况。
```js
var lengthOfLastWord = function(s) {
    s = s.replace(/^\s+|\s+$/g, '');
    if(!s || !s.length) {
        return 0;
    }
    var ss = s.split(' ');
    var lastWorld = ss[ss.length - 1];
    return lastWorld.length;
};
```