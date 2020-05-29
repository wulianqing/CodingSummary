- 二叉树

  - 题105.从前序与中序遍历序列构造二叉树

    ```c++
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder){}
    返回TreeNode*
    	1. 找到当前节点，赋值给当前TreeNode*
      2. 划分子树，左右节点分别返回buildTree(左子树前序，左子树中序)
    ```
    
  - offer 55-I.二叉树的深度

    ```c++
    dfs:
    思想:当前层的深度 = 下一层最大深度 + 1
      
    int maxDepth(TreeNode* root) {
      	if(root == NULL)return 0;
    		return max(maxDepth(root->left),maxDepth(root->right))+1;
    }
    ```

    ```c++
    bfs:
    思想:一层一层来,多增加一层则 ans++
      
    class Solution {
    public:
        int maxDepth(TreeNode* root) {
            if(root == NULL)return 0;
            queue<TreeNode*> que;
            int ans=0;
            que.push(root);
            while(!que.empty()){
              	//当前层的节点数
                int cur_layer_length = que.size();
              	//把当前层的子节点压入队列, 当前层节点全部pop, 然后层数+1
                for(int i=0;i<cur_layer_length;i++){
                    TreeNode* temp = que.front();
                    que.pop();
                    if(temp->left!=NULL)que.push(temp->left);
                    if(temp->right!=NULL)que.push(temp->right);
                }
                ans++;
            }
            return ans;
        }
    };
    ```

  - offer26. 树的子结构
  
    ```c++
    TreeNode* A,B;
    判断B是不是A的子结构
    思路:先在A中找B的root节点,再遍历B看是不是A都有
    
    递归的思想:
    	1. A找B的root节点:(isSubStructure():找,并保证结构匹配)
    			先除掉一些exception,比如B==NULL,A==NULL这种,然后先看当前是不是符合,是否结构匹配,不符合只要在左右子树有就行,所以return用||连接
      2. 结构是否匹配
          不相等直接false
          当前匹配之外,左右也必须都匹配,所有return要用&&连接
    ```
    
    
    
  - offer 27. 镜像二叉树
  
    ```c++
    思想: bfs
    
    class Solution {
    public:
        //use bfs travel
        TreeNode* mirrorTree(TreeNode* root) {
            //exception
            if(root == NULL ||(root->left==NULL && root->right == NULL))return root;
    
            //init: queue, push root
            queue<TreeNode*> q;
            q.push(root);
    
            //bfs: visit left & right child(both r null? if not: exchange)
            while(!q.empty()){
                int length_curr_queue = q.size();
                for(int i = 0;i < length_curr_queue;i++){
                    TreeNode* temp = q.front();
                    q.pop();
                    if(temp->left == NULL && temp->right == NULL){
                        continue;
                    }
                    else{
                        TreeNode* temp_node = temp->right;
                        temp->right = temp->left;
                        temp->left = temp_node;
                    }
                    if(temp->left != NULL)q.push(temp->left);
                    if(temp->right != NULL)q.push(temp->right);
                }
            }
            return root;
        }
    };
    ```
  
    