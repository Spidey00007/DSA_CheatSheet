# 🛸 Selection Sort 🚀

<img align="center" alt="Selection Sort" height="300" width="600" src="https://miro.medium.com/v2/resize:fit:1400/1*5WXRN62ddiM_Gcf4GDdCZg.gif">

---

# 📚 Selection Sort Algorithm

## ✨ Overview
Selection Sort is a simple comparison-based sorting algorithm. It repeatedly selects the smallest (or largest) element from the unsorted part and moves it to the sorted part.

### 🛠️ Characteristics
- **Time Complexity**:  
  - Best Case: `O(n²)`  
  - Worst Case: `O(n²)`
- **Space Complexity**: `O(1)` (In-place sorting)

---

## 🚀 How it Works
1. Divide the array into two parts: sorted and unsorted.
2. Find the smallest element in the unsorted part.
3. Swap it with the first element of the unsorted part.
4. Repeat until the entire array is sorted.

---

## 🧑‍💻 Implementation in C++

```cpp
#include <iostream>
#include <vector>
using namespace std;

void selectionSort(vector<int> &nums) {
    
    for(int i=0; i<nums.size(); i++) {
        int idx=i;
        for(int j=i; j<nums.size(); j++) {
            if(nums[j]<nums[idx]) {
                idx=j;
            }
        }
        swap(nums[i], nums[idx]);
    }
}

void printArray(const vector<int>& arr) {
    for (int num : arr) {
        cout << num << " ";
    }
    cout << endl;
}

int main() {
    vector<int> arr = {64, 25, 12, 22, 11};
    cout << "🔢 Original array: ";
    printArray(arr);

    selectionSort(arr);

    cout << "✅ Sorted array: ";
    printArray(arr);

    return 0;
}
```