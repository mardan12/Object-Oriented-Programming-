# greedy algorithm

## Java SE

### 贪心算法

```java
package tanxin;
import java.util.Arrays;
import java.util.Comparator;
public class EraseOverlapIntervals {
    public static void main(String[] args) {
        int[]arr = {1,5,4,6,8,9};
        int[]arr1 = {9,7,4,3,1,2,5};
        int[][] array = new int[3][3];
        array[0][0] = 3;
        array[0][1] = 2;
        array[0][2] = 7;
        array[1][1] = 6;
        array[2][2] = 1;
        array[1][0] = 8;
        array[2][0] = 9;
        System.out.println(solution(array));
        System.out.println(solution(arr));
        System.out.println(solution(arr, arr1));
    }
    static int solution(int[][]ints){
        Arrays.sort(ints, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[1]-o1[1];
            }
        });
        int count = 0;
        int pre = ints[0][1];
        for (int i = 0; i < ints.length; i++) {
            if (ints[i][0]>=pre){
                count++;
                pre=ints[i][1];
            }
        }
        return ints.length-count;
    }
    static int solution(int[]children,int[]cookies){
        Arrays.sort(children);
        Arrays.sort(cookies);
        int child = 0;
        int cookie = 0;
        while (child<children.length&&cookie<cookies.length){
            if (children[child]<=cookies[cookie++]){
                child++;
            }
        }
        return child;
    }
    static int solution(int[]prices){
        int profit = 0;
        for (int i = 0; i < prices.length-1; i++) {
            if (prices[i]<prices[i+1]){
                profit+=prices[i+1]-prices[i];
            }
        }
        return profit;
    }
}

```

