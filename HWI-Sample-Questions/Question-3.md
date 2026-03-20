#    Questuin -
##    Hard
```sql
You are given a tree with n nodes rooted at node 1. You are also 
given an array color representing the colour of each node in the 
tree.   
A set of nodes is beautiful if it satisfies the following conditions: 
• All nodes in the set have different colors. 
• For any pair of nodes (u, v), either u is the ancestor of v or v is 
the ancestor of u within the tree. 
You're given q queries where each query provides an 
integer s representing a node in the tree. 
The answer to each query is the maximum size of a beautiful 
set that can be formed by selecting nodes from the subtree 
rooted at node s. 
Find the sum of answers to all queries. Since answer can be 
large, return it modulo 109+7. 
Notes: 
• The parent of node 1 is 0. 
Input Format 
• The first line contains an integer, N, denoting the number of 
operations. 
• The next line contains an integer, X. 
• The next line contains an integer,Y. 
• The  next line contains an integer, Z. 
• Each line i of the N subsequent lines (where 1 ≤ i ≤ N) 
contains an integer describing A[i]. 
• Each line i of the N subsequent lines (where 1 ≤ i ≤ N) 
contains an integer describing B[i]. 
Constraints 
• 1	<=	𝑁	<=	10 
• 1	<=	𝑿	<=	10 
• 1	<=	𝒀	<=	10 
• 1	<=	𝒁	<=	10 
• 1	<=	𝑨[𝒊]	<=	10 
• 1	<=	𝑩[𝒊]	<=	10 
Sample Input-1: 
		 5	
				0	
				1	
				2	
				1	
				3	
				4	
				3	
				4	
				3	
				5
		        3	
				4	
				3	
				3	
 
Sample output-1: 
5 
Sample Explanation - 1: 
Here, n = 5 
p = [0, 1, 2, 1, 3] 
color = [4, 3, 4, 3, 5] 
q = 3 
queries = [4, 3, 3] 
for query 1: 
    s = 4, means we need to select beautiful set of maximum size 
in the subtree of node 4. 
    we can select nodes {4} to form beautiful set of maximum size. 
    so, answer for this query is 1. 
 
for query 2: 
    s = 3, means we need to select beautiful set of maximum size in 
the subtree of 3. 
    we can select nodes {3, 5} to form beautiful set of maximum 
size. 
    so, answer for this query is 2. 
 
for query 3: 
    s = 3, means we need to select beautiful set of maximum size in 
the subtree of 3. 
    we can select nodes {3, 5} to form beautiful set of maximum 
size. 
    so, answer for this query is 2. 
 
Hence, answer is 1 + 2 + 2 = 5. 
```
```java
import java.util.*;

public class question3 {

    static int n;
    static int[] color;
    static List<Integer>[] tree;
    static int maxSize;

    static void dfs(int node, Set<Integer> usedColors) {

        int c = color[node];

        if (usedColors.contains(c)) {
            return;
        }

        usedColors.add(c);

        maxSize = Math.max(maxSize, usedColors.size());

        for (int child : tree[node]) {
            dfs(child, usedColors);
        }

        usedColors.remove(c); // backtrack
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        n = sc.nextInt();

        int[] parent = new int[n + 1];

        for (int i = 1; i <= n; i++) {
            parent[i] = sc.nextInt();
        }

        color = new int[n + 1];

        for (int i = 1; i <= n; i++) {
            color[i] = sc.nextInt();
        }

        tree = new ArrayList[n + 1];

        for (int i = 1; i <= n; i++) {
            tree[i] = new ArrayList<>();
        }

        for (int i = 2; i <= n; i++) {
            tree[parent[i]].add(i);
        }

        int q = sc.nextInt();

        long ans = 0;
        long mod = 1000000007;

        for (int i = 0; i < q; i++) {

            int s = sc.nextInt();

            maxSize = 0;

            dfs(s, new HashSet<>());

            ans = (ans + maxSize) % mod;
        }

        System.out.println("ans"+ ans);
    }
}
```
