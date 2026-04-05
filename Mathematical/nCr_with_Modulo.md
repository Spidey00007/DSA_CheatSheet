# 📌 nCr with Modulo

## 🔹 Formula

nCr = n! / (r!(n-r)!)

### 👉 Under Modulo:

nCr = fact[n] _ invFact[r] _ invFact[n-r] % MOD

### 📖 Fermat’s Little Theorem:

If MOD is prime:

a⁻¹ = a^(MOD-2) % MOD

## 🔹 Precomputation Strategy ⚡

We precompute:

- fact[i] = i! % MOD
- invFact[i] = (i!)⁻¹ % MOD

## 🔹 invFact Logic 🔥

i! = (i+1)! / (i+1)

⇒ (i!)⁻¹ = ((i+1)!)⁻¹ \* (i+1)

### ✅ Final Relation:

invFact[i] = invFact[i+1] \* (i+1) % MOD;

---

# 🚀 Full C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

const int MOD = 1e9 + 7;
const int N = 1e6 + 5;

long long fact[N], invFact[N];

long long power(long long a, long long b) {
    long long res = 1;
    while (b) {
        if (b & 1) res = (res * a) % MOD;
        a = (a * a) % MOD;
        b >>= 1;
    }
    return res;
}

void precompute() {
    // factorial
    fact[0] = 1;
    for (int i = 1; i < N; i++)
        fact[i] = fact[i - 1] * i % MOD;

    // inverse factorial
    invFact[N - 1] = power(fact[N - 1], MOD - 2);
    for (int i = N - 2; i >= 0; i--)
        invFact[i] = invFact[i + 1] * (i + 1) % MOD;
}

long long nCr(int n, int r) {
    if (r > n || r < 0) return 0;
    return fact[n] * invFact[r] % MOD * invFact[n - r] % MOD;
}

int main() {
    precompute();

    int n = 5, r = 2;
    cout << nCr(n, r) << endl; // Output: 10

    return 0;
}
```

---

## ⚡ Complexity

- Precomputation: O(N)
- Each nCr Query: O(1)

---

## 💡 Pro Tips

- Use when multiple queries of nCr
- Works efficiently up to ~1e6
- Ensure MOD is prime (e.g. 1e9+7)
