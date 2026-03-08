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
