# Odd Even Linked List

Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.

You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.

### Example 1:

    Input: 1->2->3->4->5->NULL
    Output: 1->3->5->2->4->NULL

### Example 2:

    Input: 2->1->3->5->6->4->7->NULL
    Output: 2->3->6->7->1->5->4->NULL


## Explanation

1. Take two pointers and jump twice for each after maintaining the next pointer.

## Code:

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        ListNode *odd,*even,*temp1,*temp2;
        if(head==NULL) return NULL;
        
        if(head->next==NULL) return head;
        
        odd = head;
        even = head->next;
        
        temp1 = odd;
        temp2 = even;
        
        while(temp1 && temp2){
            temp1->next = temp2->next;
            if(temp1->next){
                temp1 = temp1->next;
            }
            else
                break;
            if(temp1){
                temp2->next = temp1->next;
                if(temp2->next){
                    temp2 = temp2->next;
                    // break;
                }
                else
                    break;
            }
        }
        temp1->next = even;
        temp2->next = NULL;
        return odd;
        
        
    }
};
```