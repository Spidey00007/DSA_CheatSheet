# 🛸 Insertion Sort 🚀

<img align="center" alt="Insertion Sort" height="300" width="600" src="https://miro.medium.com/v2/resize:fit:1012/format:webp/1*JP-wURjwf4k23U2G3GNQDw.gif">

---

<img align="center" alt="Insertion Sort" height="300" width="600" src="https://images.velog.io/images/delmasong/post/9a836b65-dcf7-48d9-8d6c-0e6307704b43/insertionSort.gif">

---

# 📚 Insertion Sort Algorithm

## ✨ Overview
Insertion Sort is a simple and intuitive sorting algorithm that builds the sorted array one item at a time by comparing each new item with the already sorted elements and inserting it into its correct position.

### 🛠️ Characteristics
- **Time Complexity**:  
  - Best Case: `O(n)` (When the array is already sorted)  
  - Worst Case: `O(n²)`  
- **Space Complexity**: `O(1)` (In-place sorting)

---

## 🚀 How it Works
1. Divide the array into sorted and unsorted parts.
2. Pick the first element from the unsorted part.
3. Compare it with the elements of the sorted part and insert it into its correct position.
4. Repeat the process for all elements until the unsorted part is empty.

---

## 🧑‍💻 Implementation in C++

```cpp
#include <iostream>
#include <vector>
using namespace std;

void insertionSort(vector<int>& nums) {
    for(int i=1; i<nums.size(); i++) {
        int j=i;
        while(j>0 && nums[j]<nums[j-1]) {
            swap(nums[j], nums[j-1]);
            j--;
        }
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

    insertionSort(arr);

    cout << "✅ Sorted array: ";
    printArray(arr);

    return 0;
}
```