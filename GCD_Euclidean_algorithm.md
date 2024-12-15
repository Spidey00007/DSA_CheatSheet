### 🧬 Use inbuilt function of LCM and GCD:
```cpp
int result = gcd(a, b);
int result = lcm(a, b);
```

### 🎗️ Euclidean algorithm code
```cpp
int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}
```
Time Complexity : O(log(min(a, b)))