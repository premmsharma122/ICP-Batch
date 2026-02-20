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
