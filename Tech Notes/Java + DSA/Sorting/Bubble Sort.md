
- In Bubble sort, traverse from left and compare adjacent elements and the higher one is placed at right side.
- Other name of bubble sort is exchange sort.
- Space complexity is $O(1)$.
- Time complexity is,
	- Best case - $O(n)$.
	- Worst case - $O(n^2)$.
- It is a stable sorting methodology.

### Code 

```java
import java.util.Arrays;  
  
public class bubbleSort {  
    public static void main(String[] args){  
        int[] arr = {5, 3, 4, 1, 2};  
        bubbleSort(arr);  
        System.out.println(Arrays.toString(arr));  
    }  
  
    static  void bubbleSort(int[] arr){  
        boolean swapped = false;  
  
        for(int i = 0; i<arr.length; i++){  
            for(int j = 1; j<arr.length; j++){  
                if(arr[j] < arr[j-1]){  
                    int temp = arr[j];  
                    arr[j] = arr[j-1];  
                    arr[j-1] = temp;  
                    swapped = true;  
                }  
            }  
  
            if(!swapped){  
                break;  
            }  
        }  
    }  
}
```
---
