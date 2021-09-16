# https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func pathSum(root *TreeNode, target int) [][]int {
    res := make([][]int, 0)
    ret := make([]int, 0)
    var help func(node *TreeNode, sum int)
    help =  func(node *TreeNode, sum int){
        if node == nil {
            return
        }
        sum -= node.Val
        ret = append(ret, node.Val)
        defer func() { ret = ret[:len(ret)-1] }()
        if node.Left == nil && node.Right == nil && sum  == 0{
            res = append(res, append([]int(nil), ret...)) 
            return 
        }
        help(node.Left,  sum)
        help(node.Right, sum)
    }
    help(root, target)
    return res
}
```