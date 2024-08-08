
## Bitwise Operators

- Types of bitwise operators,
	- AND Operator `&`,
	- OR Operator `|`,
	- XOR Operator `^`,
	- Complement `~`,
	- Left Shift Operator `<<`,
	- Right Shift Operator `>>`

### (i) AND Operators(&)
- Whenever you perform and operation with 1 and any number (i.e. `1 & any number`) , digits will remain the same.

**==`Questions`==**
**Q1.** Find a number is even or odd? 

### (ii) OR Operators (|)
- Whenever you perform or operation with 0 and any number (i.e. `1 & any number`) , digits will remain the same.

### (iii) XOR Operator (if and only if) (^)
- Only one should be true.
- If i xor any number with 1, the answer will be the compliment of that number. Many more,
	- $num(xor)1 = num'$, 
	- $num(xor)0 = num$ , 
	- $num(xor)num = 0$


### (iv) Left Shift Operator (<<)
$$10<<1 = (1010)_2 = (10100)_2 = 20$$
- If you left shift any number with 1, the result will be double the number $$a<<1 = 2a$$In General part is, $$a<<b = a*2^b$$

### (v) Right Shift Operator

- It will divide the number by 2.$$a>>b = a/2^b$$




# Number Systems

1. Decimal Number System (i.e. 0,1,2,3,4,....) & Base is 10,
2. Binary Number System (i.e. 000, 001, 010, 011, 100,....) & Base is 2,
3. Octal Number System (i.e. 0, 1, 2,...., 7) & Base is 8,
4. Hexa Decimal Number System (i.e. 0, 1, 2, 3, ....., 16) & Base is 16.

### Conversions

1. Decimal to Any Base
	Keep dividing the decimal number by base, take the remainders in the opposite direction. 

2. Any Base to Decimal
	Multiply and add the power of base with digit.$$(100101)_2 = (1*2^5) + (0*2^4) + (0*2^3) + (1*2^2) + (0*2^1) + (1*2^0) = (37)_10$$-Here base 10 represents the decimal number.



## Questions

### Q1. Find a number is even or odd?
#and 

- Last number in Binary representation of the number is 1 means odd or 0 means even.
**==`Note`==** $num (and) 1 = num (1 or 0)$
==**`Logic`**==
```Java
(num & 1 == 0) ? even : odd 
```
==`Code`==
```Java
public static void main(String[] args){  
    Scanner in = new Scanner(System.in);  
    int number = in.nextInt();  
  
    if((number & 1) == 0) System.out.printf("%d is an even number", number);  
    else System.out.printf("%d is a odd number", number);  
}
```

### Q2. Find the unique number in an array
#xor
- [[Bitwise Operators#(iii) XOR Operator (if and only if) ( ) | Refer XOR Operators]].
==`Note`== $num(xor)num = 0$
==`Logic`==
```Java
for(int num: arr){
	unique ^= num;
}
```
==`Code`==
```Java
private static int uniques(int[] arr) {  
    int unique = 0;  
  
    for(int num: arr){  
        unique ^= num;  
    }  
  
    return unique;  
}
```

### Q3. Find the $ith$ bit of a number
#and #leftShift
