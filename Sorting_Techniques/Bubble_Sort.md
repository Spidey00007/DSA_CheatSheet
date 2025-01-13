# 🛸 Bubble Sort 🚀

<img align="center" alt="Bubble Sort" height="300" width="600" src="https://miro.medium.com/v2/resize:fit:1400/1*GUkhhrPDfgdvvwVFo-il1g.gif">

---

# 📚 Bubble Sort Algorithm

## ✨ Overview
Bubble Sort is a simple sorting algorithm that repeatedly steps through the array, compares adjacent elements, and swaps them if they are in the wrong order. The process is repeated until the array is sorted.

### 🛠️ Characteristics
- **Time Complexity**:  
  - Best Case: `O(n)` (When the array is already sorted)  
  - Worst Case: `O(n²)`  
- **Space Complexity**: `O(1)` (In-place sorting)


---

## 🚀 How it Works
1. Start at the beginning of the array.
2. Compare adjacent elements and swap them if necessary (larger element moves to the right).
3. Continue this process for all elements in the array.
4. Repeat the process for the remaining unsorted part of the array until no swaps are needed.

---

## 🧑‍💻 Implementation in C++

```cpp
#include <iostream>
#include <vector>
using namespace std;

void bubbleSort(vector<int>& nums) {
    int n=nums.size();
    for(int i=n-2; i>=0; i--) {
        bool isSwap=false;
        for(int j=0; j<=i; j++) {
            if(nums[j] > nums[j+1]) {
                swap(nums[j], nums[j+1]);
                isSwap=true;
            }
        }
        if(!isSwap) break;
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

    bubbleSort(arr);

    cout << "✅ Sorted array: ";
    printArray(arr);

    return 0;
}
```