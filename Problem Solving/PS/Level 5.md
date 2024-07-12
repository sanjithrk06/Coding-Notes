
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
## 4. Anagram Detector

You are developing a word game where players need to identify anagrams of given words. Your function should be capable of quickly determining if two words are anagrams, regardless of letter case or spaces.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char str[100];
    char r1[100];
    char str1[100];
    char r2[100];
    scanf("%[^\n]%*c", &str);
    scanf("%[^\n]%*c", &str1);
    int len = strlen(str);
    int len1 = strlen(str1);
    
    int k=0;
    for(int i=0; i<len; i++){
        for(int j=i+1; j<len; j++){
            if(tolower(str[i])> tolower(str[j])){
                char temp = str[i];
                str[i] = str[j];
                str[j] = temp;
            }
        }
        if(isalpha(str[i])){
            r1[k++] = str[i];
        }
    }
    
    int l=0;
    for(int i=0; i<len1; i++){
        for(int j=i+1; j<len; j++){
            if(tolower(str1[i])> tolower(str1[j])){
                char temp = str1[i];
                str1[i] = str1[j];
                str1[j] = temp;
            }
        }
        r2[l] = str1[i];
    }
    
    for(int i=0, j=0; i<k && j<l; i++, j++){
        if(tolower(r1[i]) != tolower(r2[j])) {
            printf("False");
            return 0;
        }
    }
    
    printf("true");

    return 0;
}
```

---
## 5. Recursive Factorial Calculator

In a scientific computing project, you need to calculate factorial values for various mathematical computations. The function should handle both small and large integers efficiently.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int fact(int n){
    if(n==1) return 1;
    return n*fact(n-1);
}

int main() {
    int n;
    scanf("%d", &n);
    
    printf("Factorial : %d", fact(n));
    
    return 0;
}
```
---
## 6. Power Function

You are developing a scientific calculator application that requires computing powers of numbers. The function should accurately handle both positive and negative exponents.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <math.h>

int main() {
    int n;
    int n1;
    scanf("%d", &n);
    scanf("%d", &n1);
    
    printf("Power : %d", (int)pow(n, n1));
    
    return 0;
}
```
---
## 7. String Compression

Your data compression algorithm needs a function to compress repetitive sequences of characters in textual data. The function should reduce storage requirements without loss of information.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <math.h>

int main() {
    char str[100];
    scanf("%[^\n]s", &str);
    
    int len = strlen(str);
    int count = 1;
    
    for(int i=0; i<len; i++){
        if(i==len-1 || str[i] != str[i+1]){
            if(count==1) printf("%c", str[i]);
            else printf("%c%d", str[i], count);
            
            count=1;
            continue;
        }
        count++;
    }
    
    return 0;
}
```

---
## 8. Matrix Transposition

In a matrix manipulation tool for image processing, you need a function to transpose matrices to apply specific transformations efficiently.

```c

```

---
## 12. String Reversal

You are developing a text manipulation tool where users can reverse the order of characters in a string

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <math.h>

int main() {
    char str[100];
    scanf("%[^\n]s", &str);
    
    int len = strlen(str);
    
    for(int i=len-1; i>=0; i--){
        printf("%c", str[i]);
    }
    
    return 0;
}
```

---


## 

---
## 23. Armstrong or perfect numbers 

In various scientific and engineering domains, dealing with large datasets or numerical simulations, it may be necessary to validate the integrity of the data by checking for special number properties, such as Armstrong numbers or Perfect numbers. Develop a program to find the given number is an armstrong or perfect number

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <ctype.h>

int len(int a){
    int l=0;
    
    while(a>0){
        l++;
        a /= 10;
    }
    
    return l;
}

int ams(int a){
    int l=len(a), res = 0;
    int temp = a;
    
    while(a>0){
        int r = a%10;
        res += (int)pow(r, l);
        a /= 10;
    }
    
    if(res == temp){
        return 1;
    }
    
    return 0;
}

int main() {
    int a;
    scanf("%d", &a);
    
    if(ams(a)){
        printf("True");
    }else{
        printf("false");
    }

    return 0;
}
```

---
## 24. Simple Calculator using Function 

Develop a program for a simple calculator that performs basic arithmetic operations (addition, subtraction, multiplication, division). To ensure modularity and reusability, you decide to implement each arithmetic operation as a separate function.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int perform(char op, int a, int b){
    switch(op){
        case '+':
            return a+b;
        case '-':
            return a-b;
        case '/':
            return a/b;
        case '*':
            return a*b;
    }
    
    return -1;
}

int main() {
    char op;
    scanf("%c", &op);
    
    int a, b;
    scanf("%d", &a);
    scanf("%d", &b);
    
    printf("%d", perform(op, a, b));

    return 0;
}
```

---
## 25. Counting the Even Numbers in a given list using Function 

Developing a C program that needs to count the number of even numbers in a list of integers. To achieve this, you decide to implement a function that takes the list and its size as parameters, iterates through the list, and counts how many numbers are even.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int evenCount(int arr[], int n){
    int count = 0;
    
    for(int i=0; i<n; i++){
        if(arr[i]%2==0) count++;
    }
    
    return count;
}

int main() {
    // char str[100];
    // scanf("%[^\n]s", &str);
    // int l = strlen(str);
    int n;
    scanf("%d", &n);
    int arr[n];
    for(int i=0; i<n; i++){
        scanf("%d", &arr[i]);
    }
    
    printf("Even Numbers Count : %d\n", evenCount(arr, n));

    return 0;
}
```

---
## 26. Counting the Odd Numbers in a given list using Function 

Implement a C program that needs to count the number of odd numbers in a list of integers. To achieve this, you decide to implement a function that takes the list and its size as parameters, iterates through the list, and counts how many numbers are odd.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int oddCount(int arr[], int n){
    int count = 0;
    
    for(int i=0; i<n; i++){
        if(arr[i]%2!=0) count++;
    }
    
    return count;
}

int main() {
    // char str[100];
    // scanf("%[^\n]s", &str);
    // int l = strlen(str);
    int n;
    scanf("%d", &n);
    int arr[n];
    for(int i=0; i<n; i++){
        scanf("%d", &arr[i]);
    }
    
    printf("Odd Numbers Count : %d\n", oddCount(arr, n));

    return 0;
}
```

---
## 27. Unique Character Identification in Text Messages 

You are developing a mobile messaging application that allows users to send and receive text messages. One of the features you want to implement is the ability to identify the first unique character in a message. Your task is to write a function that takes a string as input and returns the first non-repeating character in the string. If all characters in the string are repeating, the function should return a null character or a special value to indicate that no unique character was found.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

char nr(char* str, int l){
    int flag =0;
    for(int i=0; i<l; i++){
        flag=0;
        for(int j=0; j<l; j++){
            if(i!=j && tolower(str[i]) == tolower(str[j])){
                flag = 1;
                break;
            }
        }
        
        if(flag==0) return str[i];
    }
    
    return '0';
}

int main() {
    char str[100];
    scanf("%[^\n]s", &str);
    int l = strlen(str);
    
    printf("1st Non repeating : %c\n", nr(str, l));

    return 0;
}
```