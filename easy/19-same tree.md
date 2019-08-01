相同的数，给定两个二叉树，判断是否相同，主要考察递归，代码如下
```js
var isSameTree = function(p, q) {
    if(isNull(p) && isNull(q)) {
       return true;
    }
    if((isNotNull(p) && isNull(q)) || (isNull(p) && isNotNull(q))) {
        return false;
    }
    if(p.val !== q.val){
        return false;
    }
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
};

var isNotNull = function(o) {
    return o !== null;
}

var isNull = function(o) {
    return o === null;
}

function TreeNode(val) {
    this.val = val;
    this.left = this.right = null;
}
```