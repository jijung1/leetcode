*Problem Description

Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.

Example 1:

Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

Output: True
 

Example 2:

Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

Output: False

*Solution



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
 * @param {number} k
 * @return {boolean}
 */
var findTarget = function(root, k) {
    /*
        1. how to recursively iterate over a bst
        2. only need to traverse down to and consider the subtree of bst that holds values less than the            target node
            Once subtree is found, should start from the right most leaf node and look for a pairable node where sum(n, rightleaf) == target.
        3. So for problem 1 the root.val < target, so you have to consider the entire tree. 
            reverse inorder traversal + inorder traversal
            
            
            given a subtree, how do you traverse in order
            
            curr = root;
            
            
            inorderArr(root) {
                inorderArr(root.left);
                console.log(root.val);
                inorderArr(root.right);
            }
            
            actually let's just turn the tree into an array and and iteratively search
    */
    arr2 = new Array();
    inorderTraverse(root);
    for (i = 0; i < arr2.length-1; ++i) {
        for (j = i+1; j < arr2.length; ++j) {
            
            if ((arr2[i]+arr2[j]) == k) {
                return true;
            }
        }
    }

    return false;
    
};

function inorderTraverse(node) {
    if (node.left != null) 
        inorderTraverse(node.left);
    arr2.push(node.val);

    if (node.right != null)
        inorderTraverse(node.right);

}

```
