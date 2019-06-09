 名为 Implement strStr，判断一个子串在母串出现的下标位置，其实就是实现一下 JavaScript 中的 indexOf 函数，我直接调用原生 indexOf 函数，运行时间是 52ms，自己手写的运行时间是 56ms，还是有差距哇，代码如下：
```js
var strStr = function(haystack, needle) {
    if(!needle) {
        return 0;
    }
    var findIndex = -1;
    var needleIndex = 0;
    var length = needle.length;
    var resetIndex = 0;
    for(var i = 0; i < haystack.length; i++) {
        if(haystack[i] === needle[needleIndex]) {
            needleIndex++;
        } else {
            needleIndex = 0;
            i = resetIndex++;
            continue;
        }
        if(needleIndex === length) {
            findIndex = i;
            break;
        }
    }
    return findIndex === -1 ? -1 : findIndex - length + 1;
};
```