#  Question -
You want to buy food from a store. You have a
scoring system that uses a unit called taste points
.
Each time you buy a type of food, you can measure
its tastiness by the number of taste points you get
from that food.
You have N types of food. You can buy any type
any number of times, as long as the total number
of meals does not exceed M.
However, you don't want to grow tired of a food if
you buy it too often. Therefore, you will get v[i] −
d[i] × (ti − 1) taste points when you buy the i-th
type of food for the ti-th time.
Find the maximum number of taste points you can
achieve.
##  Input Format
The first line contains an integer, n, denoting the
number of types of food you can buy.
The next line contains an integer, m, denoting
the maximum number of meals you can buy.
Each line i of the n subsequent lines (where 0 ≤ i
< n) contains an integer describing v[i].
Each line i of the n subsequent lines (where 0 ≤ i
< n) contains an integer describing d[i].
Constraints
1 <= n <= 10^5
1 <= m <= 10^9
1 <= v[i] <= 10^9
1 <= d[i] <= 10^9
##  Sample :
3
5
5
7
9
2
4
6
Output:
27
Explanation:
you can buy the 2 meals of the first type and 2
meals of the second type and 1 meal of the third
type and get 27 taste points as follows:
first type: 5 + (5 - 2) * 1 = 8
second type: 7 + (7 - 4) * 1 = 10
third type: 9 = 9
answer: 8 + 10 + 9 = 27


```java
import java.util.*;

class Solution {
    static class Node {
        long val;
        int idx;
        int count;

        Node(long val, int idx, int count) {
            this.val = val;
            this.idx = idx;
            this.count = count;
        }
    }

    public static long maxTaste(int n, long m, int[] v, int[] d) {
        PriorityQueue<Node> pq = new PriorityQueue<>(
            (a, b) -> Long.compare(b.val, a.val)
        );

        // initial push
        for (int i = 0; i < n; i++) {
            pq.add(new Node(v[i], i, 1));
        }

        long ans = 0;

        while (m-- > 0 && !pq.isEmpty()) {
            Node cur = pq.poll();

            if (cur.val <= 0) break;

            ans += cur.val;

            long nextVal = v[cur.idx] - (long)d[cur.idx] * cur.count;

            pq.add(new Node(nextVal, cur.idx, cur.count + 1));
        }

        return ans;
    }
}
```
