名为 Length of Last Word，得到一个句子中，最后一个单词的长度，这里需要注意一个前后多于空格的问题。代码如下
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