名为 Valid Parentheses，判断给定字符是否是有效的括号搭配，具体字符有'(', ')', '{', '}', '[' and ']'几种，更多描述我就不啰嗦了，看到题目描述的第一瞬间，就立刻感觉需要使用栈数据结构，我的代码如下，令人激动的是打败了 100% 的玩家，这貌似是我首次达成此成就。
```js
var map = {
    ')': '(',
    '}': '{',
    ']': '['
}
var isValid = function(s) {
    var length = s.length
    if(length % 2 !== 0) {
        return false
    }
    var stack = [], top;
    for(var i = 0; i < length; i++) {
        if(stack.length) {
            top = stack[stack.length - 1]
        } else {
            stack.push(s[i])
            continue;
        }
        if(map[s[i]] === top) {
            stack.pop()
        } else {
            stack.push(s[i])
        }
    }
    return stack.length === 0
};
```