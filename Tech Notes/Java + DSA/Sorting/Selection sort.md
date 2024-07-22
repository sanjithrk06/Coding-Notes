
- **Selection sort** is a simple and efficient sorting algorithm that works by repeatedly selecting the smallest (or largest) element from the unsorted portion of the list and moving it to the sorted portion of the list.
- **Time Complexity** - $O(n^2)$
- **Space Complexity** - $O(1)$
- It is unstable.
- **Use Case:**
	- It performs well in the small array.

### Code
```java
import java.util.*;  
  
public class selectionSort {  
    public static void main(String[] args){  
        Scanner in = new Scanner(System.in);  
  
//        int arrSize = in.nextInt();  
//        int[] arr = new int[arrSize];  
  
//        for(int i=0; i<arrSize; i++){  
//            arr[i] = in.nextInt();  
//        }  
  
        int[] arr = {3, 1, 4, 2, 5};  
  
        selection(arr);  
  
        System.out.println(Arrays.toString(arr));  
    }  
  
    static void selection(int[] arr){  
        for(int i=0; i<arr.length; i++){  
            int last = arr.length - i - 1;  
            int maxIndex = getMax(arr, last+1);  
            swap(arr, maxIndex, last);  
        }  
    }  
  
    static void swap(int[] arr, int first, int second){  
        int temp = arr[first];  
        arr[first] = arr[second];  
        arr[second] = temp;  
    }  
  
    static int getMax(int[] arr, int e){  
        int max = 0;  
        for(int i=0; i<e; i++){  
            if(arr[i] > arr[max]) max = i;  
        }  
  
        return max;  
    }  
}
```

---
