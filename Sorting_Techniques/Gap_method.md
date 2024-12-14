# :rocket: Gap Method for Merging Sorted Arrays :star2:

## :bulb: Overview
The **Gap Method** is an efficient algorithm to merge two sorted arrays without using extra space. It progressively reduces the gap between compared elements until the arrays are fully merged.

---

## :gear: Steps of the Algorithm
1. **Initialize the gap**:
   - Start with a gap equal to the combined size of the two arrays: <br>
    Initial gap = ceil((size of arr1[] + size of arr2[]) / 2) <br>
    gap = ceil( previous gap / 2) <br>
     until the gap becomes zero.

2. **Compare and Swap Elements**:
   - Compare elements separated by the gap:
     - If the element on the left is greater than the element on the right, **swap them**.
   - Perform comparisons:
     - **Within `nums1`**  
     - **Between `nums1` and `nums2`**  
     - **Within `nums2`**

3. **Repeat Until the Gap Becomes Zero**:
   - Continue reducing the gap and performing comparisons until all elements are in sorted order.

---

## :zap: Code Implementation
```cpp
#include <bits/stdc++.h>
using namespace std;

void swapIfGreater(long long arr1[], long long arr2[], int ind1, int ind2) {
    if (arr1[ind1] > arr2[ind2]) {
        swap(arr1[ind1], arr2[ind2]);
    }
}

void merge(long long arr1[], long long arr2[], int n, int m) {
    // len of the imaginary single array:
    int len = n + m;

    // Initial gap:
    int gap = (len / 2) + (len % 2);

    while (gap > 0) {
        // Place 2 pointers:
        int left = 0;
        int right = left + gap;
        while (right < len) {
            // case 1: left in arr1[]
            //and right in arr2[]:
            if (left < n && right >= n) {
                swapIfGreater(arr1, arr2, left, right - n);
            }
            // case 2: both pointers in arr2[]:
            else if (left >= n) {
                swapIfGreater(arr2, arr2, left - n, right - n);
            }
            // case 3: both pointers in arr1[]:
            else {
                swapIfGreater(arr1, arr1, left, right);
            }
            left++, right++;
        }
        // break if iteration gap=1 is completed:
        if (gap == 1) break;

        // Otherwise, calculate new gap:
        gap = (gap / 2) + (gap % 2);
    }
}

int main()
{
    long long arr1[] = {1, 4, 8, 10};
    long long arr2[] = {2, 3, 9};
    int n = 4, m = 3;
    merge(arr1, arr2, n, m);
    cout << "The merged arrays are: " << "\n";
    cout << "arr1[] = ";
    for (int i = 0; i < n; i++) {
        cout << arr1[i] << " ";
    }
    cout << "\narr2[] = ";
    for (int i = 0; i < m; i++) {
        cout << arr2[i] << " ";
    }
    cout << endl;
    return 0;
}
```

## :chart_with_upwards_trend: Complexity Analysis

### Time Complexity: O((n+m)*log(n+m)), where n and m are the sizes of the given arrays.
- Reason: The gap reduces logarithmically, and each pass involves linear traversal.

### Space Complexity: O(1) as we are not using any extra space. 