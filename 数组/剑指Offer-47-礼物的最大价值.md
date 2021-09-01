# [剑指 Offer 47.礼物的最大价值](https://leetcode-cn.com/problems/li-wu-de-zui-da-jie-zhi-lcof/)

``` go
func maxValue(grid [][]int) int {
    if len(grid) == 0{
        return 0
    }
    dp := make([][]int,len(grid))
    for i := 0; i < len(dp); i++{
        dp[i] = make([]int, len(grid[0]))
    }
    dp[0][0] = grid[0][0]
    for i := 1; i < len(grid[0]);i++{
        dp[0][i] = grid[0][i] + dp[0][i-1]
    }
    for i := 1; i < len(grid);i++{
        dp[i][0] = grid[i][0] + dp[i-1][0]
    }
    // dp[i][j] = max(dp[i-1][j], dp[i][j-1]) + grid[i][j]
    for i := 1; i < len(dp);i++{
        for j := 1; j < len(dp[0]);j++{
            dp[i][j] = max(dp[i-1][j], dp[i][j-1]) + grid[i][j]
        }
    }
    return dp[len(dp)-1][len(dp[0])-1]
}
func max(a, b int)int{
    if a > b{
        return a
    }
    return b
}
```