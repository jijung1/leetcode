*Problem Description

We have two special characters. The first character can be represented by one bit 0. The second character can be represented by two bits (10 or 11).

Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.

Example 1:
Input: 
bits = [1, 0, 0]
Output: True
Explanation: 
The only way to decode it is two-bit character and one-bit character. So the last character is one-bit character.
Example 2:
Input: 
bits = [1, 1, 1, 0]
Output: False
Explanation: 
The only way to decode it is two-bit character and two-bit character. So the last character is NOT one-bit character.
Note:

1 <= len(bits) <= 1000.
bits[i] is always 0 or 1.

*Solution



```

/**
 * @param {number[]} bits
 * @return {boolean}
 

 
 */
var isOneBitCharacter = function(bits) {
    let q = 0;
    
    for (i = 0; i < bits.length; ++i) {
        if (q == 0) {
            if (bits[i] == 1)
                q = 1;
        }
        else if (q == 1) 
            q = 2;
        
        else if (q == 2) {
            if (bits[i] == 1) {
                q = 1;
            }
            else {
                q = 3;
            }
        }
        else if (q == 3) {
            if (bits[i] == 1) {
                q = 1;
            }
        }
            
    }
    if (q == 0 || q == 3) 
        return true;
    return false;
};

```
