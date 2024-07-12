
## Sum of all the digits untill less than 10

```c
#include <stdio.h>

int sum(int a){
    int rem, sum=0;
    while(a>0){
        rem = a%10;
        sum+=rem;
        a/=10;
    }
    
    return sum;
}

int main() {
    int a;
    scanf("%d", &a);
    
    while(a>9){
        a = sum(a);
    }
    
    printf("%d", a);
    
    return 0;
}
```

## Pattern

```c
#include <stdio.h>

int main() {
    int a;
    scanf("%d", &a);
    
    for(int i=0; i< a; i++){
        int n=1;
        for(int j =0; j<a-i; j++){
            printf("%d", n);
            n++;
        }
        printf("\n");
    }
    
    return 0;
}
```

## LCM & GCD

```c
#include <stdio.h>

int main() {
    int n1, n2, gcd, lcm;
    scanf("%d %d", &n1, &n2);
    
    int max = n1>n2 ? n1:n2;
    while(1){
        if((max%n1 ==0) && (max%n2 == 0)){
            lcm = max;
            break;
        }
        max++;
    }
    
    gcd = (n1*n2) / lcm;
    
    printf("GCD : %d --- LCM : %d", gcd, lcm);
    
    return 0;
}
```


## Fibonacci numbers

```c
#include <stdio.h>

int main() {
    int n, a1 = 0, a2 = 1, a3;
    scanf("%d", &n);
    
    if(n==1){
        printf("%d", a1);
    }else if(n>1){
        printf("%d %d ", a1, a2);
        for(int i=2; i<n; i++){
            a3 = a1+a2;
            printf("%d ", a3);
            a1=a2;
            a2=a3;
        }
    }
    
    return 0;
}
```

## Armstrong Number

```c
#include <stdio.h>
#include <string.h>
#include <math.h>

int count(int a){
    char ch[20];
    
    sprintf(ch, "%d", a);
    
    return strlen(ch);
}

int main() {
    int n, temp, rem, sum = 0;
    scanf("%d", &n);
    temp = n;
    int len = count(n);
    
    while(temp>0){
        rem = temp%10;
        sum += (int)pow(rem, len);
        temp/=10;
    }
    
    if(n==sum){
        printf("It is armstrong number");
    }else{
        printf("It is not a armstrong number");
    }
    
    return 0;
}
```


## Integer to Roman

```c
#include <stdio.h>
#include <string.h>
#include <math.h>

int itor(int a){
    int value[] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
    char *sym[] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
    char result[100];
    result[0] = '\0';
    for(int i = 0; i<13; i++){
        while(a>=value[i]){
            strcat(result, sym[i]);
            a-=value[i];
        }
    }
    printf("%s", result);
}

int main() {
    int n;
    scanf("%d", &n);
    
    itor(n);
    
    return 0;
}
```


## Roman to Integer

```c
#include <stdio.h>
#include <string.h>
#include <math.h>

void rtoi(char *ch){
    int values[26];
    values['I' - 'A'] = 1;
    values['V' - 'A'] = 5;
    values['X' - 'A'] = 10;
    values['L' - 'A'] = 50;
    values['C' - 'A'] = 100;
    values['D' - 'A'] = 500;
    values['M' - 'A'] = 1000;
    int cur = 0, prev = 0, result = 0;
    for(int i = 0; i<strlen(ch); i++){
        cur = values[ch[i] - 'A'];
        if(cur>prev){
          result+=cur - 2*prev;  
        }else{
            result+= cur;
        }
        prev = cur;
    }
    
    printf("%d", result);
}

int main() {
    char ch[10];
    scanf("%[^\n]s", &ch);
    
    rtoi(ch);
    
    return 0;
}
```


## Swap 1st & last number

```c
#include <stdio.h>
#include <string.h>
#include <math.h>

int main() {
    int a;
    scanf("%d", &a);
    
    char ch[100];
    sprintf(ch, "%d", a);
    
    int len = strlen(ch);
    
    char temp = ch[len-1];
    ch[len-1] = ch[0];
    ch[0] = temp;
    
    printf("%s", ch);
    
    return 0;
}
```

## 