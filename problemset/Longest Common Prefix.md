名为 Longest Common Prefix，求字符串数组中最长相同前缀
```js
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    // 如果一个单词都没有，直接返回空
    if(strs.length === 0) return ''
    // 取第一个单词
    var firstStr = strs[0]
    // 取第一个单词的长度
    var firstLen = firstStr.length
    // 用来存储结果
    var res = ''
    // 参考第一个单词长度循环
    for(var i = 0; i< firstLen; i++) {
        var count = 0;
        // 循环每一个单词
        for(var j = 0; j < strs.length - 1; j++) {
            // 取各自单词的各自 i 号位置上的字母
            var a = strs[j][i]
            var b = strs[j + 1][i]
            // 两两比较，如果相同，将成功次数 count + 1
            if(compare(a, b)) {
                count++
            } else {
                // 不相同，认定出现不一致的地方了，跳出循环
                break;
            }
        }
        // 如果成功次数等于所有单词个数减 1，认为大家该位置都相同，将字符累加到结果上
        if(count === strs.length - 1) {
           res += firstStr[i]
        } else {
            // 出现不一致结束循环
            break;
        }
    }
    return res
};

function compare(a, b) {
    return a === b
}
```