名为 Remove Duplicates from Sorted Array，看了描述一大堆，甚至有点看不懂，但代码一写一尝试，发现好简单的样子，主要需要注意的地方就是要倒序遍历数组，否则删除元素会导致 index 发生变化，从而不正确，代码如下：
```js
var removeDuplicates = function(nums) {
    for(var i = nums.length - 1; i >= 0; i--) {
        if(nums[i] === nums[i+1]) {
           nums.splice(i+1, 1);
        }
    }
    return nums.length;
};
```