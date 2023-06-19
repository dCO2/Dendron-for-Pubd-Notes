---
id: k6x1pxjfj7oldhylm7xxfo0
title: same tree - leetcode 100
desc: ''
updated: 1687192603422
created: 1687173247651
---

At the time I was just beginning to properly understand how the code for recursion should play out when implementing one, I attempted the [Same Tree (Easy) Leetcode problem](https://leetcode.com/problems/same-tree/) with the following accepted solution in C++:

```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool issame = true;
    
    int caller(TreeNode* p, TreeNode* q){
        
        if(p == nullptr && q == nullptr){
            return 0;
        }
        
        if(p == nullptr || q == nullptr){
            issame = false;
            return 0;
        }
    
        if(p->val != q->val){
            issame = false;
        }
        
        if(!issame){
            return 0;
        }
        
        if(p->right != nullptr && q->right != nullptr){
            int pr = caller(p->right, q->right);
        }
        
        if(p->left != nullptr && q->left != nullptr){
            int pl = caller(p->left, q->left);
        }
        
        if(p->right == nullptr && q->right != nullptr){
            issame = false;
            return 0;
        }
        
        if(p->left == nullptr && q->left != nullptr){
            issame = false;
            return 0;
        }
        
        if(p->right != nullptr && q->right == nullptr){
            issame = false;
            return 0;
        }
        
        if(p->left != nullptr && q->left == nullptr){
            issame = false;
            return 0;
        }
        
        return 0;
    }
    
    bool isSameTree(TreeNode* p, TreeNode* q) {
        int test = caller(p, q);
        return issame;
    }
};
```

It is clear that this was the most intuitive way for me to think about solving recursion. VIZ: Initialize some global variable, and go through each of the (base)cases for the recursion so that some condition modifies the global variable.

The same pattern is seen when I solved for [validate binary search tree](), [Balanced Binary Tree - leetcode 110](),...

But I can't help but think there's a much better approach to these, yes?? Or some code with the same logic but refactored elegantly.

And yes there is. See [[thinking non-intuitively about rescurion]].

Also, mind you, the code is not verbose because of the choice of programming language; c++, but because of my (intuitive & beginner) thought process while solving it.

#### Misc:
[[balanced binary tree]]
[[validate binary search tree]]

[[maximum value in a binary tree]]
