
**Time Complexity :** 
- Best case : O($1$)
- Worst case : O($n$)

**Code :**

```java
class LinearSearch {
    public static void main(String[] args) {
        int[] arr = {18, 12, 4, 9, 21};
        int target = 18;
        int ans = linearSearch(arr, target);
        System.out.println(ans);
    }
    
    
    // search in the array : return the index if item found
    // otherwise if item not found return -1
    static int linearSearch(int[] arr, int target){
        if(arr.length == 0){
            return -1;
        }
        
        //run the for loop
        for(int element : arr){
            //check for element at every index if it is = target
            if(element == target) {
                return i;
            }
        }
        
        //this line will execute if none of the return statements are execued
        // hence the target not found
        return -1;
    }
}
```


## Questions

### Q1. Search in String

```java
class SearchInString {
    public static void main(String[] args) {
        String name = "Sanjith";
        char target = 'a';
        System.out.println(search(name, target));
    }
    
    static boolean search(String str, char target){
        if(str.length()==0){
            return false;
        }
        
        for(char ch : str.toCharArray()){
            if(target == str.charAt(i)){
                return true;
            }
        }
        
        return false;
    }
}
```

---
### Q2. Search in range

```java
class SearchInRange {
    public static void main(String[] args) {
        int[] arr = {18, 12, -7, 3, 14, 28};
        int[] range = {1, 4};
        int target = 3;
        System.out.println(search(arr, range, target));
    }
    
    static boolean search(int[] arr, int[] range, int target){
        if(arr.length==0){
            return false;
        }
        
        for(int i=range[0]; i<=range[1]; i++){
            if(target == arr[i]){
                return true;
            }
        }
        
        return false;
    }
}
```

---
### Q3. Minimun Number

```java
class MinNumber {
    public static void main(String[] args) {
        int[] arr = {18, 12, -7, 3, 14, 28};
        System.out.println(minNum(arr));
    }
    
    static int minNum(int[] arr){
        int min = 0;
        
        for(int i=0; i<arr.length; i++){
            if(i==0 || min>arr[i]){
                min = arr[i];
            }
        }
        
        return min;
    }
}
```

---
### Q4. Search in 2D array

```java
import java.util.*;

class MinNumber {
    public static void main(String[] args) {
        int[][] arr = {
            {18, 12, 14, 28},
            {7, 4, 9},
            {3, 1, 29, 52},
            {16, 42, 2}
        };
        int target = 2;
        int[] ans = search(arr, target);
        System.out.println(Arrays.toString(ans));
    }
    
    static int[] search(int[][] arr, int target){
        
        for(int i=0; i<arr.length; i++){
            for(int j=0; j<arr[i].length; j++){
                if(target == arr[i][j]){
                    return new int[]{i, j};
                }   
            }
        }
        return new int[]{-1, -1};
    }
}
```

---
