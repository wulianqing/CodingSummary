- 二叉树

  - 题105.从前序与中序遍历序列构造二叉树

    ```c++
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder){}
    返回TreeNode*
    	1. 找到当前节点，赋值给当前TreeNode*
      2. 划分子树，左右节点分别返回buildTree(左子树前序，左子树中序)
    ```
