
## 1. Recursive Fibonacci Sequence Generator

Imagine you are developing a program to calculate Fibonacci numbers for a mathematical modeling application. Your function needs to efficiently compute Fibonacci numbers up to a large index requested by the user.

**Solution :**
```c
// 1) Using recursion

#include <stdio.h>

int fib(int n){
    if(n==0){
        return 0;
    }else if(n==1){
        return 1;
    }
    
    return fib(n-1) + fib(n-2);
}

int main() {
    int num;
    scanf("%d", &num);
    
    printf("Result : %d", fib(num));

    return 0;
}


// 2) Normal function Method

// Online C compiler to run C program online
#include <stdio.h>

int fib(int num) {
    int t1=0, t2=1, t3;
    
    if(num==0) {
        return t1;
    }
    
    for(int i=2; i<=num; i++){
        t3 = t1+t2;
        t1 = t2;
        t2 = t3;
    }
    
    return t2;
}

int main() {
    
    int num;
    scanf("%d", &num);
    
    printf("Result : %d", fib(num));

    return 0;
}
```

**Test Case 1:** 
Input: 6 
Output: 8 (fibonacci(6) = 8) 

**Test Case 2:** 
Input: 10 
Output: 55 (fibonacci(10) = 55) 

**Test Case 3:** 
Input: 0 
Output: 0 (fibonacci(0) = 0)

---
## 2. Palindrome Checker

You are building a text processing tool that needs to identify palindromes in user input. The function should be able to handle various types of input strings, including alphanumeric characters and punctuation.

**Solution :**
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    scanf("%[^\n]s", &str);
    int len = strlen(str);
    
    for(int i=0; i<=len/2; i++){
        if(str[i]!=str[len-i-1]){
            printf("false");
            return 0;
        }
    }
    
    printf("true");

    return 0;
}
```

**Test Case 1:** 
Input: "radar" 
Output: True 

**Test Case 2:** 
Input: "hello" 
Output: False 

**Test Case 3:** 
Input: "Was it a car or a cat I saw?" 
Output: True

---
## 3. Prime Number Checker

In a cryptography application, you need to verify if a given number is prime to ensure security of generated keys. The function should be accurate and efficient for large numbers.

**Solution :**
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    int h = n/2;
    
    if(n<2) {
        printf("False");
    }
    
    for(int i=2; i<=h; i++){
        if(n%i==0) {
            printf("False");
            return 0;
        }
    }
    
    printf("True");

    return 0;
}
```

**Test Case 1:** 
Input: 17 
Output: True 

**Test Case 2:** 
Input: 15 
Output: False 

**Test Case 3:** 
Input: 1001 
Output: False

---
## 4.


```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char str[100];
    scanf("%[^\n]s", &str);
    int len = strlen(str);
    int j=len-1;
    
    for(int i=0; i<len && j>=0; i++, j--){
        
        if(!isalpha(str[i]) ){
            i++;
        }
        if(!isalpha(str[j]) ){
            j--;
        }
        if(tolower(str[i])!=tolower(str[j])){
            printf("false");
            return 0;
        }
    }
    
    printf("true");

    return 0;
}
```