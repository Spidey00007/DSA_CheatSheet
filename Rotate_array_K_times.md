# ❤️‍🔥 Rotate array K Times

The `std::reverse` function operates on a half-open range `[start, end)`.

- ✅ Includes the element at `start`
- ❌ Excludes the element at `end`

---


## 🔁 Rotations using std::rotate

### ⬅️ LEFT rotation (k steps)

```cpp
rotate(nums.begin(), nums.begin() + k, nums.end());
```


### ➡️ RIGHT rotation (k steps)

```cpp
rotate(nums.rbegin(), nums.rbegin() + k, nums.rend());
```

---

## ♨️ Rotate array k times LEFT (using reverse)

```cpp
// Reverse the first k elements (0 to k-1)
reverse(nums.begin(), nums.begin() + k);

// Reverse the remaining elements (k to n-1)
reverse(nums.begin() + k, nums.end());

// Reverse the entire array (0 to n-1)
reverse(nums.begin(), nums.end());
```



## 🚀 Rotate array k times RIGHT (using reverse)

```cpp
// Reverse the first part (0 to n-k-1)
reverse(nums.begin(), nums.begin() + (n - k));

// Reverse the second part (n-k to n-1)
reverse(nums.begin() + (n - k), nums.end());

// Reverse the entire array
reverse(nums.begin(), nums.end());
```
