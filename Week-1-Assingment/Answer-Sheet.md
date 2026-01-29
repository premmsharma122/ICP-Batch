#  Question 1: Maximum Number of Different Candies
##  Submision Link: https://leetcode.com/problems/distribute-candies/submissions/1835887305
```java
#import java.util.*;

class Solution {
    public int distributeCandies(int[] candyType) {
        HashSet<Integer> set = new HashSet<>();
        for (int c : candyType) {
            set.add(c);
        }
        return Math.min(set.size(), candyType.length / 2);
    }
}
```
#    Question 2: Assign Cookies (Greedy)
##   Submision Link : https://leetcode.com/problems/assign-cookies/submissions/1560447245
```java
import java.util.*;

class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);

        int i = 0;
        int j = 0;

        while (i < g.length && j < s.length) {
            if (s[j] >= g[i]) {
                i++;
            }
            j++;
        }

        return i;
    }
}

```
