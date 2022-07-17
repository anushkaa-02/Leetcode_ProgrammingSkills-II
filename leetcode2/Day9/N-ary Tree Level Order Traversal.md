# N-ary Tree Level Order Traversal
- ## Question:
>Given an n-ary tree, return the level order traversal of its nodes' values.
>
>Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value (See examples).

- Example :

      Input: root = [1,null,3,2,4,null,5,6]
      Output: [[1],[3,2,4],[5,6]]
      
- ## Solution:
```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(Node* root) {
        vector<vector<int>> ans;
        
        if(root==NULL)
            return ans;
        
        queue<Node*> q;
        q.push(root);
        
        while(!q.empty())
        {
            vector<int> level;
            int size= q.size();
            
            for(int i=0;i<size;i++)
            {
                Node *node= q.front();
                q.pop();
                
                int s= (node->children).size();
                
                for(int i=0;i<s;i++)
                {
                    if((node->children).at(i)!=NULL)
                        q.push((node->children).at(i));
                }
                
                level.push_back(node->val);
            }
            ans.push_back(level);
        }
        
        return ans;
        
    }
};
```

## Tags

`Tree` `BFS`
