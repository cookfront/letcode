Merge Two Binary Trees
========

关键词：`二叉树`、`递归`

## 题目描述

> Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.
> 
> You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

**Example 1:**

```
Input: 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  

Output: 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
```

## 解题思路

**思路一：**

先把当前根节点合并到一个新的节点上，然后递归的合并左右子树即可。先写了一个很挫的代码：

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode mergeTrees(TreeNode t1, TreeNode t2) {
        if (t1 == null && t2 == null) return null;

        int val = 0;
        if (t1 != null && t2 != null) {
            val = t1.val + t2.val;
        } else if (t1 != null) {
            val = t1.val;
        } else if (t2 != null) {
            val = t2.val;
        }

        TreeNode node = new TreeNode(val);

        node.left = mergeTrees(t1 == null ? null : t1.left, t2 == null ? null : t2.left);
        node.right = mergeTrees(t1 == null ? null : t1.right, t2 == null ? null : t2.right);

        return node;
    }
}
```

## 总结

这道题目前只想到一种递归的方式。
