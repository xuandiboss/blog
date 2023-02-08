# 描述
请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果：

[
  [3],
  [20,9],
  [15,7]
]
## 提示：
节点总数 <= 1000
# 代码实现
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[][]}
 */
var levelOrder = function(root) {
    const result = [];
    const queue = [];
    if(!root) {
        return [];
    }
    queue.push(root);
    while(queue.length) {
        const level = queue.length;
        result.push([]);
        for(let i = 0; i < level; i++) {
            const node = queue.shift();
            if(result.length % 2) {
                result[result.length - 1].push(node.val);
            } else {
                result[result.length - 1].unshift(node.val);
            }
            node.left && queue.push(node.left);
            node.right && queue.push(node.right);
        }
    }
    return result;
};
```