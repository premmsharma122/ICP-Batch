#    Question -
##    Medium 
```sql
You are given three integers X,Y and Z and two 
arrays A and B both of length N. You are also given an 
integer sum which is initially equal to 0. 
You have perform N operations and in each ith operation you 
must do only one of the following : 
1. Subtract B[i] from sum. 
2. Decrease both of X and Y by 1, then add A[i] * X * Y * 
Z to sum. 
3. Decrease both of Y and Z by 1, then add A[i] * X * Y * 
Z to sum. 
However, after each operation, X,Y and Z must all remain greater 
than or equal to 0. 
Find the maximum sum you can obtain after performing all 
operations. Since answer can be large, return it modulo 109+7. 
Input Format 
1. The first line contains an integer, N, denoting the number of 
operations. 
2. The next line contains an integer, X. 
3. The next line contains an integer,Y. 
4. The  next line contains an integer, Z. 
5. Each line i of the N subsequent lines (where 1 ≤ i ≤ N) 
contains an integer describing A[i]. 
6. Each line i of the N subsequent lines (where 1 ≤ i ≤ N) 
contains an integer describing B[i]. 
Constraints 
• 1	<=	𝑁	<=	10 
• 1	<=	𝑿	<=	10 
• 1	<=	𝒀	<=	10 
• 1	<=	𝒁	<=	10 
• 1	<=	𝑨[𝒊]	<=	10 
• 1	<=	𝑩[𝒊]	<=	10 
Sample Input-1: 
2	
1	
2	
2	
0	
0	
10	
5
Sample output-1: 
0	
 
Explanation-1: 
Here, N = 2, X = 1, Y = 2, Z = 2 
A = [0, 0] 
B = [10, 5] 
 
It is given that in starting, sum = 0 
 
operation 1: 
Apply type 2 operation (i.e. Decrease both of X and Y by 1, then 
add A[1]*X*Y*Z to sum) 
X = 0, Y = 1, Z = 2 
sum = sum + 0*0*1*2 = 0 
 
operation 2: 
Apply type 3 operation (i.e. Decrease both of Y and Z by 1, 
then add A[2]*X*Y*Z to sum) 
X = 0, Y = 0, Z = 1 
sum = sum + 0*0*0*1 = 0 
 
Hence, answer is the final value of sum i.e. sum = 0.
```
```java
import java.util.*;

public class question2 {

    static long mod = 1000000007;

    public static long help(int n, int x, int y, int z, int A[], int B[], int idx, long sum){

        if(idx == n){
            return sum;
        }

        // operation 1
        long ans1 = help(n, x, y, z, A, B, idx+1, sum - B[idx]);

        long ans2 = Long.MIN_VALUE;
        long ans3 = Long.MIN_VALUE;

        // operation 2 (decrease X,Y first)
        if(x >= 1 && y >= 1){
            long val = (long)A[idx] * (x-1) * (y-1) * z;
            ans2 = help(n, x-1, y-1, z, A, B, idx+1, sum + val);
        }

        // operation 3 (decrease Y,Z first)
        if(y >= 1 && z >= 1){
            long val = (long)A[idx] * x * (y-1) * (z-1);
            ans3 = help(n, x, y-1, z-1, A, B, idx+1, sum + val);
        }

        return Math.max(ans1, Math.max(ans2, ans3));
    }

    public static void main(String args[]){

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int x = sc.nextInt();
        int y = sc.nextInt();
        int z = sc.nextInt();

        int A[] = new int[n];
        int B[] = new int[n];

        for(int i=0;i<n;i++){
            A[i] = sc.nextInt();
        }

        for(int i=0;i<n;i++){
            B[i] = sc.nextInt();
        }

        long ans = help(n, x, y, z, A, B, 0, 0);

        ans = ((ans % mod) + mod) % mod;

        System.out.println(ans);
    }
}
```
