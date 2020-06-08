# Count square submatrices with all ones
## https://leetcode.com/problems/count-square-submatrices-with-all-ones


## Implementation : Time : O(rows * columns)  , Space : O(rows * columns)
```java
class Solution {
    public int countSquares(int[][] matrix) {
        if(matrix == null || matrix.length == 0)
            return 0;
        int rows = matrix.length;
        int columns = matrix[0].length;
        int total = 0;
        int[][] dp = new int[rows+1][columns+1];
        
        for(int i = 1; i <= rows; i++) {
            for(int j = 1; j <= columns; j++) {
                if(matrix[i-1][j-1] == 1) {
                    int min = Math.min(dp[i][j-1], dp[i-1][j]);
                    min = Math.min(min, dp[i-1][j-1]);
                    dp[i][j] = min + 1;
                    total += dp[i][j];
                }
            }
        }
        return total;
    }
}
```

# References :
https://www.youtube.com/watch?v=7xMVc2lPXhI
