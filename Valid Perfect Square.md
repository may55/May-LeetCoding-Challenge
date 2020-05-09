# Valid Perfect Square

Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note: Do not use any built-in library function such as sqrt.

### Example 1:

> Input: 16
> Output: true

### Example 2:

> Input: 14
> Output: false


## Explanation

1. Use binary search to find square root.


## Code:

```
class Solution {
public:
    bool find(int n){
        long long l =1,r=n;
        long long ans = 1;
        while(l<=r){
            long long mid = (l+r)/2;
            if(mid*mid>n){
                r = mid-1;
            }
            else if(mid*mid==n){
                 return true;
            }
            else{
                l = mid+1;
            }
        }
        return false;
    }
    bool isPerfectSquare(int num) {
        return find(num);        
    }
};
```