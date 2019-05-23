名为 Merge Two Sorted Lists，给定两个链表式的已经排序的结构，合并成一个。

一开始想到一个很蠢的方式，直接将两个 ListNode 转成 Array，然后 concat Array 在进行 sort，然后转成 ListNode 结构。这种方式有多蠢我就不说了好吧，结果就是执行效率贼慢，因此我都不好意思贴代码了。

接下来说说高效的两种实现方式，一种是递归，一种是非递归。

使用递归
```js
var mergeTwoLists = function(l1, l2) {
    if(l1 === null) {
        return l2;
    }
    if(l2 === null) {
        return l1;
    }
    if(l1.val < l2.val) {
        l1.next = mergeTwoLists(l1.next, l2);
        return l1;
    } else {
        l2.next = mergeTwoLists(l1, l2.next);
        return l2;
    }
};
```

使用递归可能没那么好理解，看看非递归的方式就很容易明白了
```js
function ListNode(val) {
    this.val = val;
    this.next = null;
}
var mergeTwoLists = function(l1, l2) {
    var res = new ListNode(0);
    var temp = res;
    while(l1 !== null && l2 !== null) {
        var min = Math.min(l1.val, l2.val);
        temp.next = new ListNode(min);
        temp = temp.next;
        if(l1.val < l2.val) {
            l1 = l1.next;
        } else {
            l2 = l2.next;
        }
    }
    if(l1 === null) {
       temp.next = l2;
    } else {
        temp.next = l1;
    }
    return res.next;
}
```