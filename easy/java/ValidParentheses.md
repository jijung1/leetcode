*Problem Description

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

Example 1:

Input: "()"
Output: true
Example 2:

Input: "()[]{}"
Output: true
Example 3:

Input: "(]"
Output: false
Example 4:

Input: "([)]"
Output: false
Example 5:

Input: "{[]}"
Output: true

*Solution



```

import java.util.*;
import java.lang.*;
class Solution {
    public boolean isValid(String s) {
        Stack<java.lang.Character> openingBracket = new Stack<java.lang.Character>();
        for (int i = 0; i < s.length(); ++i) {
            char a = s.charAt(i);
            if (a == '(' || a == '{' || a == '[') {
                openingBracket.push(a);
            }
            else if (a == ')') {
                if (openingBracket.isEmpty())
                    return false;
                if (openingBracket.peek() == '(')
                    openingBracket.pop();
                else 
                    return false;
            }
            else if (a == ']') {
                    if (openingBracket.isEmpty())
                    return false;
                if (openingBracket.peek() == '[')
                    openingBracket.pop();
                else 
                    return false;
            }

            else if (a == '}') {
                    if (openingBracket.isEmpty())
                    return false;
                if (openingBracket.peek() == '{')
                    openingBracket.pop();
                else 
                    return false;
            }
        }
        if (openingBracket.isEmpty()) 
            return true;
        else
            return false;
    }
}



```
