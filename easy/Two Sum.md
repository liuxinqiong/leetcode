给定一个数组和目标值，返回数组中相加等于目标值的两项的下标。

方案
```js
var twoSum = function(nums, target) {
    for(var i = 0; i < nums.length; i++) {
        var number = nums[i]
        var delta = target - number
        var index = nums.indexOf(delta)
        if( index > -1 && index !== i) {
            return [i, index]
        }
    }
};
```

分析下来，这个解法有很大的性能空间，主要是 indexOf 内部肯定也是开循环查找，如此时间复杂度便是O(n ^ 2)，解决思路：用 Map 代替 Array，因为 Map 的元素查找复杂度为 O(1)，优化后代码如下
```js
var twoSum = function(nums, target) {
    if(nums.length === 2) {
        return [0, 1]
    }
    const length = nums.length
    let hashTable = Object.create(null)
    for(let i = 0; i < length; i++) {
        hashTable[nums[i]] = i
    }
    for(let i = 0; i < length; i++) {
        var number = nums[i]
        var delta = target - number
        let found = hashTable[delta]
        if(found !== undefined && found !== i) {
            return [i, found]
        }
    }
};
```

接下来看一种更优秀的写法，将 Array 转 Map 的过程，放在查找的循环中
```js
var twoSum = function(nums, target) {
    if (nums.length === 2) return [0, 1];
    const len = nums.length;
    let map = {};
    for(let i = 0; i < len; i++) {
        let n = target - nums[i];
        let find = map[n];
        if(find !== undefined) return [find, i];
        else map[nums[i]] = i;
    }
};
```

这种方案，我一开始想，会不会错过彼此，比如目前 n 元素在 map 中不存在，但是在后续的 nums 中是有的，但仔细一想，前一次错过彼此了，但是循环到后面的指定元素的时候，前一个元素肯定就已经存在于 map 中了，因此这是一种很棒的解法。