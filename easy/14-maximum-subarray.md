给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

这个题目感觉很厉害哇，想了很久了，没有头绪，无奈看了下评论。
```js
var maxSubArray = function(nums) {
    var res = nums[0];
    var sum = 0;
    for(var i = 0; i < nums.length; i++) {
        var num = nums[i];
        if(sum > 0) {
            sum += num;
        } else {
            sum = num
        }
        res = Math.max(res, sum);
    }
    return res;
};
```