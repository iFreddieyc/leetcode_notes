# 121. Best Time to Buy and Sell Stock
[Link to the problem](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

The idea is to use **sliding window**.

Create three variables: `left`, `right` and `max_profit`.
`left` means index(day) to buy, `right` means index(day) to sell, and `max_profit` means the max profit so far.

The window: (`left`, `right`) would represent buy stock, hold stock and sell stock. 

Initialize `left` and `max_profit` to zero.
Iterate `prices` from left to right using `right` as index.
                      
If `prices[right]` is less than `prices[left]`, it means there exists a lower price to buy. Thus we should set `left` to `right` as the index of the lowest price so far.
Also, check if `prices[right] - prices[left]` (our profit if we sell today, i.e., at day `right`) is greater than `max_profit`, if so, update `max_profit`.
                      
Python code:
```
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        l = 0
        max_diff = 0
        for r in range(len(prices)):
            if prices[r] < prices[l]:
                l = r
            max_diff = max(max_diff, prices[r] - prices[l])
        return max_diff
```

C++ code:
```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int l = 0;
        int profit = 0;
        for(int r = 0; r < prices.size(); r++){
            if(prices[r] < prices[l]){
                l = r;
            }
            if(prices[r] - prices[l] > profit){
                profit = prices[r] - prices[l];
            }
        }
        return profit;
    }
};
```
