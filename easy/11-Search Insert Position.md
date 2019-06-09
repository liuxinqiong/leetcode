名为 Search Insert Position，查询指定元素应该插入的位置，如果数组中已经存在该元素，则直接返回对应下标。

比较简单，就不废话了，直接贴代码
```js
var searchInsert = function(nums, target) {
    for(var i = 0; i < nums.length; i++) {
        var value = nums[i];
        if(target <= value) {
            return i;
        }
    }
    return nums.length;
};
```