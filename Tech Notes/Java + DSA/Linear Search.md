
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

