
### What is pivot?
- Choose any element.
- All the elements < pivot will be on LHS of Pivot.
- All the elements > pivot will be on RHS of Pivot.

### How to pick pivot?
- Random element.
- Corner element.
- Pick the middle element.

```java
import java.util.Arrays;  
  
public class quickSort {  
    public static void main(String[] args) {  
        int[] arr = {3,2,3,1,2,4,5,5,6};  
  
        sort(arr, 0, arr.length-1);  
  
        System.out.println(Arrays.toString(arr));  
    }  
  
    static void sort(int[] arr, int low, int high){  
        if(low>=high) return;  
        int s = low, e = high;  
        int m = s + (e-s)/2;  
        int p = arr[m];  
  
        while(s<=e){  
            while(arr[s] < p) s++;  
            while(arr[e] > p) e--;  
  
            if(s<=e) {  
                int temp = arr[s];  
                arr[s] = arr[e];  
                arr[e] = temp;  
                s++;  
                e--;  
            }  
        }  
  
        sort(arr, low, e);  
        sort(arr, s, high);  
    }  
}
```

