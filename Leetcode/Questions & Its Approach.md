
## 1. Two Sum (1)
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
## 2. Remove Duplicates from Sorted Array (26)
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
## 3. Palindrome Number (9)
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
## 4. Reverse Integer (7)
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
## 5. Remove Element (27)
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
