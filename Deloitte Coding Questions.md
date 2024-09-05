# Deloitte Coding Questions 

#### Question 1
Determine whether a given integer num can be converted into a palindrome by removing one digit. An integer is a palindrome if it reads the same backward and forward.

Read the input from STDIN and write the output to STDOUT. You should not write arbitary strings while reading the input and while printing as these contribute to the standard output

**Input Format:**
The first line of input has N, the number of integers given.
The next N lines contain an integer num.

**Output Format:**
The N lines of output contain "YES" if the input integer is a palindrome, and "No" if not a palindrome.

**Constraints:**
1 <= N <= 2000
-2^31 < num < 2^31

**Sample Input1:**
2
31
-123

**Sample Output1:**
YES 
NO

**Expaination1:**
In given two integers, the first integer is 31, By removing either 1 or 3, we are left with 3 or 1, which read the same backward, so "YES" is printed in the first line.
The second integer is -123 which cannot read the same backwards irrespectiveof which number is removed. Hence "NO" is printed in the second line.

**Sample Input2:**
2
12321
2202

**Sample Output2:**
YES 
YES

**Expaination2:**
Removing 3 from the first integer gives 1221, which is a palindrome.
Removing 0 from the second integer gives 222, which is a palindrome.

#### Solution: 
Filename: palindrome.py 
```python
def can_be_converted_to_palindrome(n):
    num_str = str(abs(n))
    
    # Check if the given string is a palindrome
    def is_palindrome(s):
        return s == s[::-1]
    
    # Check all possible strings by removing one digit
    for i in range(len(num_str)):
        new_str = num_str[:i] + num_str[i+1:]
        if is_palindrome(new_str):
            return True
    
    return False

def main():
    k = int(input())
    
    for _ in range(k):
        n = int(input())
        if can_be_converted_to_palindrome(n):
            print("YES")
        else:
            print("NO")

main()

```


#### Question 2
Given a positive integer interval l and an integer destination point D, your task is to find the number of integer-valued jumps required to reach the destination point D from the starting position O on number line considering both positive and negative destinations.

Write a program to determine the total number of jumps required to reach the destination point D.

Read the Input from STDIN(Standard Input) and print it to STDOUT(Standard Output) with a trailing newline. You should not write arbitary strings while reading the input and while printing as these contribute to the standard output.

**Constraints:**
1 <= l <= 500
-10000 <= D <= 10000

**Input Format:**
The first line of input consists of two integers I and D, the positive interval and destination.

**Output Format:**
The output should print the total number of jumps required to each the destination.
If no paths are found, display the message "There is no path available".

**Sample Input:**
2 10

**Sample Output:**
5

**Explaination:**
Given, that the interval I is 2.
Destination D is 10

| Leap Interval | Leap Destination | No. of Jumps required to reach the destination |
|:-------------:|:----------------:|:----------------------------------------------:|
| 2 | 0 -> 2 -> 4 -> 6 -> 8 -> 10 | 5 |


As given in the above table, there are 5 jumps to reach the destination 10.

#### Solution:
Filename: jump-calculator.py
```python
def main():
    # Read the interval and destination from input
    l, D = map(int, input().split())
    
    # Check if the destination is reachable
    if D % l == 0:
        # Calculate the number of jumps
        jumps = abs(D) // l
        print(jumps)
    else:
        print("There is no path available")

main()

```

