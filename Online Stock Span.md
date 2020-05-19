# Find All Anagrams in a String

Write a class StockSpanner which collects daily price quotes for some stock, and returns the span of that stock's price for the current day.

The span of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backwards) for which the price of the stock was less than or equal to today's price.

For example, if the price of a stock over the next 7 days were [100, 80, 60, 70, 60, 75, 85], then the stock spans would be [1, 1, 1, 2, 1, 4, 6].

 

### Example 1:

    Input: ["StockSpanner","next","next","next","next","next","next","next"], [[],[100],[80],[60],[70],[60],[75],[85]]
    Output: [null,1,1,1,2,1,4,6]
    Explanation: 
    First, S = StockSpanner() is initialized.  Then:
    S.next(100) is called and returns 1,
    S.next(80) is called and returns 1,
    S.next(60) is called and returns 1,
    S.next(70) is called and returns 2,
    S.next(60) is called and returns 1,
    S.next(75) is called and returns 4,
    S.next(85) is called and returns 6.

    Note that (for example) S.next(75) returned 4, because the last 4 prices
    (including today's price of 75) were less than or equal to today's price.


## Explanation

1. This is nice question using stack.
2. So basically, just maintain the stack in decreasing order.
3. When a number less than the top element came just push it and answer is one.
4. When the number is bigger, pop till the element are less than current element and answer will be the difference between the current index and top element's index.

## Code:

```
class StockSpanner {
public:
    stack<int> st;
    vector<int> arr;
    StockSpanner() {
        while(!st.empty())
            st.pop();
        arr.clear();
    }
    
    int next(int price) {
        arr.push_back(price);
        while(!st.empty() && arr[st.top()]<=price)
            st.pop();
        
        // int ans = arr.size()-1;
        int ans = arr.size() - 1 - (st.empty() ? -1 : st.top());
        st.push(arr.size()-1);
        return ans;
    }
};
```