# 📘 Notes on Bounds and Iterators in C++

------------------------------------------------------------------------

## 🔎 Bounds in a Sorted Vector

``` cpp
// lower_bound = first element >= x
auto low = lower_bound(arr.begin(), arr.end(), x);

// upper_bound = first element > x
auto up  = upper_bound(arr.begin(), arr.end(), x);

int smaller = low - arr.begin();   // Number of elements >= x
int equal   = up - low;            // Number of elements = x
int greater = arr.end() - up;      // Number of elements > x
```

-   **`lower_bound`** → first element **≥ x**
-   **`upper_bound`** → first element **\> x**

------------------------------------------------------------------------

## 🧭 Iterators in C++

### ▶️ `begin()`

-   Returns an iterator pointing to the **first element**.
-   Example: `*arr.begin()` → first element.

### ⏭️ `end()`

-   Returns an iterator pointing **just after the last element**.
-   ⚠️ Not valid to dereference.
-   Example: used in loops →
    `for(it = arr.begin(); it != arr.end(); it++)`.

### ◀️ `rbegin()`

-   Returns a **reverse iterator** pointing to the **last element**.
-   Example: `*arr.rbegin()` → last element.

### ⏮️ `rend()`

-   Returns a **reverse iterator** pointing **before the first element**
    (one before index `0`).
-   Example: used in reverse loops →
    `for(it = arr.rbegin(); it != arr.rend(); it++)`.

------------------------------------------------------------------------

✅ Quick Visual (for `arr = {10, 20, 30}`):

    Index:   0     1     2
    Value:  10    20    30
             ^           ^
     begin()             rbegin()
     end() → after 30    rend() → before 10

# 🗂️ Notes on Bounds with `std::set` and `std::map`

------------------------------------------------------------------------

## 🔑 `std::set` Example

``` cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<int> s = {1, 3, 5, 7, 9};
    int x = 5;

    // lower_bound = first element >= x
    auto low = s.lower_bound(x);

    // upper_bound = first element > x
    auto up  = s.upper_bound(x);

    int smaller = distance(s.begin(), low);  // elements < x
    int equal   = distance(low, up);         // elements == x (0 or 1 in set)
    int greater = distance(up, s.end());     // elements > x

    cout << "Count smaller than " << x << ": " << smaller << endl;
    cout << "Count equal to "   << x << ": " << equal   << endl;
    cout << "Count greater than " << x << ": " << greater << endl;

    return 0;
}
```

✅ Works like vector, but with `distance()` since iterators in `set` are
not random-access.

------------------------------------------------------------------------

## 📌 `std::map` Example

``` cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<int, string> mp = {{1, "A"}, {3, "B"}, {5, "C"}, {7, "D"}};
    int x = 5;

    // lower_bound = first key >= x
    auto low = mp.lower_bound(x);

    // upper_bound = first key > x
    auto up  = mp.upper_bound(x);

    int smaller = distance(mp.begin(), low);  // keys < x
    int equal   = distance(low, up);          // keys == x (0 or 1 in map)
    int greater = distance(up, mp.end());     // keys > x

    cout << "Count keys smaller than " << x << ": " << smaller << endl;
    cout << "Count keys equal to "   << x << ": " << equal   << endl;
    cout << "Count keys greater than " << x << ": " << greater << endl;

    return 0;
}
```

------------------------------------------------------------------------

## 🧮 For `multiset` / `multimap`

If duplicates exist, use **`equal_range`** to count them:

``` cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    multiset<int> ms = {1, 2, 2, 2, 3, 4, 5, 5};
    int x = 2;

    // Precompute lower_bound and upper_bound
    auto low = ms.lower_bound(x); // first element >= x
    auto up  = ms.upper_bound(x); // first element > x

    // Equal count (elements == x)
    int equal = distance(low, up);

    // Greater than x
    int greater = distance(up, ms.end());

    // Greater than or equal to x
    int greater_equal = distance(low, ms.end());

    // Smaller than x
    int smaller = distance(ms.begin(), low);

    // Smaller than or equal to x
    int smaller_equal = distance(ms.begin(), up);

    cout << "Equal to " << x << ": " << equal << endl;
    cout << "Greater than " << x << ": " << greater << endl;
    cout << "Greater or equal to " << x << ": " << greater_equal << endl;
    cout << "Smaller than " << x << ": " << smaller << endl;
    cout << "Smaller or equal to " << x << ": " << smaller_equal << endl;

    return 0;
}
```

------------------------------------------------------------------------

## 💡 Key Point

-   `vector` → random access iterators → supports `it - begin()`
-   `set`, `map` → bidirectional iterators → ❌ no subtraction, use
    `std::distance()`
-   `lower_bound`, `upper_bound`, `equal_range` all work in **sorted
    containers**
