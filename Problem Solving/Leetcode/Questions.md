
**([[#THE END|Navigate to End]])**

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
// Code 1
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

// Code 2
class Solution {
    public int searchInsert(int[] nums, int target) {
        int res = insertAt(nums, target);

        return res;
    }

    int insertAt(int[] arr, int val){
        int s = 0, e = arr.length - 1;

        if (val <= arr[s]) return 0;
        else if (val > arr[e]) return arr.length;
        else if (s==e) return 0;

        while(s<=e){
            int mid = s + (e-s)/2;

            if(arr[mid] >= val && arr[mid-1] < val) return mid;
            else if (arr[mid] > val) e = mid-1;
            else s = mid+1;
        }

        return -1;
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
## 15. [Sort Colors](https://leetcode.com/problems/sort-colors/) (75)
#array  #twoPointer  #sorting 

```java
class Solution {
    public void sortColors(int[] nums) {
        Arrays.sort(nums);
    }
}
```
---
## 16. [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) (33)
#array #sorting #binarySearch 

```java
class Solution {
    public int search(int[] nums, int target) {
        int len = nums.length;
        int l = 0, r = len-1, mid;
  
        while(l<=r) {
            mid = (l+r)/2;
            if(nums[mid] == target) return mid;
            if (nums[l] <= nums[mid]) {
                if (nums[l] <= target && target < nums[mid]) r = mid-1;
                else l = mid+1;
            } else {
                if (nums[mid] < target && target <= nums[r]) l = mid+1;
                else r = mid-1;
            }
        }
  
        return -1;
    }
}
```
---
## 17. [Summary Ranges](https://leetcode.com/problems/summary-ranges/) (228)
#array #arrayList

```java
class Solution {
    public List<String> summaryRanges(int[] nums) {
        List<String> str = new ArrayList<>();
        int l = 0, r = 0;
  
        for (int i = 1; i <= nums.length; i++) {
            if (i == nums.length || nums[i] - nums[r] != 1) {
                if (nums[l] == nums[r]) {
                    str.add(Integer.toString(nums[l]));
                    l = i;
                } else {
                    str.add(Integer.toString(nums[l])+"->"+Integer.toString(nums[r]));
                    l = i;
                }
            }
            r = i;
        }
        return str;
    }
}
```
---
## 18. [Merge Intervals](https://leetcode.com/problems/merge-intervals/) (56)
#array #sorting 

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
  
        List<int[]> res = new ArrayList<>();
        int[] prev = intervals[0];
  
        for (int i = 1; i < intervals.length; i++) {
            int[] interval = intervals[i];
            if (interval[0] <= prev[1]) {
                prev[1] = Math.max(prev[1], interval[1]);
            } else {
                res.add(prev);
                prev = interval;
            }
        }
  
        res.add(prev);
  
        return res.toArray(new int[res.size()][]);        
    }
}
```
---
## 19.  [Distance Between Bus Stops](https://leetcode.com/problems/distance-between-bus-stops/) (1184)
#array 

```java
class Solution {
    public int distanceBetweenBusStops(int[] distance, int start, int destination) {
        int dis1 = 0;
        int dis2 = 0;
        int k = destination;
        for(int i = 0; i < distance.length; i++){
            if(start <= i && i < k || start > i && i >= k){
                dis1 += distance[i];
            }else{
                dis2 += distance[i];
            }
        }
        if(dis1 > dis2) return dis2;
        return dis1;
    }
}
```
---
## 20. [Maximum Product of Three Numbers](https://leetcode.com/problems/maximum-product-of-three-numbers/) (628)
#array #math #sorting 

```java
class Solution {
    public int maximumProduct(int[] nums) {
        Arrays.sort(nums);
  
        int len = nums.length;
  
        return Math.max(nums[len-1]*nums[len-2]*nums[len-3], nums[0]*nums[1]*nums[len-1]);
    }
}
```
---
## 21.  [Largest Number At Least Twice of Others](https://leetcode.com/problems/largest-number-at-least-twice-of-others/) (747)
#array #sorting 

```java
class Solution {
    public int dominantIndex(int[] nums) {
        int max1 = Integer.MIN_VALUE, max2 = Integer.MIN_VALUE, ind = 0;
  
        for(int i=0; i<nums.length; i++) {
            if(i==0 || nums[i] > max1) {
                max2 = max1;
                max1 = nums[i];
                ind = i;
            }else if (nums[i] > max2) {
                max2 = nums[i];
            }
        }
  
        if(max2*2 <= max1) return ind;
  
        return -1;
    }
}
```
---
## 22. [Monotonic Array](https://leetcode.com/problems/monotonic-array/) (896)
#array 

```java
class Solution {
    public boolean isMonotonic(int[] nums) {
        int n = nums.length;
        if (n == 1) return true;
  
        boolean isInc = true;
        boolean isDec = true;
  
        for (int i = 1; i < n; i++) {
            if (!isInc && !isDec) {
                return false;
            }
  
            if (nums[i] < nums[i - 1]) {
                isInc = false;
            }
            if (nums[i] > nums[i - 1]) {
                isDec = false;
            }
        }
  
        return isInc || isDec;        
    }
}
```
---
## 23. [Minimum Number of Moves to Seat Everyone](https://leetcode.com/problems/minimum-number-of-moves-to-seat-everyone/) (2037)
#array #sorting 

```java
class Solution {
    public int minMovesToSeat(int[] seats, int[] students) {
        Arrays.sort(seats);
        Arrays.sort(students);
  
        int moves = 0;
        for(int i=0; i<seats.length; i++) {
            moves += Math.abs(seats[i] - students[i]);
        }
  
        return moves;
    }
}
```

---
## 24. [Assign Cookies](https://leetcode.com/problems/assign-cookies/) (455)
#array  #sorting 

```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int j = 0, gLen = g.length, sLen = s.length;
        for(int i = 0; i < sLen; i++){
            if(j < gLen && g[j] <= s[i]){
                j++;
            }
        }
        return j;
    }
}
```

---
## 25. [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) (121)
#array 

```java
class Solution {
    public int maxProfit(int[] prices) {
        int buy = prices[0], len = prices.length, max = 0;
  
        for(int i=1; i<len; i++) {
            if(buy > prices[i]) buy = prices[i];
            max = Math.max(max, prices[i] - buy);
        }
  
        return max;
    }
}
```

---
## 26. [Rectangle Area](https://leetcode.com/problems/rectangle-area/) (223)
#math #geometry

```java
class Solution {
    public int computeArea(int ax1, int ay1, int ax2, int ay2, int bx1, int by1, int bx2, int by2) {
        int areaA, areaB;
  
        areaA = (ax2-ax1) * (ay2-ay1);
        areaB = (bx2-bx1) * (by2-by1);
  
        if(ax2<bx1 && ay2<by1) {
            return areaA + areaB;
        }
  
        int l, w, areaM = 0;
  
        l = Math.min(ax2, bx2) - Math.max(ax1, bx1);
        w = Math.min(ay2, by2) - Math.max(ay1, by1);
  
        if (l>0 && w>0) {
            areaM = l*w;
        }
  
        return areaA + areaB - areaM;
    }
}
```

---
## 27. [Power of Three](https://leetcode.com/problems/power-of-three/) (326)
#math #recursion

```java
class Solution {
    public boolean isPowerOfThree(int n) {
        if (n%3 != 0 && n!=1) return false;
        double t = n;
  
        while(t>=3){
            t /= 3;
        }
  
        if(t==1.00) return true;
  
        return false;
    }
}
```

---
## 28. [Length of Last Word](https://leetcode.com/problems/length-of-last-word/) (58)
#string

```java
class Solution {
    public int lengthOfLastWord(String s) {
        s = s.trim();
        int len = 0;
        for (int i = s.length() - 1; i >= 0; i--) {
            if (s.charAt(i) != ' ') len++;
            else if (len > 0) break;
        }
        return len;
    }
}
```

---
## 29. [Ugly Number](https://leetcode.com/problems/ugly-number/) (263)
#math  

```java
class Solution {
    public boolean isUgly(int n) {
        if (n<1) return false;
  
        while(n%2==0) n/=2;
        while(n%3==0) n/=3;
        while(n%5==0) n/=5;
  
        if (n==1) return true;
        return false;
    }
}
```

---

## 30. [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/) (118)
#array  #dynamicProgramming

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> result = new ArrayList<>();
        if (numRows == 0) {
            return result;
        }
  
        List<Integer> firstRow = new ArrayList<>();
        firstRow.add(1);
        result.add(firstRow);
  
        for (int i = 1; i < numRows; i++) {
            List<Integer> prevRow = result.get(i - 1);
            List<Integer> currentRow = new ArrayList<>();
            currentRow.add(1);
  
            for (int j = 1; j < i; j++) {
                currentRow.add(prevRow.get(j - 1) + prevRow.get(j));
            }
  
            currentRow.add(1);
            result.add(currentRow);
        }
  
        return result;
    }
}
```

---
## 31. [Valid Anagram](https://leetcode.com/problems/valid-anagram/) (242)
#string 

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        char[] sArr = s.toCharArray();
        char[] tArr = t.toCharArray();
        Arrays.sort(sArr);
        Arrays.sort(tArr);
  
        return Arrays.equals(sArr, tArr);
    }
}


// Best Option
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] m = new int[128];
        for (char ch : s.toCharArray()) m[ch]++;
        for (char ch : t.toCharArray()) {
            if (--m[ch] < 0) return false;
        }
        return true;
    }
}
```

---
## 32. [Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/) (349)
#array #hashSet #sorting 

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> res = new HashSet<Integer>();
  
        for(int i=0; i<nums1.length; i++) {
            for(int j =0; j<nums2.length; j++) {
                if(nums1[i] == nums2[j]) {
                    res.add(nums1[i]);
                    break;
                }
            }
        }
  
        int[] arr = res.stream().mapToInt(Integer::intValue).toArray();
  
        return arr;
    }
}
```

---

## 33. [Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/) (1752)
#array 

**My Solution :**
```java
class Solution {
    public boolean check(int[] nums) {
        int k = nums.length-1;
  
        for(int i=1; i<nums.length; i++) {
            if(nums[k] >= nums[i] && nums[i-1]>nums[i]) {
                k = i;
            }
        }
  
        for(int i=0; i<nums.length-1; i++) {
            int ind = (k+i)%nums.length;
            int nxt = (k+i+1)%nums.length;
            if(nums[ind] > nums[nxt]) {
                return false;
            }
        }
  
        return true;
    }
}
```

**Best Solution :**
```java
class Solution {
    public boolean check(int[] nums) {
        int ans = 0, size = nums.length;
  
        if (nums[0] < nums[size - 1]) {
            ans++;
        }
  
        for (int i = 1; i < size; i++) {
            if (nums[i - 1] > nums[i]) {
                ans++;
  
                if (ans > 1) {
                    return false;
                }
            }
        }
  
        return true;
    }
}
```

---
## 34. [Rotate Array](https://leetcode.com/problems/rotate-array/) (189)
#array 

```java
class Solution {
    public void rotate(int[] nums, int k) {
        int[] res = new int[nums.length];
        Arrays.fill(res, 0);
  
        for(int i=0; i<nums.length; i++) {
            res[(i+k)%nums.length] = nums[i];
        }
  
        for(int i=0; i<nums.length; i++) {
            nums[i] = res[i];
        }
    }
}
```

---
## 35. [Missing Number](https://leetcode.com/problems/missing-number/) (268)

```java
class Solution {
    public int missingNumber(int[] nums) {
        int res = nums.length;
        for (int i = 0; i < nums.length; i++) {
            res += i - nums[i];
        }
        return res;      
    }
}
```

---
## 36. [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) (287)

```java
class Solution {
    public int findDuplicate(int[] nums) {
        Arrays.sort(nums);
        for(int i=0;i<nums.length-1;i++)
            if(nums[i] == nums[i+1]) return nums[i];
        return -1;
    }
}
```

---
## 37. [Single Number](https://leetcode.com/problems/single-number/) (136)
#array 

```java
class Solution {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);
  
        for(int i=0; i<nums.length-1; i++) {
            if(nums[i] != nums[i+1]) return nums[i];
            if(nums[i] == nums[i+1]) i++;
        }
  
        return nums[nums.length-1];
    }
}
```

---
## 38. [Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/) (2149)
#array #twoPointer 

```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        ArrayList<Integer> posArr = new ArrayList<Integer>();
        ArrayList<Integer> negArr = new ArrayList<Integer>();
  
        for(int i=0; i<nums.length; i++) {
            if(nums[i]>0) posArr.add(nums[i]);
            else negArr.add(nums[i]);
        }
  
        int p=0, n=0;
  
        for(int i=0; i<nums.length; i++) {
            if(i==0 || i%2==0) nums[i] = posArr.get(p++);
            else nums[i] = negArr.get(n++);
        }
  
        return nums;
    }
}
```

**Best Approach :**
```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int even = 0, odd = 1;
        int[] ans = new int[nums.length];
  
        for(int i = 0; i < nums.length; i++){
            if(nums[i] < 0){
                ans[odd] = nums[i];
                odd += 2;
            }else{
                ans[even] = nums[i];
                even += 2;
            }
        }
        return ans;
    }
}
```

---
## 39. [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/) (448)

```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        boolean[] isAvailable = new boolean[nums.length];
        for(int i=0;i<nums.length;i++){
            isAvailable[nums[i]-1] = true;
        }
        List<Integer> ans = new ArrayList<>();
        for(int i=0;i<isAvailable.length;i++){
            if(!isAvailable[i]){
                ans.add(i+1);
            }
        }
        return ans;
    }
}
```

---
## 40. [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) (74)
#array  #binarySearch 

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if(target<matrix[0][0]) return false;
  
        int ind = 0;
        for(int i=0; i<matrix.length; i++) {
            if(i==matrix.length-1 && target >=matrix[i][0]) {
                ind = i;
                break;
            }else if(target >= matrix[i][0] && target < matrix[i+1][0]) {
                ind = i;
                break;
            }
        }
  
        int l=0, r=matrix[ind].length-1;
  
        while(l<=r) {
            int mid = (l+r)/2;
  
            if(matrix[ind][mid]==target) return true;
            else if(target > matrix[ind][mid]) l=mid+1;
            else if(target < matrix[ind][mid]) r = mid-1;
        }
  
        return false;
    }
}
```
---
## 41. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (41)
#array 

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        Arrays.sort(nums);
        int ind=-1;
  
        for(int i=0; i<nums.length; i++) {
            if(nums[i] == 1) {
                ind = i;
                break;
            }else if(i==nums.length-1) return 1;
        }
        int k=1;
        for(int i=0; i<nums.length-ind; i++){
            if(nums[i+ind] < k) continue;
            else if(nums[i+ind] != k) return k;
            k++;
        }
  
        return nums[nums.length-1]+1;
    }
}
```
---
## 42. [Majority Element](https://leetcode.com/problems/majority-element/) (169)
#array 

```java
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
  
        int count=0, maxCount = 0, val = nums[0], maxVal = nums[0];
        for(int i=1; i<nums.length; i++) {
            if(nums[i-1] == nums[i]){
                count++;
                val = nums[i];
            }
            else count =0;
            if(count>maxCount){
                maxCount=count;
                maxVal = val;
            }
        }
  
        return maxVal;
    }
}
```
---
## 43. [Majority Element II](https://leetcode.com/problems/majority-element-ii/) (229)
#array #sorting #counting

```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        ArrayList<Integer> res = new ArrayList<Integer>();
        Arrays.sort(nums);
  
        int count=0, tar = nums.length/3;
        for(int i=0; i<nums.length; i++) {
            if(i==0 || nums[i-1] == nums[i]){
                count++;
            }
            else count =1;
            if(count>tar && !res.contains(nums[i])) {
                res.add(nums[i]);
            }
        }
  
        return res;
    }
}
```
---
## 44. [Insert Interval](https://leetcode.com/problems/insert-interval/) (57)
#array #sorting 

```java
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        ArrayList<int[]> arr = new ArrayList<int[]>();
        boolean flag = false;
  
        for(int i=0; i<intervals.length; i++){
            int[] interval = intervals[i];
  
            if(newInterval[0] > interval[1]) {
                arr.add(interval);
            }else if(newInterval[1] < interval[0]){
                if(!flag) {
                    arr.add(newInterval);
                    flag=true;
                }
                arr.add(interval);
            }else {
                newInterval[0] = Math.min(newInterval[0], interval[0]);
                newInterval[1] = Math.max(newInterval[1], interval[1]);
            }
        }
  
        if(!flag) arr.add(newInterval);
  
        return arr.toArray(new int[arr.size()][]);
    }
}
```
---
## 45. [Sqrt(x)](https://leetcode.com/problems/sqrtx/) (69)

```java
class Solution {
    public int mySqrt(int x) {
        if (x == 0) {
            return 0;
        }
        int first = 1, last = x;
        while (first <= last) {
            int mid = first + (last - first) / 2;
            if (mid == x / mid) {
                return mid;
            } else if (mid > x / mid) {
                last = mid - 1;
            } else {
                first = mid + 1;
            }
        }
        return last;
    }
}
```
---
## 46.  [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/) (350)
#array #sorting 

```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);
  
        ArrayList<Integer> res = new ArrayList<>();
        int i = 0, j = 0;
        int n1 = nums1.length, n2 = nums2.length;
  
        while (i < n1 && j < n2) {
            if (nums1[i] == nums2[j]) {
                res.add(nums1[i]);
                i++;
                j++;
            } else if (nums1[i] < nums2[j]) {
                i++;
            } else {
                j++;
            }
        }
  
        int[] result = new int[res.size()];
        for (int k = 0; k < res.size(); k++) {
            result[k] = res.get(k);
        }
  
        return result;
    }
}
```
---
## 47. [Binary Search](https://leetcode.com/problems/binary-search/) (704)
#array #binarySearch 

```java
class Solution {
    public int search(int[] nums, int target) {
        int l=0, r=nums.length-1;
  
        while(l<=r) {
            int mid = (l+r)/2;
  
            if(nums[mid]==target) {
                return mid;
            }else if(nums[mid]>target) {
                r=mid-1;
            }else {
                l=mid+1;
            }
        }
  
        return -1;
    }
}
```
---
## 48. [Maximum Count of Positive Integer and Negative Integer](https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/)
#array 

```java
class Solution {
    public int maximumCount(int[] nums) {
        int pCount =0, nCount=0;
  
        for(int num: nums){
            if(num>0) pCount++;
            else if(num<0) nCount++;
        }
  
        return Math.max(pCount, nCount);
    }
}
```
## 49. [Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)
#string #array

```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        char ind='z';
        int f=0; 
        for(char ch: letters) {
            if((int)ch > (int)target) {
                if((int)ch <= (int)ind) {
                    ind = ch;
                    f=1;
                }
            }
        }

        if(f==0) ind = letters[0];

        return ind;
    }
}
```
---
## 50. [Check If N and Its Double Exist](https://leetcode.com/problems/check-if-n-and-its-double-exist/) (1346)
#array

```java
class Solution {
    public boolean checkIfExist(int[] arr) {
        for(int i=0; i<arr.length; i++){
            for(int j=i+1; j<arr.length; j++){
                if(arr[i] == arr[j]*2 || arr[j] == arr[i]*2) return true;
            }
        }

        return false;
    }
}
```
---
## 51. [Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/) (171)
#string 

```java
class Solution {
    public int titleToNumber(String columnTitle) {
        int res = 0;
  
        for(char str : columnTitle.toUpperCase().toCharArray()) {
            res *= 26;
            res += str - 'A' + 1;
        }
  
        return res;
    }
}
```
---
## 52. [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) (238)
#array 

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] ans = new int[nums.length];
        int n= nums.length;
        int zCount =0, zInd=0, product=1;
  
        for(int i=0; i<n; i++){
            if(nums[i]==0){
                zCount++;
                zInd = i;
            }else {
                product *= nums[i];
            }
        }
  
        if(zCount==1){
            ans[zInd] = product;
            return ans;
        }else if(zCount>1){
            return ans;
        }else{        
            for(int i = 0; i < n; i++) {
                ans[i] = product/nums[i];
            }
        }
  
        return ans;
    }
}
```
---
## 53. [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/) (8)
#string 

```java
class Solution {
    public int myAtoi(String s) {
        int l = s.length();
        int res = 0, sign = 1, i = 0;
  
        while (i < l && s.charAt(i) == ' ') {
            i++;
        }
  
        if (i < l && (s.charAt(i) == '-' || s.charAt(i) == '+')) {
            sign = (s.charAt(i) == '-') ? -1 : 1;
            i++;
        }
  
        while (i < l && Character.isDigit(s.charAt(i))) {
            int digit = s.charAt(i) - '0';
  
            if (res > (Integer.MAX_VALUE - digit) / 10) {
                return (sign == 1) ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
  
            res = res * 10 + digit;
            i++;
        }
  
        return res * sign;
    }
}
```
---
## 54. [Find Numbers with Even Number of Digits](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/) (1295)
#array 

```java
class Solution {
    public int findNumbers(int[] nums) {
        int count=0;
  
        for(int n: nums){
            if(even(n)) count++;
        }
  
        return count;
    }
  
    boolean even(int num){
        int digit = digit(num);
  
        if(digit%2 == 0) return true;
  
        return false;
    }
  
    int digit(int num){
        return (int)(Math.log10(num)+1);
    }
}
```

---
## 55. [Group Anagrams](https://leetcode.com/problems/group-anagrams/) (49)
#sorting  #array #string 

```java

// without using hash map
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        int l = strs.length;
        int[] flag= new int[l];
        Arrays.sort(strs);
  
        List<List<String>> res = new ArrayList<List<String>>();
  
        for(int i=0; i<l; i++){
            if(flag[i] == 1) continue;
            List<String> str = new ArrayList<String>();
            str.add(strs[i]);
            for(int j=0; j<l; j++){
                if(j==i) continue;
                if(isAnagram(strs[i], strs[j])){
                    str.add(strs[j]);
                    flag[j] = 1;
                }
            }
            res.add(str);
        }
  
        return res;
    }
  
    boolean isAnagram(String s, String t) {
        char[] sarr = s.toCharArray();
        char[] tarr = t.toCharArray();
        Arrays.sort(sarr);
        Arrays.sort(tarr);
  
        if(sarr.length != tarr.length) return false;
  
        for(int i=0; i<sarr.length && i<tarr.length; i++){
            if(sarr[i]!=tarr[i]){
                return false;
            }
        }
  
        return true;
    }
}


// Using hash map
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> res = new ArrayList<>();
        HashMap<String, Integer> hm = new HashMap<>();
  
        int ind=0;
        for(String str : strs){
            char[] s = str.toCharArray();
            Arrays.sort(s);
            String st = new String(s);
  
            if(hm.containsKey(st)){
                res.get(hm.get(st)).add(str);
            }else{
                hm.put(st, ind);
                res.add(new ArrayList<>());
                res.get(ind).add(str);
                ind++;
            }
        }
  
        return res;
    }
}
```
---
## 56. [Find Resultant Array After Removing Anagrams](https://leetcode.com/problems/find-resultant-array-after-removing-anagrams/) (2273)
#array #hashMap #string #anagram

```java
class Solution {
    public List<String> removeAnagrams(String[] words) {
        List<String> res = new ArrayList<>();
        HashMap<String, Integer> mp = new HashMap<>();
  
        int k=0;
        for(String str : words){
            char[] s = str.toCharArray();
            Arrays.sort(s);
            String st = new String(s);
  
            if(mp.containsKey(st)){
                continue;
            }else{
                mp.clear();
                mp.put(st, k++);
                res.add(str);
            }
        }
  
        return res;
    }
}
```
---
## 57. [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) (11)
#array 

```java
class Solution {
    public int maxArea(int[] height) {
        int n=height.length;
        int l=0, r=n-1, max = Integer.MIN_VALUE;

        while(l<r){
            int a = Math.min(height[l], height[r]);
            int area = a*(r-l);

            if(max<area) max = area;

            if(height[l]<height[r]) l++;
            else r--;
        }

        return max;
    }
}
```
---
## 58. [Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/) (1672)
#array 

```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int max = Integer.MIN_VALUE;

        for(int i=0; i<accounts.length; i++){
            int wealth = 0;
            for(int j=0; j<accounts[i].length; j++){
                wealth += accounts[i][j];
            }

            if(wealth > max) max = wealth;
        }

        return max;
    }
}
```
---
## 59. [Roman to Integer](https://leetcode.com/problems/roman-to-integer/) (13)
#array #string 

```java
class Solution {
    public int romanToInt(String s) {
        char[] str = s.toCharArray();

        int sum = 0;
        for(int i=0; i<str.length; i++){
            int s1 = value(str[i]);

            if(i+1 < str.length){
                int s2 = value(str[i+1]);

                if(s1 < s2){
                    sum += (s2-s1);
                    i++;
                }else{
                    sum +=s1;
                }
            }else{
                sum+=s1;
            }
        }

        return sum;
    }

    int value(char ch){
        switch(ch){
            case 'I': return 1;
            case 'V': return 5;
            case 'X': return 10;
            case 'L': return 50;
            case 'C': return 100;
            case 'D': return 500;
            case 'M': return 1000;
        }

        return 0;
    }
}
```
---
## 60. [Integer to Roman](https://leetcode.com/problems/integer-to-roman/) (12)
#string #array 

```java
class Solution {
    public String intToRoman(int num) {
        StringBuilder res = new StringBuilder();
        int[] val = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        String[] sym = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};

        for(int i=0; i<13; i++){
            int di = num/val[i];
            num = num%val[i];
            while(di>0){
                res.append(sym[i]);
                di--;
            }
        }
        return res.toString();
    }
}
```
---
## 61. [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) (34)
#array #sorting #binarySearch 

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
## 62. [Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/) (852)
#array #binarySearch 

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
## 63. [Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/) (540)
#array #binarySearch 

```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int len = nums.length;
        if(len==1) return nums[0];
        if(nums[0]!=nums[1]) return nums[0];
        if(nums[len-2] != nums[len-1]) return nums[len-1];
        int s = 0, e = len-1;

        while(s<=e){
            int m = s + (e-s)/2;

            if(nums[m] == nums[m+1]){
                if(m%2==0) s = m+1;
                else e = m-1;
            }else if(nums[m] == nums[m-1]){
                if((m-1)%2==0) s = m+1;
                else e = m-1;
            }else return nums[m];
        }

        return nums[0];
    }
}
```
---
## 64. [Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/) (81)
#array #binarySearch 

```java
class Solution {
    public boolean search(int[] nums, int target) {
        int len = nums.length;

        int l = 0, r = len-1;

        while(l<=r){
            int m = l + (r-l)/2;

            if(nums[m] == target || nums[l] == target || nums[r] == target) return true;

            if(nums[l] == nums[m] && nums[m] == nums[r]){
                l++;
                r--;
                continue;
            }else if(nums[l] <= nums[m]) {
                if(nums[l] <= target && target < nums[m]) r = m-1;
                else l = m + 1;
            }else {
                if(nums[m] < target && target <= nums[r]) {
                    l = m+1;
                }
                else r = m-1;
            }
        }

        return false;
    }
}
```

---
## 65. [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) (153)
#array #binarySearch 

```java
class Solution {
    public int findMin(int[] nums) {
        int n = nums.length;
        int l=0, r=n-1;

        while(l<=r){
            int mid = l + (r-l)/2;

            if(nums[mid] <= nums[r]){
                if(mid == 0 || nums[mid] < nums[mid-1]) return nums[mid];
                else r = mid-1;
            }else l = mid+1;
        }

        return -1;
    }
}
```
---
## 66. [Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/) (11)
#array #binarySearch 

```java
class Solution {
    public int shipWithinDays(int[] weights, int days) {
        int max = Integer.MIN_VALUE, sum = 0;

        for(int i=0; i<weights.length; i++){
            if(weights[i] > max) max = weights[i];
            sum += weights[i];
        }

        if(days==1) return sum;

        int low = max, high = sum, res = sum;

        while(low<=high){
            int mid = low + (high - low)/2;

            if(isShip(weights, mid, days)){
                res = mid;
                high = mid-1;
            }else low = mid+1;
        }

        return res;
    }

    boolean isShip(int[] weights, int max, int days){
        int count = 0, sum = 0;

        for(int i=0; i<weights.length; i++){
            if(count >= days) return false;
            if((sum + weights[i]) > max){
                sum = 0;
                count++;
            }
            sum += weights[i];
        }
        if(count >= days) return false;

        return true;
    }
}
```
---
## 67. [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/) (875)
#array #binarySearch 

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        Arrays.sort(piles);
        int maxEl = piles[piles.length-1];
        
        int l = 1, r = maxEl, res = 0;

        while(l<=r){
            int m = l + (r-l)/2;

            int totHrs = findHrs(m, piles);

            if(totHrs <= h){
                res = m;
                r = m-1; 
            }else{
                l = m+1;
            }
        }

        return res;
    }

    int findHrs(int m, int[] piles){
        int cnt = 0;

        for(int i:piles){
            cnt += Math.ceil((double) i / m);
        }

        return cnt;
    }
}
```

---
## 68. [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) (74)
#array #binarySearch #2Darray 

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int l = 0, r = matrix.length-1;

        while(l<=r){
            int m = l + (r-l)/2;

            if(matrix[m][0] <= target){
                if(matrix[m][matrix[m].length-1] >= target){
                    return bs(matrix[m], target);
                }else{
                    l = m+1;
                }
            }else{
                r = m-1;
            }
        }

        return false;
    }

    boolean bs(int[] matrix, int target){
        int l = 0, r = matrix.length-1;

        while(l<=r){
            int m = l + (r-l)/2;

            if(matrix[m] > target) r = m-1;
            else if(matrix[m] < target) l = m+1;
            else return true;
        }

        return false;
    }
}
```

---
## 70. [Find in Mountain Array](https://leetcode.com/problems/find-in-mountain-array/) (1095)
#binarySearch #array 

```java
/**
 * // This is MountainArray's API interface.
 * // You should not implement it, or speculate about its implementation
 * interface MountainArray {
 *     public int get(int index) {}
 *     public int length() {}
 * }
 */
 
class Solution {
    public int findInMountainArray(int target, MountainArray mountainArr) {
        int peak = peakIndex(mountainArr);
        if(mountainArr.get(peak) < target) return -1;
        int len = mountainArr.length();

        int left = binarySearch(target, mountainArr, 0, peak);
        int right = binarySearch(target, mountainArr, peak+1, len-1);

        if(left < 0 && right >= 0) return right;
        else if(left >= 0 && right < 0) return left;
        else if(left >= 0 && right >= 0) return Math.min(left, right);

        return -1;
    }

    int peakIndex(MountainArray arr){
        int s = 0, e = arr.length()-1;

        while(s<=e){
            int m = s + (e-s)/2;

            if(arr.get(m) > arr.get(m+1)){
                if(arr.get(m-1) < arr.get(m)) return m;
                else e = m-1;
            }else s = m+1;
        }

        return -1;
    }

    int binarySearch(int target, MountainArray arr, int s, int e){
        int l = s, r = e;

        if(arr.get(l) >= arr.get(r)){
            while(l<=r){
                int m = l + (r-l)/2;

                if(arr.get(m) > target) l = m+1;
                else if(arr.get(m) < target) r = m-1;
                else return m;
            }
        }else{
            while(l<=r){
                int m = l + (r-l)/2;

                if(arr.get(m) > target) r = m-1;
                else if(arr.get(m) < target) l = m+1;
                else return m;
            }
        }

        return -1;
    }
}
```

---
## 71. [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/) (401)
#array #binarySearch 

```java
class Solution {
    public int splitArray(int[] nums, int k) {
        int start = 0, end = 0;

        for(int num : nums){
            start = Math.max(num, start);
            end += num;
        }

        while(start < end){
            int mid = start + (end-start)/2;

            int count = 1, sum = 0;
            for(int num : nums){
                if(sum + num > mid){
                    sum = num;
                    count++;
                }else sum += num;
            }

            if(count > k) start = mid + 1;
            else end = mid;
        }

        return end;
    }
}
```

---
## 72. [3Sum](https://leetcode.com/problems/3sum/) (15)
#array #arrayList 

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res=new ArrayList<>();
        
        Arrays.sort(nums);
        
        for(int i=0;i<nums.length;i++){
            if(i>0 && nums[i]==nums[i-1]) continue;
            
            int j=i+1;
            int k=nums.length-1;
            
            while(j<k){
                if(nums[i]+nums[j]+nums[k] > 0){
                    k--;
                } else if(nums[i]+nums[j]+nums[k] < 0){
                    j++;
                } else{
                    List<Integer> arr = new ArrayList<Integer>();
                    arr.add(nums[i]);
                    arr.add(nums[j]);
                    arr.add(nums[k]);
                    res.add(arr);
                    j++;
                    k--;
                    while(j<k&& nums[j]==nums[j-1]) j++;
                    while(j<k&& nums[k]==nums[k+1]) k--;

                }
            }
        }
        
        return res;
    }
}
```

---
## 73. [Sort an Array](https://leetcode.com/problems/sort-an-array/) (912)
#array #sorting 

```java
class Solution {
    public int[] sortArray(int[] nums) {
        mergeSort(nums, 0, nums.length-1);
        return nums;
    }
    public void mergeSort(int []arr, int low, int high){
        if(low >= high) return;

        int mid = (low+high)/2;
        mergeSort(arr, low, mid);
        mergeSort(arr, mid+1, high);
        merge(arr, low, high, mid);
    }
    public void merge(int []arr, int low, int high, int mid){
        ArrayList<Integer> temp = new ArrayList<>();
        int left = low;
        int right = mid+1;

        while(left <= mid && right <= high){
            if(arr[left] <= arr[right]){
                temp.add(arr[left]);
                left++;
            }else{
                temp.add(arr[right]);
                right++;
            }
        }
        while(left <= mid){
            temp.add(arr[left]);
            left++;
        }
        while(right <= high){
            temp.add(arr[right]);
            right++;
        }
        for(int i=low; i<= high; i++){
            arr[i] = temp.get(i-low);
        }
    }
}
```

---
## 74. [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/) (448)
#array #sorting #cyclicSort

```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> res = new ArrayList<>();

        int i=0;
        while(i<nums.length){
            int cInd = nums[i]-1;
            if(cInd >= nums.length) {
                i++;
                continue;
            }
            if(nums[i] != nums[cInd]){
                swap(nums, i, cInd);
            }else i++;
        }

        for(int k=0; k<nums.length; k++){
            if(k+1 != nums[k]) res.add(k+1);
        }

        return res;
    }

    void swap(int[] arr, int f, int s){
        int temp = arr[f];
        arr[f] = arr[s];
        arr[s] = temp;
    }
}
```
---
## 75. [Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/) (442)
#array #duplicates #cyclicSort 

```java
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        int k = 0;
        while(k<nums.length){
            int cInd = nums[k]-1;
            if(cInd >= nums.length) {
                k++;
                continue;
            }
            if(nums[k] != nums[cInd]){
                swap(nums, k, cInd);
            }else k++;
        }

        List<Integer> res = new ArrayList<>();
        for(int i=0; i<nums.length; i++){
            if(i+1 != nums[i]) res.add(nums[i]);
        }

        return res;
    }

    void swap(int[] arr, int f, int s){
        int t = arr[f];
        arr[f] = arr[s];
        arr[s] = t;
    }
}
```
---

## 76. [Set Mismatch](https://leetcode.com/problems/set-mismatch/) (645)
#array #cyclicSort 

```java
class Solution {
    public int[] findErrorNums(int[] nums) {
        int k = 0;
        while(k<nums.length){
            int cInd = nums[k]-1;
            if(cInd >= nums.length) {
                k++;
                continue;
            }
            if(nums[k] != nums[cInd]){
                swap(nums, k, cInd);
            }else k++;
        }

        List<Integer> res = new ArrayList<>();
        for(int i=0; i<nums.length; i++){
            if(i+1 != nums[i]) {
                res.add(nums[i]);
                res.add(i+1);
            }
        }

        int[] arr = new int[res.size()];
        for (int i = 0; i < res.size(); i++) {
            arr[i] = res.get(i);
        }

        return arr;
    }

    void swap(int[] arr, int f, int s){
        int t = arr[f];
        arr[f] = arr[s];
        arr[s] = t;
    }
}
```
---
## 77. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (41)
#array #cyclicSort 

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int k = 0;
        while(k<nums.length){
            int cInd = nums[k]-1;
            if(cInd >= nums.length || cInd < 0) {
                k++;
                continue;
            }
            if(nums[k] != nums[cInd]){
                swap(nums, k, cInd);
            }else k++;
        }

        for(int i=0; i<nums.length; i++){
            if(i+1 != nums[i]) return i+1;
        }

        return nums.length+1;
    }

    void swap(int[] arr, int f, int s){
        int t = arr[f];
        arr[f] = arr[s];
        arr[s] = t;
    }
}
```
---
## 78. [Neither Minimum nor Maximum](https://leetcode.com/problems/neither-minimum-nor-maximum/) 
#array 

```java
class Solution {
    public int findNonMinOrMax(int[] nums) {
        if(nums.length==2||nums.length==1)return -1;
        int min = Integer.MAX_VALUE;
        int max = Integer.MIN_VALUE;
        int n = 0;
        for(int i = 0;i<nums.length;i++){
            max = Math.max(max,nums[i]);
            min = Math.min(min,nums[i]);

        }
        
        for(int j = 0;j<nums.length;j++){
            if(nums[j]!=min&&nums[j]!=max){
                n = nums[j];

            }
        }
      
        return n;
    }
}
```
---
## 79. [Recyclable and Low Fat Products](https://leetcode.com/problems/recyclable-and-low-fat-products/)
#database #sql

```SQL
SELECT product_id from Products WHERE low_fats = 'Y' AND recyclable = 'Y'
```

---
## 80. [Find Customer Referee](https://leetcode.com/problems/find-customer-referee/)
#database #sql 

```SQL
SELECT name FROM Customer
WHERE referee_id != 2 OR referee_id is null
ORDER BY name;
```

---
## 81. [Big Countries](https://leetcode.com/problems/big-countries/)
#database #sql 

```SQL
SELECT name, population, area from World
WHERE population >= 25000000 OR area >= 3000000
ORDER BY name;
```

---
## 82. [Article Views I](https://leetcode.com/problems/article-views-i/)
#database #sql 

```SQL
SELECT DISTINCT author_id as id from Views
WHERE author_id = viewer_id
ORDER BY id;
```

---
## 83. [Invalid Tweets](https://leetcode.com/problems/invalid-tweets/)
#database #sql 

```SQL
SELECT tweet_id FROM Tweets
WHERE LENGTH(content) > 15;
```

---
## 84. [Replace Employee ID With The Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/)
#database #sql 

```sql
SELECT EmployeeUNI.unique_id, Employees.name 
FROM Employees
LEFT JOIN EmployeeUNI 
ON EmployeeUNI.id = Employees.id;
```

---
## 85. [Product Sales Analysis I](https://leetcode.com/problems/product-sales-analysis-i/)
#database #sql 

```sql
SELECT Product.product_name, Sales.year, Sales.price 
FROM Sales
INNER JOIN Product
ON Product.product_id = Sales.product_id;
```

---
## 86. [Customer Who Visited but Did Not Make Any Transactions](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/) 
#database #sql 

```sql
SELECT v.customer_id, COUNT(v.customer_id) as count_no_trans
FROM Visits v
LEFT JOIN Transactions t
ON v.visit_id = t.visit_id
WHERE t.transaction_id IS NULL
GROUP BY v.customer_id
```

---
## 87. 



























---
### THE END
