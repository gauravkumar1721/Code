# Code
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> nextLargerNodes(ListNode* head) {
       vector<int> V;
        stack<int> S;
        if(!head) return V;
        while(head!=NULL){
            while(S.empty() == false && V[S.top()]<head->val){
                
               V[S.top()]=head->val;
                S.pop();
            }
            S.push(V.size());
            V.push_back(head->val);
            head=head->next;
        }
        while(S.empty() == false){
       V[S.top()]=0;
            S.pop();
        }
      return V;      
    }
};
