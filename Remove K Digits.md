#   Remove K Digits

Given a non-negative integer num represented as a string, remove k digits from the number so that the new number is the smallest possible.

Note:

    The length of num is less than 10002 and will be ≥ k.
    The given num does not contain any leading zero.



### Example 1:

    Input: num = "1432219", k = 3
    Output: "1219"
    Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.

### Example 2:

    Input: num = "10200", k = 1
    Output: "200"
    Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.


### Example 3:

    Input: num = "10", k = 2
    Output: "0"
    Explanation: Remove all the digits from the number and it is left with nothing which is 0.



## Explanation

1. There are multiple ways to solve this question.
2. Basically insert every character in the ans if and only if the last char is less than the current one.
3. Remember not to insert leading zero.

## Code:

```
class Solution {
public:
    string removeKdigits(string num, int k) {
        string ans = "";         
        
       
       for (char ch: num) {
           while (ans.length() && ans.back() > ch && k) {
               ans.pop_back();                                  
               k--;                                            
           }
           
           if (ans.length() || ch != '0') { ans.push_back(ch); }  
       }
       
       while (ans.length() && k--) { ans.pop_back(); }          
       
       return ans.empty() ? "0" : ans;
        
    }
};
```