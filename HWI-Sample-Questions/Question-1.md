#    Question -
##   Easy 
```sql
You have an array A of integers with n elements. There 
are q queries to process and each query consists of four 
integers: l, r, x, and y. 
 For the subarray of A ranging from index l to r, you need to 
assign a sequence of integers for each subsequent element. 
The sequence should start from x and increase by y. This means: 
• A[l] will be assigned the value of x. 
• A[l+1] will be assigned the value of x + y. 
• A[l+2] will be assigned the value of x + 2*y. 
• Continuing this pattern, A[l+i] will be assigned the 
value of x + i*y, where i ranges from 0 to (r - l). 
Find the sum of all integers in A after processing all queries. 
Since answer can be large, return it modulo 109+7. 
Input Format 
1. The first line contains an integer, n, denoting the 
number of elements in A. 
2. Each line i of the n subsequent lines (where 0 ≤ i < n) 
contains an integer describing A[i]. 
3. The next line contains an integer, q, denoting the 
number of rows in queries. 
4. Each line i of the q subsequent lines (where 0 ≤ i < q) 
contains 4 space separated integers each describing 
the row queries[i]. 
5. The 4 space separated integers denote the value of l, r, 
x and y for the i-th query. 
Constraints 
• 1	<=	𝒏	<=	10
• 0	<=	𝑨[𝒊]	<=	10
• 1	≤	𝒒	≤	10
• 0	<=	𝒒𝒖𝒆𝒓𝒊𝒆𝒔[𝒊][𝒋]	<=	10
          Sample Input 1 
5	
5	
5	
0	
3	
0	
5	
0	2	1	2	
0	1	6	5	
2	3	8	0	
2	4	9	6	
3	4	8	9	
          Sample output 1 
51	
```

```java
import java.util.*;

public class question1 {

    static long MOD = 1000000007;

    public static long processQueries(int[] arr, int[][] queries) {

        for (int i = 0; i < queries.length; i++) {

            int l = queries[i][0];
            int r = queries[i][1];
            int x = queries[i][2];
            int y = queries[i][3];

            for (int j = l; j <= r; j++) {
                arr[j] = x + (j - l) * y;
            }
        }

        long sum = 0;

        for (int v : arr) {
            sum = (sum + v) % MOD;
        }

        return sum;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] A = new int[n];

        for (int i = 0; i < n; i++) {
            A[i] = sc.nextInt();
        }

        int q = sc.nextInt();

        int[][] queries = new int[q][4];

        for (int i = 0; i < q; i++) {
            queries[i][0] = sc.nextInt(); // l
            queries[i][1] = sc.nextInt(); // r
            queries[i][2] = sc.nextInt(); // x
            queries[i][3] = sc.nextInt(); // y
        }

        long ans = processQueries(A, queries);

        System.out.println(ans);

        sc.close();
    }
}
```
