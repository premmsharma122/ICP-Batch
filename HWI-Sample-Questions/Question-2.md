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
