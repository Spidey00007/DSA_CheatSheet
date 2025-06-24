
# ⚠️ C++ STL: When You Cannot Use `&` Reference in Range-Based Loops

This guide explains where and why you **cannot** use `&` (non-const reference) when iterating over STL containers in C++.

---

## ❌ You CANNOT Use `&` Reference With:

### 1. `std::set`, `std::unordered_set`
- These containers store **unique keys**, which are **immutable** once inserted.
- Iterating with a non-const reference is **not allowed** because it could break internal structure (e.g., hash or order).

```cpp
std::unordered_set<int> s = {1, 2, 3};

for (int& val : s) {      // ❌ ERROR: keys are const internally
    val = val + 1;
}

for (const int& val : s) { // ✅ OK: read-only access
    std::cout << val << " ";
}
```

---

### 2. `std::map`, `std::unordered_map` (for the **key**)
- Map keys are **const** within the container.
- You cannot modify them using a non-const reference.

```cpp
std::unordered_map<int, std::string> m = {{1, "one"}, {2, "two"}};

for (auto& pair : m) {           // ✅ OK: pair is std::pair<const int, string>
    // pair.first++;            // ❌ ERROR: key is const
    pair.second = "updated";     // ✅ OK: value is mutable
}
```

---

## ✅ You CAN Use `&` Reference With:

### 1. `std::vector`, `std::deque`, `std::list`
- All elements are mutable and can be modified with a reference.

```cpp
std::vector<int> v = {1, 2, 3};

for (int& val : v) {  // ✅ OK: elements can be changed
    val *= 2;
}
```

---

## 🧠 General Rule

> If the container enforces uniqueness or ordering (`set`, `map`), then its **keys are immutable**. Avoid non-const references in those cases.

Use:
```cpp
for (const auto& x : container)  // ✅ Safe, read-only
```
unless you're modifying elements of a container like `vector`, `deque`, etc.

---

Happy Coding! 🚀
