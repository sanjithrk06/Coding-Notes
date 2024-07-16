
**Time Complexity :** 
- Best case : O($1$)
- Worst case : O($log(n)$)

==**The array must be sorted first to be able to apply binary search**==
#### Steps
- Find the middle element.
- Check if target > mid => search in the right, else search in left.
- If middle element == target element return it.

#### Code

```java
public class binarySearch {  
    public static void main(String[] args) {  
        int[] arr = {-14, -3, 3, 7, 13, 18};  
        int target = 13;  
  
        int res = binary(arr, target);  
        System.out.println(res);  
    }  
  
    static int binary(int[] arr, int target){  
        int s = 0;  
        int e = arr.length -1;  
  
        while(s<=e){  
            //find the middle element  
            // int mid = (s + e) / 2; // might be possible that (s+e) might exceed the integer value limit            int m = s + (e-s) / 2;  
  
            if (target < arr[m]) e = m-1;  
            else if (target > arr[m]) s = m+1;  
            else return m;  
        }  
  
        return -1;  
    }  
}
```

---
### Order Agnostic Binary Search

- Implementing the binary search for all type of sorted arrays(i.e. ascending or descending).

**Code**

```java
public class orderAgnosticBinarySearch {  
    public static void main(String[] args) {  
        int[] arr = {-14, -3, 3, 7, 13, 18};  
        int target = 13;  
  
        int res = orderAgnosticBS(arr, target);  
        System.out.println(res);  
    }  
  
    static int orderAgnosticBS(int[] arr, int target){  
        int s = 0;  
        int e = arr.length -1;  
        boolean isAsc = arr[s] < arr[e];  
  
        while(s<=e){  
            //find the middle element  
            // int mid = (s + e) / 2; // might be possible that (s+e) might exceed the integer value limit            int m = s + (e-s) / 2;  
  
            if(arr[m] == target) return m;  
  
            if(isAsc) {  
                if (target < arr[m]) e = m - 1;  
                else s = m + 1;  
            }else{  
                if (target > arr[m]) e = m - 1;  
                else s = m + 1;  
            }  
        }  
  
        return -1;  
    }  
}
```

---
