# Counting Bits (Easy)

## Approach 1 

1. We are iterating till n;
for every i, we have to count set bits in its binary representation.
    0 --> 0
    1 --> 1
    2 --> 10
    3 --> 11
    4 --> 100
    5 --> 101
    
    Output : [0,1,1,2,1,2]
2. Iterating till i becomes zero and adding its remainder to sum on division by 2 and reducing i by 2;
3. Add sum to the ans vector.

Time Complexity : O(nlogn)

## Approach 2 [DP]

Let if we hace X and Y in such a wat that,
X/2 = Y

then #setbits(X) - #setbits(Y) <= 1


Example. Let X = 7 and Y = 3, then 7/2 = 3;

            7 -> 111 #setbits(7) = 3
            
            3 -> 011 #setbits(3) = 2
            
            difference = 3-2 <= 1;
            
Example. Let X = 12 and Y = 6, then 12/2 = 6;

            12 -> 1100 #setbits(12) = 2
            
             6 -> 0110 #setbits(6) = 2
             
            difference = 2-2 <= 1;
            
There can be two case : whether X is even or odd.
If X is odd:

    * then LSB(least significant bit) will always be _set_(1) and dividing by 2 means right shifting the number by 1 bit.
    
    * so if LSB is _set_ and right shift by 1 bit then the last set bit will be lost.
    
    * therefore the new number Y has 1 set bit less in comparison to X.
    
If X is even:

    * then LSB will be 0, therefore even if we do right shift by 1 bit, then only _unset_(0) bit will be lost.
    
So, 

    when X is even: #setbits(X) = #setbits(Y)

    when X is odd:  #setbits(X) = 1 + #setbits(Y)
    
Time Complexity : O(n)
