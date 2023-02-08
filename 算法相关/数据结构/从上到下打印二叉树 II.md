# 描述
从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

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
  [9,20],
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
    if(!root) {
        return [];
    }
    const result = [];
    const queue = [];
    queue.push(
        root
    );
    while(queue.length) {
        const level = queue.length;
        result.push([])
        for(let i = 0 ; i< level; i ++) {
            const node = queue.shift();
            result[result.length - 1].push(node.val);
            node.left && queue.push(node.left );
            node.right && queue.push(node.right);
        }

    }
    return result;
};
```