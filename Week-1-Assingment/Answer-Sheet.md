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
##   Submission Link : https://leetcode.com/problems/assign-cookies/submissions/1560447245
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
#    Question 3: Subarrays With Exactly K Distinct Integers
##    Submission Link : https://leetcode.com/problems/subarrays-with-k-different-integers/submissions/1900586806
```java
import java.util.*;

class Solution {
    public int subarraysWithKDistinct(int[] nums, int k) {
        return atMost(nums, k) - atMost(nums, k - 1);
    }

    private int atMost(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int left = 0;
        int res = 0;

        for (int right = 0; right < nums.length; right++) {
            map.put(nums[right], map.getOrDefault(nums[right], 0) + 1);

            while (map.size() > k) {
                map.put(nums[left], map.get(nums[left]) - 1);
                if (map.get(nums[left]) == 0) {
                    map.remove(nums[left]);
                }
                left++;
            }

            res += right - left + 1;
        }

        return res;
    }
}

```
#    Question 4: Sum of Power of All Subsequences
##    Submission Link :https://leetcode.com/problems/power-of-heroes/submissions/1900590848
```java
java
import java.util.*;

class Solution {
    public int sumOfPower(int[] nums) {
        Arrays.sort(nums);
        long mod = 1_000_000_007;
        long res = 0;
        long prefix = 0;

        for (int x : nums) {
            long val = (x * 1L * x) % mod;
            res = (res + val * (x + prefix)) % mod;
            prefix = (prefix * 2 + x) % mod;
        }

        return (int) res;
    }
}
```
#    Question 5: 
##    Submission Link : 
```java

```
#    Question 6:
##    Submission Link :
```java

```
