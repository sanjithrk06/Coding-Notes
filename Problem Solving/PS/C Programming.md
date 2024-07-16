

## String Splitting

```c
// Online C compiler to run C program online
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    scanf("%[^\n]%*c", str);
    
    char delim[] = " ";
    char* tok = strtok(str, delim);
    int maxLen = -1000;
    int minLen = 1000;
    char* max = tok;
    char* min = tok;
    
    while(tok!=NULL){
        int len = strlen(tok);
        if(maxLen < len) {
            maxLen = len;
            max = tok;
        }
        if(minLen > len) {
            minLen = len;
            min = tok;
        }
        printf("%s %d\nMin : %s\nMax : %s\n\n", tok, len, min, max);
        tok = strtok(NULL, delim);
    }
    
    return 0;
}
```


## First & last word

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    scanf("%[^\n]%*c", str);
    
    char delim[] = " ";
    char* tok = strtok(str, delim);
    char* first = tok;
    char* last = tok;
    
    while(tok!=NULL){
        last = tok;
        printf("%s\nfirst : %s\nlast : %s\n\n", tok, first, last);
        tok = strtok(NULL, delim);
    }
    
    printf("First Word : %s\nLast Word : %s", first, last);
    
    return 0;
}
```

---
## Matrix Transpose

```c
#include <stdio.h>
#include <string.h>

int main() {
    int arr[10][10], trans[10][10], r, c;
    printf("Enter row and col : ");
    scanf("%d %d", &r, &c);
    
    for(int i=0; i<r; i++){
        for(int j=0; j<c; j++){
            scanf("%d", &arr[i][j]);
        }
    }

    for(int i=0; i<r; i++){
        for(int j=0; j<c; j++){
            trans[j][i] = arr[i][j];
        }
    }

    for(int i=0; i<r; i++){
        for(int j=0; j<c; j++){
            printf("%d ", trans[i][j]);
            if(j == c-1) printf("\n");
        }
    }
    
    return 0;
}
```

---
## Matrix Multiplication

```c
#include <stdio.h>
#include <string.h>

// Function to multiply two matrices
void multiplyMatrices(int r1, int c1, int r2, int c2, int arr[r1][c1], int arr1[r2][c2], int result[r1][c2]) {
    for(int i = 0; i < r1; i++) {
        for(int j = 0; j < c2; j++) {
            result[i][j] = 0;
            for(int k = 0; k < c1; k++) {
                result[i][j] += arr[i][k] * arr1[k][j];
            }
        }
    }
}

int main() {
    int r1, c1, r2, c2;
    int arr[10][10], arr1[10][10], result[10][10];

    // Input dimensions of the matrices
    printf("Enter rows and columns for the first matrix: ");
    scanf("%d %d", &r1, &c1);
    printf("Enter rows and columns for the second matrix: ");
    scanf("%d %d", &r2, &c2);
    
    // Check if multiplication is possible
    if(c1 != r2) {
        printf("Invalid dimensions for matrix multiplication\n");
        return 1;
    }
    
    // Input elements of the first matrix
    printf("Enter elements of the first matrix:\n");
    for(int i = 0; i < r1; i++) {
        for(int j = 0; j < c1; j++) {
            scanf("%d", &arr[i][j]);
        }
    }
    
    // Input elements of the second matrix
    printf("Enter elements of the second matrix:\n");
    for(int i = 0; i < r2; i++) {
        for(int j = 0; j < c2; j++) {
            scanf("%d", &arr1[i][j]);
        }
    }
    
    // Call function to multiply the matrices
    multiplyMatrices(r1, c1, r2, c2, arr, arr1, result);
    
    // Output the result of the multiplication
    printf("Resultant matrix:\n");
    for(int i = 0; i < r1; i++) {
        for(int j = 0; j < c2; j++) {
            printf("%d ", result[i][j]);
        }
        printf("\n");
    }

    return 0;
} 
```

---
## Int to Roman

```c
// Online C compiler to run C program online
#include <stdio.h>
#include <string.h>

int main() {
    int n;
    scanf("%d", &n);
    
    int arr[] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
    char str[][3] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
    
    for(int i=0; i<13; i++){
        int di = n/arr[i];
        n = n%arr[i];
        while(di--){
            printf("%s", str[i]);
        }
    }

    return 0;
}
```

---
## Roman to int

```c
// Online C compiler to run C program online
#include <stdio.h>
#include <string.h>

int value(char s){
    switch(s){
        case 'I':
            return 1;
        case 'V':
            return 5;
        case 'X':
            return 10;
        case 'L':
            return 50;
        case 'C':
            return 100;
        case 'D':
            return 500;
        case 'M':
            return 1000;
    }
    
    return 0;
}

int rtoi(char s[]){
    int res = 0;
    int l = strlen(s);
    
    for(int i=0; i<l; i++){
        int s1 = value(s[i]);
        
        if(i+1<l){
            int s2 = value(s[i+1]);
            
            if(s1 < s2){
                res += (s2-s1);
                i++;
            }else res +=s1;
        }else res += s1;
    }
    
    return res;
}

int main() {
    char rom[100];
    scanf("%[^\n]%*c", rom);
    
    printf("%d", rtoi(rom));

    return 0;
}
```

---
