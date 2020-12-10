# [2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

## 题目

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```
Explanation: 342 + 465 = 807.


## 题目大意

2 个逆序的链表，要求从低位开始相加，得出结果也逆序输出，返回值是逆序结果链表的头结点。

1.需要创建一个ListNode 的指针head做为l1->val 和l2->val 相加所得到的链表的头结点

2.一个ListNode 的指针pur永远指向我们创造的新的链表的末尾

3.一个ListNode 的指针s存放i = l1->val + l2->val 取余的结果 将 i = i/10 存放进位再一个一个地添加到pur的next域

4.注意在最后要将pur的next域置为NULL，返回head->next

5.在进行while的时候要注意情况l1 l2都为空但进位非空时也要进行

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */


struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2){
    struct ListNode *head, *s, *pur; int i;
    head = (struct ListNode *)malloc(sizeof(struct ListNode));
    pur = head;
    i = 0;
    while(l1  || l2 || i){
        if(l1 != NULL){
            i += l1->val;
            l1 = l1->next;
        }
        if(l2 != NULL){
            i += l2->val;
            l2 = l2->next;
        }
        s = (struct ListNode *)malloc(sizeof(struct ListNode));
        s->val = i%10;
        pur->next = s;
        pur = s;
        i = i/10;
        
    }
    pur->next = NULL;
   return head->next;
}
```

