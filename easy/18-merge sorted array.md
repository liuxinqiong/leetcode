给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

这个题目尝试了蛮多次，感觉 nums1 数组使用 0 占位，从 JS 的角度反而增加了复杂度，最后给出的代码如下
```js
var merge = function(nums1, m, nums2, n) {debugger;
    var t = 0; // 偏移
    for(var i = 0; i < n; i++) {
        var n2 = nums2[i];
        if(!m) {
            nums1.splice(0, 1, n2);
            m++;
            continue;
        }
        for(var j = t; j < m; j++) {
            var n1 = nums1[j];
            var nextIndex = j + 1;
            var next = nums1[nextIndex];
            var insertIndex = -1;
            if(n2 <= n1) {
                insertIndex = j;
            }
            if(n2 > n1 && ( nextIndex >= m || n2 <= next)) {
                insertIndex = j + 1;
            }
            if(insertIndex !== -1) {
                nums1.splice(insertIndex, 0, n2);
                m++;
                t = insertIndex;
                break;
            }
        }
    }
    nums1.length = m
};
```