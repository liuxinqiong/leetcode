名为 Remove Element，不知道是不是同情我落下的打卡太多了还是咋滴，这次的题目和上次差不太多，考察的也是 splice 函数的使用，比较简单，就不多废话啦，代码如下：
```js
var removeElement = function(nums, val) {
    for(var i = nums.length - 1; i >= 0; i--) {
        if(nums[i] === val) {
            nums.splice(i, 1);
        }
    }
    return nums.length;
};
```