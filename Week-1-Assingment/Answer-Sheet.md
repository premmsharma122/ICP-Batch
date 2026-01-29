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
