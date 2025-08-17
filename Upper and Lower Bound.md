# 📘 Notes on Bounds and Iterators in C++

------------------------------------------------------------------------

## 🔎 Bounds in a Sorted Vector

``` cpp
// lower_bound = first element >= x
auto low = lower_bound(arr.begin(), arr.end(), x);

// upper_bound = first element > x
auto up  = upper_bound(arr.begin(), arr.end(), x);

int smaller = low - arr.begin();   // all elements before first >= x
int equal   = up - low;            // elements equal to x
int greater = arr.end() - up;      // all elements after last > x
```

-   **`lower_bound`** → first element **≥ x**\
-   **`upper_bound`** → first element **\> x**\
-   **Smaller count** = elements before `lower_bound`\
-   **Equal count** = difference between `upper_bound` and
    `lower_bound`\
-   **Greater count** = elements after `upper_bound`

------------------------------------------------------------------------

## 🧭 Iterators in C++

### ▶️ `begin()`

-   Returns an iterator pointing to the **first element**.\
-   Example: `*arr.begin()` → first element.

### ⏭️ `end()`

-   Returns an iterator pointing **just after the last element**.\
-   ⚠️ Not valid to dereference.\
-   Example: used in loops →
    `for(it = arr.begin(); it != arr.end(); it++)`.

### ◀️ `rbegin()`

-   Returns a **reverse iterator** pointing to the **last element**.\
-   Example: `*arr.rbegin()` → last element.

### ⏮️ `rend()`

-   Returns a **reverse iterator** pointing **before the first element**
    (one before index `0`).\
-   Example: used in reverse loops →
    `for(it = arr.rbegin(); it != arr.rend(); it++)`.

------------------------------------------------------------------------

✅ Quick Visual (for `arr = {10, 20, 30}`):

    Index:   0     1     2
    Value:  10    20    30
             ^           ^
     begin()             rbegin()
     end() → after 30    rend() → before 10
