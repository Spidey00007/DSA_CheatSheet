A multiset, also known as a bag, is a collection of elements that allows duplicate elements, unlike a traditional set where each element must be unique.

The issue is that multiset::erase only removes one occurrence of the element, but it requires an iterator for the specific element you want to remove, not the element's value directly. In your case, calling ms.erase(nums[l]) might not correctly remove the element because nums[l] is the value, and the multiset can contain multiple occurrences of the same value.

### erase specific value
```cpp
ms.erase(ms.find(nums[l]));
```

NOTE: Use ms.rbegin() to access last element not ms.end().
NOTE: The find function does not return a bool. Instead, it returns an iterator to the first occurrence of the specified value. If the value is not found, it returns the end() iterator.

#### Accessing a Specific Value
```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    multiset<int> ms = {10, 20, 20, 30};

    // Find the first occurrence of 20
    auto it = ms.find(20);
    if (it != ms.end()) {
        cout << "First occurrence of 20: " << *it << endl;
    }

    return 0;
}
```

## Practice a leetcode important problem
1438. Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit