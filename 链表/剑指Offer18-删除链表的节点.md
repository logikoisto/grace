# [剑指 Offer 18. 删除链表的节点](!https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/)
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func deleteNode(head *ListNode, val int) *ListNode {
    if head == nil{
        return head
    }
    dummy := &ListNode{
        Next:head,
    }
    pre := dummy
    for pre != nil && pre.Next != nil{
        if pre.Next.Val == val{
            pre.Next = pre.Next.Next
            continue
        }
        pre = pre.Next
    }
    return dummy.Next
}
```