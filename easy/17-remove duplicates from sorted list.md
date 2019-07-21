名为 remove duplicates from sorted list，删除排序列表中的重复元素，解该题开始并没有主要到是已经排序链表，因此给出的解法，性能上会有所损耗，不过结果还算好，击败了 84.36 % 用户，针对优化的方案，以后给吧！！！
```js
var deleteDuplicates = function(head) {
    var res = new ListNode();
    if(!head) {
        return res.next;
    }
    var object = Object.create(null);
    var currentElement = res;
    while(head.next) {
        var val = head.val;
        if(!object[val]) {
            object[val] = true;
            currentElement.next = new ListNode(val);
            currentElement = currentElement.next;
        }
        // 移动到下一个元素
        head = head.next;
    }
    // 处理最后值
    if(!object[head.val]) {
        currentElement.next = new ListNode(head.val);
    }
    return res.next;
};

function ListNode(val) {
    this.val = val;
    this.next = null;
}
```