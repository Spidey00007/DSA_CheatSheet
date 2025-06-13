# 🚀 Miscellaneous

## 🧮 Number Properties
```cpp
// Number of Bits in Binary
int bits = int(log2(num)) + 1;

// Number of Digits in Decimal
int digits = int(log10(num)) + 1;
```

## ✏️ Repeat Character in String  
```cpp
//It adds '?' n times in string

string str = string(5, '?');
```

## 🧪 Compare Containers  
- Use `==` to directly compare vector, set, or map.
- Can't be used in stack or queue.

## 🪄 Sorting String with Hyphen  
- Sorting the string "-4563782001" will rearrange its characters in ascending order based on ASCII characters.
- The `-` character has the lowest ASCII value among the characters. So, the digits will be in ascending order.
- Sorting `-4563782001` will result in: `-0123456789`

# 🚫 Not Allowed Without Custom Hash

Using `unordered_map` or `unordered_set` with certain types requires a custom hash function. The following are **not allowed by default**:

| ❌ Type              | ❌ Example                                 |
|---------------------|--------------------------------------------|
| **Pairs**           | `unordered_set<pair<int, int>>`           |
| **Tuples**          | `unordered_map<tuple<int, int, int>, int>`|
| **Custom Classes**  | `unordered_set<MyClass>`                  |

---

# ✅ Allowed in Ordered Containers

These types **are allowed** in `map` and `set` (ordered containers) because they use **comparators** (`operator<`) instead of hash functions.

| ✔️ Type              | ✔️ Example                                 |
|----------------------|--------------------------------------------|
| **Pairs**            | `map<pair<int, int>, int>`                |
| **Tuples**           | `set<tuple<int, int, int>>`               |
| **Custom Classes**   | `set<MyClass>` *(with operator< defined)* |


# 🧱 Data Structures & Access Support

## 1️⃣ Data Structures That Support Both `front()` and `back()`

| Data Structure       | `front()` | `back()` | Notes                                    |
|----------------------|----------|----------|------------------------------------------|
| `queue` (FIFO)       | ✅       | ✅       | Standard queue (first-in, first-out)     |
| `deque`              | ✅       | ✅       | Supports push/pop from both ends         |
| `vector`             | ✅       | ✅       | Efficient for accessing both ends        |
| `list` (Doubly Linked)| ✅       | ✅       | Efficient for insert/delete at both ends |

---

## 2️⃣ Data Structures That Support Only `front()`

| Data Structure     | `front()` | `back()` | Notes                                           |
|--------------------|-----------|----------|-------------------------------------------------|
| `stack` (LIFO)     | ❌        | ✅       | Only top element is accessible (`stack.top()`)  |
| `priority_queue`   | ❌        | ✅       | Only highest-priority element accessible (`pq.top()`) |
