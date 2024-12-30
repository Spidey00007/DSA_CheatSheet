# 🚀 Bit Manipulation Algorithms Cheat Sheet
---

## 🧮 1. Count Set Bits (Hamming Weight)
- Count the number of `1`s in the binary representation of a number.
```
int countSetBits(int n) {
    int count = 0;
    while (n) {
        count += (n & 1);
        n >>= 1;
    }
    return count;
}
```

## 🔄 2. Check if a Number is a Power of Two
- Determine if a number is a power of two.
```
bool isPowerOfTwo(int n) {
    return (n > 0) && ((n & (n - 1)) == 0);
}
```

## ↔️ 3. Toggle a Bit
- Toggle the `k`-th bit of a number.
```
int toggleBit(int n, int k) {
    return n ^ (1 << k);
}
```

## 📋 4. Set a Bit
- Set the `k`-th bit of a number to `1`.
```
int setBit(int n, int k) {
    return n | (1 << k);
}
```

## ❌ 5. Clear a Bit
- Clear the `k`-th bit of a number.
```
int clearBit(int n, int k) {
    return n & ~(1 << k);
}
```

## 🧐 6. Check if a Bit is Set
- Check if the `k`-th bit of a number is set.
```
bool isBitSet(int n, int k) {
    return (n & (1 << k)) != 0;
}
```

## 🔄 7. Swap Two Numbers Without Temp Variable
- Swap two numbers using bitwise operations.
```
void swapNumbers(int &a, int &b) {
    a ^= b;
    b ^= a;
    a ^= b;
}
```

## 🛠 8. Find the Only Non-Repeating Element
- Find the unique element in an array where every other element repeats.
```
int findUnique(int arr[], int n) {
    int result = 0;
    for (int i = 0; i < n; ++i) {
        result ^= arr[i];
    }
    return result;
}
```

## 🚩 9. Get the Lowest Set Bit
- Get the position of the lowest set bit in a number.
```
int getLowestSetBit(int n) {
    return n & -n;
}
```

## 📈 10. Count Different Bits in Two Numbers
- Count the number of differing bits between two numbers.
```
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
```
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
```
int findMissingNumber(int arr[], int n) {
    int x1 = 0, x2 = 0;
    for (int i = 0; i < n - 1; ++i) x1 ^= arr[i];
    for (int i = 1; i <= n; ++i) x2 ^= i;
    return x1 ^ x2;
}
```