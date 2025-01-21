# Leetcode---2017
Grid Game
// code in java
class Solution {
    public long gridGame(int[][] grid) {
        int n = grid[0].length;
        long[] prefixSumTop = new long[n + 1];
        long[] prefixSumBottom = new long[n + 1];
        
        for (int i = 0; i < n; i++) {
            prefixSumTop[i + 1] = prefixSumTop[i] + grid[0][i];
            prefixSumBottom[i + 1] = prefixSumBottom[i] + grid[1][i];
        }
        
        long result = Long.MAX_VALUE;
        
        for (int i = 0; i < n; i++) {
            long topPath = prefixSumTop[n] - prefixSumTop[i + 1];
            long bottomPath = prefixSumBottom[i];
            result = Math.min(result, Math.max(topPath, bottomPath));
        }
        
        return result;
    }
}
