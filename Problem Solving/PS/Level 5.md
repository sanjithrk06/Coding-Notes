
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
## 9. Word Frequency Counter

You are developing a text analysis tool that requires counting the occurrences of each word in a given document. The function should handle different languages and punctuation marks appropriately.

```c

```
---
## 10. Sorting Algorithm Implementation

In a data analytics application, you need to sort large datasets to perform efficient analysis. Your function should implement a robust sorting algorithm to handle various data types and sizes.

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <math.h>

void sort(int arr[], int l){
    for(int i=0; i<l; i++){
        for(int j=i+1; j<l; j++){
            if(arr[i]>arr[j]){
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }   
    }
}

int main(){
    int n;
    scanf("%d", &n);
    
    int arr[n];
    for(int i=0; i<n; i++){
        scanf("%d", &arr[i]);
    }
    
    sort(arr, n);
    
    for(int i=0; i<n; i++){
        printf("%d ", arr[i]);
    }
    
    return 0;
}
```
---

## 11. Matrix Multiplication



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
## 13. Calculating Building Dimensions

You are an architect working on the design of a new office building. As part of your design process, you need to calculate the dimensions of various structural elements, such as the size of the foundation, the height of the floors, and the thickness of the walls. One of the key calculations you need to perform is finding the square root of the total floor area of the building. This will help you determine the appropriate size and layout of the foundation. Write a program that includes a function “findSquareRoot()” that takes a float value representing the total floor area and returns the square root of that value as a float. Use this function in your program to calculate the square root of the floor area and display the result. Assume that the user will input the total floor area of the building when prompted.

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <math.h>

double sqroot(float num){
    if(num<0){
        printf("It's Negative num");
        return -1.0;
    }
    
    double res = sqrt(num);
    
    return res;
}

int main(){
    float num;
    scanf("%f", &num);
    
    double res = sqroot(num);
    
    if(res != -1.0){
        printf("result : %.2lf", res);
    }
    
    return 0;
}
```

---
## 14. Analyzing Text Documents

You are working on a project that involves analyzing text documents to extract various statistics, such as the number of words, the number of unique words, and the length of the longest word. As a first step, you need to write a program that can determine the length of a given string. Your program should include a function called “findStringLength()” that takes a string as input and returns the length of the string as an integer. You will then use this function in your main program to prompt the user to enter a string, call the findStringLength() function, and display the length of the string. This functionality will be a crucial component of your larger text analysis project, as it will allow you to quickly and accurately determine the length of words, sentences, and entire documents.

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <math.h>

int main(){
    char str[100];
    scanf("%[^\n]s", str);
    
    int len = strlen(str);
    
    printf("String Length : %d", len);
    
    return 0;
}
```
---
## 15. Calculating Sums for Budgeting

You are working on a budgeting application that helps users keep track of their expenses. One of the features you want to implement is the ability to calculate the sum of all even or odd expenses within a given range. Your program should include a recursive function called “sumEvenOdd()” that takes the starting number, ending number, and a flag to indicate whether to sum even or odd numbers. The function should return the sum of all even or odd numbers in the given range. In the main program, you will prompt the user to enter the starting and ending numbers of the range, as well as a choice to sum either even or odd numbers. You will then call the “sumEvenOdd()” function with the user-provided inputs and display the result. This functionality will be useful for users who want to analyze their spending patterns and identify areas where they can cut back on expenses.

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <math.h>

void even(int n1, int n2){
    int sum = 0;
    for(int i=n1; i<=n2; i++){
        if(i%2==0){
            sum +=i;
        }
    }
    printf("Even Sum : %d", sum);
}

void odd(int n1, int n2){
    int sum = 0;
    for(int i=n1; i<=n2; i++){
        if(i%2!=0){
            sum +=i;
        }
    }
    printf("Odd Sum : %d", sum);
}

int main(){
    int n1, n2, c;
    scanf("%d %d %d", &n1, &n2, &c);
    
    switch(c){
        case 0:
            odd(n1, n2);
            break;
        case 1:
            even(n1, n2);
            break;
    }
    
    return 0;
}
```

---
## 16. GCD (Greatest Common Divisor) Calculator

You are developing a utility for a mathematics app that needs to compute the greatest common divisor of two numbers provided by users to help them simplify fractions. Create a function to compute the greatest common divisor of two numbers using recursion.

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <math.h>

int gcd(int n1, int n2){
    int gcd = 1;
    for(int i=1; i<n1 && i<n2; i++){
        if(n1%i==0 && n2%i==0){
            gcd = i;
        }
    }
    
    return gcd;
}

int main(){
    int n1, n2;
    scanf("%d %d", &n1, &n2);
    
    printf("GCD : %d", gcd(n1, n2));
    
    return 0;
}
```

---
## 17. Binary to Decimal Conversion

You are developing a digital logic simulation tool for an electronics engineering course. As part of this tool, you need to implement a feature that allows students to convert binary numbers (represented as strings) to their decimal equivalents. This will help students understand and verify their work on binary arithmetic and digital circuit design. Create a function to convert a binary number (given as a string) to its decimal equivalent.

```c
// Online C compiler to run C program online
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <math.h>

int btod(char str[], int l){
    int res=0;
    
    for(int i=0; i<l; i++){
        int val = str[l-1-i] - '0';
        int power = pow(2, i);
        res += val*power;
    }
    
    return res;
}

int main(){
    char str[100];
    scanf("%[^\n]s", &str);
    int l = strlen(str);
    
    int bin = btod(str, l);
    
    printf("%d", bin);
    
    return 0;
}
```

---
## 18. Convert Lowercase into Uppercase using Function

Develop a C program that processes user input and needs to convert any lowercase letters entered into uppercase for consistency and further processing. You decide to implement a function specifically for this conversion task to maintain clarity and reusability.

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>

char* convert(char str[], int l){
    for(int i=0; i<l; i++){
        str[i] = toupper(str[i]);
    }
    
    return str;
}

int main() {
    char str[100];
    scanf("%[^\n]%*c", &str);
    int l = strlen(str);
    
    char* res = convert(str, l);
    
    printf("%s", res);

    return 0;
}
```

---
## 19. Leap Year Check using Function

Developing a program that needs to determine if a given year is a leap year. To achieve this, you decide to implement a function that performs the leap year check based on the following criteria: A year is a leap year if it is divisible by 4. However, if the year is divisible by 100, it is not a leap year unless it is also divisible by 400.

```c
#include <stdio.h>
#include <string.h>

int leap(int n){
    if((n % 4 == 0 && n % 100 != 0) || n % 400 == 0){
        return 1;
    }else return 0;
}

int main() {
    int n;
    scanf("%d", &n);
    
    if(leap(n)){
        printf("Leap Year");
    }else printf("Non Leap Year");
    
    return 0;
}
```

---
## 20. Remove Duplicates in a given array using Function

Develop a program that processes an array of integers and needs to remove any duplicate elements. To achieve this, you decide to implement a function that: Takes an array of integers as input. Removes duplicates from the array while maintaining the order of remaining elements. Returns the new size of the array after removing duplicates.

```c
// Online C compiler to run C program online
#include <stdio.h>
#include <string.h>

int sort(int arr[], int n){
    for(int i=0; i<n; i++){
        for(int j=i+1; j<n; j++){
            if(arr[i]>arr[j]){
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
    
    return *arr;
}

int removeDup(int res[], int arr[], int n){
    sort(arr, n);
    int rn=0;
    
    for(int i=0; i<n; i++){
        if(i!=0 && arr[i] == arr[i-1]){
            continue;
        }
        res[rn++] = arr[i];
    }
    
    return rn;
}

int main() {
    int n;
    scanf("%d", &n);
    int arr[n];
    for(int i=0; i<n; i++){
        scanf("%d", &arr[i]);
    }
    
    int res[n];
    int rn = removeDup(res,arr, n);
    
    for(int i=0; i<rn; i++){
        printf("%d ", res[i]);
    }
    
    return 0;
}
```


```c
#include <stdio.h>
#include <stdlib.h>

// Function to sort the array
void sort(int arr[], int n){
    for(int i = 0; i < n - 1; i++){
        for(int j = i + 1; j < n; j++){
            if(arr[i] > arr[j]){
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
}

// Function to remove duplicates and return the new array and its size
int* removeDup(int arr[], int n, int *new_size){
    sort(arr, n);
    int *res = (int *)malloc(n * sizeof(int));
    int rn = 0;
    
    for(int i = 0; i < n; i++){
        if(i == 0 || arr[i] != arr[i - 1]){
            res[rn++] = arr[i];
        }
    }
    
    *new_size = rn;
    return res;
}

int main() {
    int n;
    scanf("%d", &n);
    int arr[n];
    for(int i = 0; i < n; i++){
        scanf("%d", &arr[i]);
    }
    
    int new_size;
    int *res = removeDup(arr, n, &new_size);
    
    for(int i = 0; i < new_size; i++){
        printf("%d ", res[i]);
    }
    printf("\n");
    
    free(res); // Free the allocated memory
    
    return 0;
}

```

---
## 21. Reverse the sentence

Implement functions in reversing sentences, which can be a technique used to achieve a particular style or effect, such as emphasizing the importance of certain words or creating a sense of disorientation.

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    scanf("%[^\n]%*c", &str);
    int l = strlen(str);
    
    for(int i=0; i<=l/2; i++){
        char temp = str[i];
        str[i] = str[l-i-1];
        str[l-i-1] = temp;
    }
    
    printf("%s", str);

    return 0;
}
```
---
## 22. Sum of primes

Some mathematical competitions and problem-solving challenges involve finding whether a given number can be expressed as the sum of two prime numbers. A number theory calculator with this feature can help participants quickly solve such problems and explore related concepts. Write a program to find whether the given number can be expressed as the sum of two prime numbers.

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <math.h>

int isPrime(int a){
    int sq = sqrt(a);
    
    if(a<2) return 0;
    
    for(int i=2; i<=sq; i++){
        if(a%i==0){
            return 0;
        }
    }
    
    return 1;
}


int sop(int n){
    int a, b;
    if(n<2) {
        return 0;
    }
    
    for(int i=2; i<n; i++){
        if(isPrime(i)){
            int k = n-i;
            if(isPrime(k)){
                return 1;
            }
        }
    }
    
    return 0;
}

int main(){
    int n;
    scanf("%d", &n);
    
    if(sop(n)){
        printf("True");   
    }else {
        printf("False");
    }
    
    return 0;
}
```

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