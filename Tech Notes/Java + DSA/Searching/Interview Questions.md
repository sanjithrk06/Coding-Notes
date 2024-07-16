
# Binary Search

### Q1. Ceiling of a Number
#array 

```java
public class ceilingOfNum {  
    public static void main(String[] args) {  
        int[] arr = {1, 4, 7, 12, 17, 22};  
        int val = -2;  
  
        int res = insertAt(arr, val);  
        System.out.println(res);  
    }  
  
    static int insertAt(int[] arr, int val){  
        int s = 0, e = arr.length - 1;  
  
        if (val < arr[s]) return 0;  
        else if (val > arr[e]) return arr.length;  
  
        while(s<=e){  
            int mid = s + (e-s)/2;  
  
            if( arr[mid] >= val && arr[mid-1] <val) return mid;  
            else if (arr[mid] > val) e = mid-1;  
            else s = mid+1;  
        }  
  
        return -1;  
    }  
}
```

---
### Q4. [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) (34)
#array #sorting 

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int[] res = new int[2];
        res[0] = binarySearch(nums, target, -1);
        res[1] = binarySearch(nums, target, 1);
        return res;
    }

    int binarySearch(int[] nums, int target, int flag){
        int len = nums.length;
        int l=0, r=len-1, ans = -1;

        while(l<=r){
            int m = l + (r-l)/2;

            if(nums[m]==target){
                ans = m;
                if(flag == 1) l = m+1;
                else r = m-1;
            }else if(nums[m]>target) r = m-1;
            else l = m+1;
        }

        return ans;
    }
}
```
---
## Q5. Find the position of an element in an infinite sorted array


```java
public class binaryInfiniteArray {  
    public static void main(String[] args) {  
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20};  
  
        int target = 9;  
  
        System.out.println(result(arr, target));  
    }  
  
    static int result(int[] arr, int target){  
        int start = 0, end = 1;  
        while(target > arr[end]){  
            int nStart = end+1;  
            end += ((end-start)+1)*2;  
            start = nStart;  
        }  
  
        return binarySearch(arr, target, start, end);  
    }  
  
    static int binarySearch(int[] arr, int target, int start, int end){  
        while(start<=end){  
            int mid = start + (end-start)/2;  
  
            if(arr[mid] > target) end = mid-1;  
            else if(arr[mid] < target) start = mid+1;  
            else return mid;  
        }  
  
        return 0;  
    }  
}
```

---
## Q6. [Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/) (852)

```java
class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        int s = 0, e = arr.length - 1;

        while(s<=e){
            int m = s+ (e-s)/2;

            if(arr[m] > arr[m+1]){
                if(arr[m] > arr[m-1]){
                    return m;
                }else e = m - 1;
            }else if(arr[m] < arr[m+1]){
                s = m + 1;
            }
        }

        return -1;
    }
}
```
---

