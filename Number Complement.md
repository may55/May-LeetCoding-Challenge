#   Number Complement


Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

 

### Example 1:

>Input: 5
>Output: 2
>Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.

 

### Example 2:

>Input: 1
>Output: 0
>Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.





## Explanation

1. Simply change number to decimal in compliment form.
2. Pop extra zero bits from front.
3. Convert the number form binary to decimal.


## Code:

```
class Solution {
public:
    int findComplement(int num) {
        string s;
        while(num){
            if(num&1)
                s.push_back('0');
            else
                s.push_back('1');
            num /= 2;
        }
        int res = 0;
        while(s.size() && s.back()=='0')
            s.pop_back();
        reverse(s.begin(),s.end());        
        for(auto it: s){
            res *= 2;
            if(it-'0')
                res++;
        }
        return res;
    }
};
```