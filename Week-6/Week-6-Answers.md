#  2673. Make Costs of Paths Equal in a Binary Tree
```java
class Solution {
    public int minIncrements(int n, int[] cost) {
        int ans = 0;
        for (int i = n / 2; i >= 1; i--) {
            int left = cost[2 * i - 1];
            int right = cost[2 * i];
            ans += Math.abs(left - right);
            cost[i - 1] += Math.max(left, right);
        }
        return ans;
    }
}
```
#    1382. Balance a Binary Search Tree
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public void inorder(TreeNode node, List<Integer> val){
        if(node==null) return;
        inorder(node.left,val);
        val.add(node.val);
        inorder(node.right, val);
    }
    public TreeNode build(List<Integer> val, int l , int r){
        if(l>r) return null;
        int mid = (l+r)/2;
        TreeNode rt = new TreeNode(val.get(mid));
        rt.left= build(val,l,mid-1);
        rt.right = build(val,mid+1,r);
        return rt;
    }
    public TreeNode balanceBST(TreeNode root) {
        List<Integer> val = new ArrayList<>();
        inorder(root,val);
        return build(val,0,val.size()-1);
    }
}
```
