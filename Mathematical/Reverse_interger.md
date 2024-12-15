### :fountain: Reverse interger

```
Int Range == [-2147483648, 2147483647]

Positive of INT_MIN is not in range of integer. So, (-1 * INT_MIN) is not an integer.

Reverse integer, also works for negative: eg: x=123, x=-123
```

###### :circus_tent: Question based on above concept (Leetcode 7):

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.
Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

```cpp
class Solution {
public:
    int reverse(int x) {
        int ans=0;
        while(x) {
            if(ans > INT_MAX/10 || ans < INT_MIN/10) return 0;
            ans=ans*10 + (x%10);
            x/=10;
        }
        return ans;
    }
};
```