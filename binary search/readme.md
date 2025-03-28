# 📌 Binay Search Problems

## 1️⃣ Find First and Last Position of Element in Sorted Array  

### **Approach:**

- Optimized: Use Binary Search O(logn) ✅

 
```js

var searchRange = function(nums, target) {
    let ans = [-1,-1]
    let start = 0;
    let end = nums.length;
    let mid;

    //for first
    while(start<=end){
        mid = start + Math.floor( (end-start)/2 )

        if(nums[mid]==target){
            ans[0] = mid;
            end = mid-1
        }
        else if(nums[mid]>target){
            end = mid-1
        }
        else{
            start = mid+1
        }
    }


    start = 0
    end = nums.length-1

    //for last
    while(start<=end){
        mid = start + Math.floor( (end-start)/2 )

        if(nums[mid]==target){
            ans[1] = mid;
            start = mid+1
        }
        else if(nums[mid]>target){
            end = mid-1
        }
        else{
            start = mid+1
        }
    }

    return ans
};
```



## 2️⃣ Find Insert Position (Leetcode 35)  

### **Approach:**

- Optimized: Use Binary Search O(logn) ✅

- If target is found, return its index.

- If target is not found, return start, because start will be at the correct insertion index.

 
```js

var searchInsert = function(nums, target) {
    let start = 0, end = nums.length-1, mid;

    while(start<=end){
        mid = Math.floor(start+(end-start)/2)

        if(nums[mid]==target){
            return mid
        }else if(nums[mid]<target){
            start = mid+1
        }else{
            end = mid-1
        }
    }

    return start
};
```