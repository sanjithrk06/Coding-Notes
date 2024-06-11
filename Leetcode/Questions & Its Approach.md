
## 1. [Two Sum](https://leetcode.com/problems/two-sum/) (1)
#array

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] res = {0, 0};
        int len = nums.length;
  
        for(int i=0; i<len-1; i++){
            for(int j=i+1; j<len && i!=j; j++){
                if(nums[i] + nums[j] == target) {
                    res[0] = i;
                    res[1] = j;
                    return res;
                }
            }
        }

        return res;
    }
}
```


---
## 2. [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) (26)
#array 

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int len = nums.length;
        int i=1, j=1;
  
        while(i<len && j<=i) {
            if (nums[i] == nums[i-1]) {
                i++;
                continue;
            }
            nums[j++] = nums[i++];
        }
  
        return j;
    }
}
```


---
## 3. [Palindrome Number](https://leetcode.com/problems/palindrome-number/) (9)
#math

```java
class Solution {
    public boolean isPalindrome(int x) {
        if(x<0) return false;
        int temp = x, rev = 0;
        while(temp>0){
            int rem = temp%10;
            rev = rev*10 + rem;
            temp /= 10;
        }
  
        if (x == rev) return true;
  
        return false;        
    }
}
```

---
## 4. [Reverse Integer](https://leetcode.com/problems/reverse-integer/) (7)
#math 

```java
class Solution {
    public int reverse(int x) {
        int flag=0;
        if(x<0) flag=1;
  
        int temp=Math.abs(x);
        long rev = 0;
  
        while(temp>0) {
            int rem = temp%10;
            rev = rev*10 + rem;
            temp /= 10;
  
            if(rev > Integer.MAX_VALUE || rev < Integer.MIN_VALUE) return 0;
        }
  
        if(flag==1) rev = -rev;
  
        return (int)rev;
    }
}
```

---
## 5. [Remove Element](https://leetcode.com/problems/remove-element/) (27)
#array 

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int len = nums.length, i=0, j=0;
  
        while(i<len && j<=i) {
            if(nums[i] == val) {
                i++;
                continue;
            }
            nums[j++] = nums[i++];
        }
  
        return j;
    }
}
```

---
## 6.  [Search Insert Position](https://leetcode.com/problems/search-insert-position/) (35)
#array #binarySearch

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int len = nums.length;
        if (nums[0] > target) return 0;
        if (nums[len-1] < target) return len;
  
        int l=0, r=len-1, mid;
  
        while(l<=r) {
            mid = (l+r)/2;
  
            if (nums[mid] == target) return mid;
            if (nums[mid] > target) {
                if (nums[mid-1] < target) return mid;
                r=mid;
            }
            if (nums[mid] < target)
                if (nums[mid+1] > target) return mid+1;
                l=mid+1;
            }
        }
  
        return 0;
    }
}
```

---
## 7. [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) (88)
#array #twoPointer #sorting

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int[] res = new int[m+n];
        int j=0;
  
        for(int i=m; i<n+m; i++) {
            nums1[i] = nums2[i-m];
        }
  
        Arrays.sort(nums1);
    }
}
```

---
## 8. [Third Maximum Number](https://leetcode.com/problems/third-maximum-number/) (414)
#array  #sorting 

```java
class Solution {
    public int thirdMax(int[] nums) {
        long max1=Long.MIN_VALUE;
        long max2=Long.MIN_VALUE;
        long max3=Long.MIN_VALUE;
        for(int num : nums){
            if(num>max1){
                max3 = max2;
                max2 = max1;
                max1 = num;
            }else if(max1>num && num>max2){
                max3 = max2;
                max2 = num;
            }else if(max2>num && num>max3){
                max3=num;
            }
        }
        return max3 != Long.MIN_VALUE ? (int) max3 : (int) max1;
    }
}
```

---
## 9.  [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) (217)
#array #sorting #hashTable

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        for(int i=0; i<nums.length-1; i++){
            if(nums[i] == nums[i+1]) return true;
        }
  
        return false;
    }
}
```
---
## 10. [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/) (4)
#array 

```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int len = nums1.length + nums2.length;
        int[] arr = new int[len];

        for(int i=0; i<nums1.length; i++){
            arr[i] = nums1[i];
        }
  
        int j = nums1.length;
        for(int i=0; i<nums2.length; i++){
            arr[i+j] = nums2[i];
        }
  
        Arrays.sort(arr);

        int mid = len/2;
        if (len%2==0) {
            return (double)(arr[mid] + arr[mid-1])/2.0;
        }else {
            return (double)arr[mid];
        }
    }
}
```
---
## 11. [Move Zeroes](https://leetcode.com/problems/move-zeroes/) (283)
#array #twoPointer 

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int len = nums.length, i=0, j=1;
  
        while(j!=len && i!=len && i<=j) {
            if (nums[i] == 0) {
                if (nums[j] == 0) j++;
                else {
                    int temp = nums[i];
                    nums[i++] = nums[j];
                    nums[j++] = temp;
                }
            }else {
                i++;
                j++;
            }
        }
  
    }
}
```
---
## 12. [Plus One](https://leetcode.com/problems/plus-one/) (66)
#array #math 

```java
class Solution {
    public int[] plusOne(int[] digits) {
        int len = digits.length;
        if ( digits[len-1] != 9) {
            digits[len-1]++;
            return digits;
        }

        int i=len-1, c=1;
        while(i>=0) {
            if (c==0) break;
            if(digits[i] == 9) {
                digits[i] = 0;
                i--;
            }else {
                digits[i] += c;
                c=0;
            }
        }
  
        if(c==1) {
            int[] res = new int[len+1];
            res[0] = 1;
            for(int j=0; j<len; j++) {
                res[j+1] = digits[j];
            }
  
            return res;
        }else return digits;
    }
}
```
---
## 13. [Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/) (485)
#array 

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count=0, max = 0;
        for(int i=0; i<nums.length; i++) {
            if(nums[i] == 1) {
                count++;
                if(i==nums.length-1 && max<count) {
                    max = count;
                }
            }
            else {
                if (max<count) max=count;
                count=0;
            }
        }
  
        return max;
    }
}
```
---
## 14. [Duplicate Zeros](https://leetcode.com/problems/duplicate-zeros/) (1089)
#array #twoPointer 

```java
class Solution {
    public void duplicateZeros(int[] arr) {
        int[] temp = arr.clone();
        int len = arr.length, i=0;
  
        for(int j=0; i<len; j++){
            arr[i++] = temp[j];
            if(temp[j] == 0 && i!=len) {
                arr[i++] = 0;
            }
        }
    }
}
```
---
