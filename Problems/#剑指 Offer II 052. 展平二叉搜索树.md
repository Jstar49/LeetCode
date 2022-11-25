<!--
 * @Author: joessem jxxclj@gmail.com
 * @Date: 2022-11-25 22:27:57
 * @LastEditors: joessem jxxclj@gmail.com
 * @LastEditTime: 2022-11-25 22:28:48
 * @FilePath: \LeetCode\Problems\#剑指 Offer II 052. 展平二叉搜索树.md
 * @Description: 
 * 
 * Copyright (c) 2022 by joessem jxxclj@gmail.com, All Rights Reserved. 
-->
## 描述

给你一棵二叉搜索树，请 按中序遍历 将其重新排列为一棵递增顺序搜索树，使树中最左边的节点成为树的根节点，并且每个节点没有左子节点，只有一个右子节点。

 

示例 1：



输入：root = [5,3,6,2,4,null,8,1,null,null,null,7,9]
输出：[1,null,2,null,3,null,4,null,5,null,6,null,7,null,8,null,9]
示例 2：



输入：root = [5,1,7]
输出：[1,null,5,null,7]
 

提示：

树中节点数的取值范围是 [1, 100]
0 <= Node.val <= 1000

来源：力扣（LeetCode）
链接：https://leetcode.cn/problems/NYBBNL
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 方案

```c#

/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left;
 *     public TreeNode right;
 *     public TreeNode(int val=0, TreeNode left=null, TreeNode right=null) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
public class Solution {
    List<TreeNode> inin = new List<TreeNode>();
    public TreeNode IncreasingBST(TreeNode root) {
        TreeNode retNode = new TreeNode();
        TreeNode start = retNode;
        test(retNode, root);
        foreach(TreeNode node in inin){
            retNode.right = new TreeNode(node.val);
            retNode = retNode.right;
        }

        return start.right;
    }
    void test(TreeNode retNode, TreeNode root){
        if (root == null){
            return;
        }
        
        test(retNode, root.left);
        // retNode.right = new TreeNode(root.val, null, null);
        inin.Add(root);
        // Console.WriteLine(root.val);
        // retNode = retNode.right;
        test(retNode, root.right);
        
    }
}

```