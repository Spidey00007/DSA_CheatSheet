# 🚀 Bit Manipulation Algorithms Cheat Sheet
---

## 🧮 1. Count Set Bits (Hamming Weight)
- Count the number of `1`s in the binary representation of a number.
```cpp
int countSetBits(int n) {
    int count = 0;
    while (n) {
        count += (n & 1);
        n >>= 1;
    }
    return count;
}
```
Time Complexity : `O(no of bits)`

- Right Shift and Assign `n >>= 1`: This shifts the bits of n to the right by 1 position and then assigns the result back to n.
- `n >>= 1` is equivalent to `n = n >> 1` or `n = n / 2`

### Another method
```cpp
int countSetBits(int n) {
    int count=0;
    while(n) {
        n = n & (n-1);
        count++;
    }
    return count;
}
```
Time Complexity : `O(no of set bits)`

## 🔄 2. Check if a Number is a Power of Two
- Determine if a number is a power of two. 
```cpp
bool isPowerOfTwo(int n) {
    return (n > 0) && ((n & (n - 1)) == 0);
}
```
Time Complexity : `O(1)`

## ↔️ 3. Toggle a Bit
- Toggle the `k`-th bit of a number.
```cpp
int toggleBit(int n, int k) {
    return n ^ (1 << k);
}
```

## 📋 4. Set a Bit
- Set the `k`-th bit of a number to `1`.
```cpp
int setBit(int n, int k) {
    return n | (1 << k);
}
```

## ❌ 5. Clear a Bit
- Clear the `k`-th bit of a number.
```cpp
int clearBit(int n, int k) {
    return n & ~(1 << k);
}
```

## 🧐 6. Check if a Bit is Set
- Check if the `k`-th bit of a number is set.
```cpp
bool isBitSet(int n, int k) {
    return (n & (1 << k)) != 0;
}
```

## 🔄 7. Swap Two Numbers Without Temp Variable
- Swap two numbers using bitwise operations.
```cpp
void swapNumbers(int &a, int &b) {
    a ^= b;
    b ^= a;
    a ^= b;
}
```

## 🚩 8. Get the Lowest Set Bit
- Get the position of the lowest set bit in a number.
```cpp
int getLowestSetBit(int n) {
    return n & -n;
}
```

## 🛠 9. Unset last set bit(rightmost)
```cpp
int unsetLastBit(int n) {
    return n & (n-1);
}
```

## 📈 10. Count Different Bits in Two Numbers
- Count the number of differing bits between two numbers.
```cpp
int countDifferentBits(int a, int b) {
    int diff = a ^ b;
    int count = 0;
    while (diff) {
        count += (diff & 1);
        diff >>= 1;
    }
    return count;
}
```

## 🌟 11. Reverse Bits of a Number
- Reverse the bits of a 32-bit unsigned integer.
```cpp
unsigned int reverseBits(unsigned int n) {
    unsigned int result = 0;
    for (int i = 0; i < 32; ++i) {
        result = (result << 1) | (n & 1);
        n >>= 1;
    }
    return result;
}
```

## 🔢 12. Find Missing Number in Array (XOR Method)
- Find the missing number in an array of size `n-1` containing numbers from `1` to `n`.
```cpp
int findMissingNumber(int arr[], int n) {
    int x1 = 0, x2 = 0;
    for (int i = 0; i < n - 1; ++i) x1 ^= arr[i];
    for (int i = 1; i <= n; ++i) x2 ^= i;
    return x1 ^ x2;
}
```

## 🍇 13. XOR of numbers from 1 to n
 ```cpp
 int findXor(int n) {
    if(n%4 == 0) return n;
    if(n%4 == 1) return 1;
    if(n%4 == 2) return n+1;
    if(n%4 == 3) return 0;
 }
 ```
 - PROBLEM : Find XOR from L to R
 ```cpp
 int findXor(int n) {
    if(n%4 == 0) return n;
    if(n%4 == 1) return 1;
    if(n%4 == 2) return n+1;
    if(n%4 == 3) return 0;
 }
 int findXorLtoR(int L, int R) {
    return findXor(L-1) ^ findXor(R);
 }
```

## 🎨 14. Unset all bits except rightmost set bit
- **`-temp` is the two's complement of `temp`**

🔍 **Performing `temp & (-temp)`:**
This operation clears all bits in `temp` except for the **rightmost set bit**.

For example:
- `temp = 12` (binary: `1100`)
- `-temp = -12` (binary: `0100`)

Now, perform the bitwise AND:
- `temp & (-temp) = 1100 & 0100 = 0100`

🧠 As you can see, only the **rightmost 1-bit** in `temp` remains (which in this case is `4`). 🎯

```cpp
int rightmostSetBit(int n) {
    n & (-n);
}
```