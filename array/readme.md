# 📌 Arrays Problems

## 1️⃣ Two Sum  
🔗 **[Leetcode 1](https://leetcode.com/problems/two-sum/)**

### **Approach:**
- Brute Force: Try all pairs (O(n²))
- Optimized: Use HashMap (O(n)) ✅
- Ek HashMap (map) use karenge jo har number ka index store karega.
- Har number ke liye check karenge ki (target - current number) pehle se map me hai ya nahi.
- Agar hai, toh answer mil gaya! ✅
- Agar nahi, toh current number ko map me store kar lenge.  

```js
function twoSum(nums, target) {
    let map = new Map();
    for (let i = 0; i < nums.length; i++) {
        let second = target - nums[i];
        if (map.has(second)) {
            return [map.get(second), i];
        }
        map.set(nums[i], i);
    }
    return [];
}
```

## 2️⃣ Best Time To Buy And Sell Stocks

### **Approach:**
- Brute Force: Try all pairs using two nested loop (O(n²))
- Optimized: (O(n)) ✅
- Track karna hain min price, har din taki buy price minimum ho.
- Calculate max profit har din using (current price - minPrice).

```js
var maxProfit = function(arr) {
    let profit=0
    let maxProfit=0
    let minPrice = Infinity

    for(let i=0; i<arr.length; i++){
        minPrice = Math.min(minPrice, arr[i])
        profit = arr[i] - minPrice
        maxProfit = Math.max(maxProfit, profit)
    }

    return maxProfit
};
```


