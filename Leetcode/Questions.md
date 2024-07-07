
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

---
### THE END