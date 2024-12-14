# :rocket: Gap Method for Merging Sorted Arrays :star2:

## :bulb: Overview
The **Gap Method** is an efficient algorithm to merge two sorted arrays without using extra space. It progressively reduces the gap between compared elements until the arrays are fully merged.

---

## :gear: Steps of the Algorithm
1. **Initialize the gap**:
   - Start with a gap equal to the combined size of the two arrays:  
     \[
     \text{gap} = \lceil \frac{m+n}{2} \rceil
     \]
   - Reduce the gap in each iteration:  
     \[
     \text{gap} = \lceil \frac{\text{gap}}{2} \rceil
     \]
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

void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
    int gap = (m + n + 1) / 2; // Initialize gap

    while (gap > 0) {
        int i = 0, j = gap;
        
        while (j < m + n) {
            int num1 = (i < m) ? nums1[i] : nums2[i - m];
            int num2 = (j < m) ? nums1[j] : nums2[j - m];

            if (num1 > num2) {
                if (i < m && j < m) {
                    swap(nums1[i], nums1[j]);
                } else if (i < m) {
                    swap(nums1[i], nums2[j - m]);
                } else {
                    swap(nums2[i - m], nums2[j - m]);
                }
            }

            i++;
            j++;
        }

        // Reduce the gap for the next iteration
        gap = (gap == 1) ? 0 : (gap + 1) / 2;
    }
}
```

## :chart_with_upwards_trend: Complexity Analysis

### Time Complexity:
\[
O((m+n) \log(m+n))
\]  
- The gap reduces logarithmically, and each pass involves linear traversal.

### Space Complexity:
\[
O(1)
\]  
- No extra space is used aside from a few variables.
