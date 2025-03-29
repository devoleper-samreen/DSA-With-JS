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


## 3️⃣ Best Time To Buy And Sell Stocks II

### **Approach:**

- Track karna hain min price, har din taki buy price minimum ho.
- Price increase hote hi turant sell karna hain
- Then next buy karna hain and sell karna hain
- All sell ka profit calculate karna hain


```js
var maxProfit = function(arr) {
    let minPrice = Infinity
    let profit = 0

    
    for(let i=0; i<arr.length; i++){
        minPrice = Math.min(minPrice, arr[i])

        if(arr[i]>minPrice){
            profit += arr[i] - minPrice;
            minPrice = arr[i]
        }
    }

    return profit
    
};
```



## 3️⃣ Majority Element (n/2)

### **Approach:**

- Ek candidate le lo (start me koi bhi) aur count 1 rakho

- Same element mile to count++ karo, nahi mila to count-- karo

- Agar count 0 ho jaye, to new candidate le lo

- End tak jo candidate bachega, wahi majority element hoga


```js

var majorityElement = function(nums) {
    let count = 0, candidate = null

    for(let num of nums){
        if(count===0){
            candidate = num
        }

        count += (num===candidate)?1 : -1
    }

    return candidate
    
};
```



## 3️⃣ Rotate Array  (n/2)

### **Approach:**

- Pura array reverse karo

- First k elements reverse karo

- Last n-k elements reverse karo


```js

function reverse(nums, s, e){
    while(s<=e){
        [nums[s], nums[e]] = [nums[e], nums[s]]
        s++
        e--
    }
}

var rotate = function(nums, k) {
    const n = nums.length

    if(n==1){
        return 
    }

    k = k%n

    //reverse full array
    reverse(nums, 0, n-1)

    //reverse first k element
    reverse(nums, 0, k-1)

    //reverse k to n element 
    reverse(nums, k, n-1)
};
```

