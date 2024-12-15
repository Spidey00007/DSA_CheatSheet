# 🛸 Merge Sort 🚀

<img align="center" alt="Merge Sort" height="250" width="200" src="https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif">

---

### 🏗️ Concept of Merge Sort

Merge Sort is a **divide and conquer** algorithm. It works by recursively dividing the input array into two halves, sorting each half, and then merging the sorted halves.

Steps involved:
1. **Divide** the array into two halves.
2. **Sort** each half recursively.
3. **Merge** the two sorted halves into one sorted array.

---

#### :flying_saucer: Code for Merge Sort with extra space, Space Complexity: O(n)

```cpp
#include <bits/stdc++.h>
using namespace std;


void merge(int l, int mid, int r, vector<int>& nums) {
    vector<int> temp(r-l+1);
    int index=0, left=l, right=mid+1;
    while(left<=mid && right<=r) {
        if(nums[left] <= nums[right]) {
            temp[index]=nums[left];
            index++;
            left++;
        }
        else {
            temp[index]=nums[right];
            index++;
            right++;
        }
    }
    while(left<=mid) {
        temp[index]=nums[left];
        index++;
        left++;
    }
    while(right<=r) {
        temp[index]=nums[right];
        index++;
        right++;
    }
    
    // Copying elements from temp to nums
    for(int i=l; i<=r; i++) {
        nums[i]=temp[i-l];
    }
}

void mergeSort(int l, int r, vector<int>& nums) {
    if(l >= r) {
        return;
    }

    int mid=l+(r-l)/2;
    mergeSort(l, mid, nums);
    mergeSort(mid+1, r, nums);
    merge(l, mid, r, nums);
}


int main() {

    vector<int> nums = {9, 4, 7, 6, 3, 1, 5}  ;
    int n = nums.size();

    cout << "Before Sorting Array: " << endl;
    for (int i = 0; i < n; i++) {
        cout << nums[i] << " "  ;
    }
    cout << endl;

    mergeSort(0, n - 1, nums);

    cout << "After Sorting Array: " << endl;
    for (int i = 0; i < n; i++) {
        cout << nums[i] << " "  ;
    }
    cout << endl;
    return 0 ;
}
```

---

### :flying_saucer: Code for Merge Sort without extra space
#### Gap method: Intitution comes from "Shell Sorting", Space Complexity: O(1)

```
#include <bits/stdc++.h>
using namespace std;

void merge(int l, int r, vector<int>& nums) {
    int len=r-l+1;
    int gap=len;
    
    while(gap>0) {
        gap=(gap/2) + (gap%2);
        for(int i=gap; i<len; i++) {
            if(nums[i] < nums[i-gap]) {
                swap(nums[i], nums[i-gap]);
            }
        }
        if(gap==1) {
            break;
        }
    }
}

void mergeSort(int l, int r, vector<int>& nums) {
    if(l >= r) {
        return;
    }

    int mid=l+(r-l)/2;
    mergeSort(l, mid, nums);
    mergeSort(mid+1, r, nums);
    merge(l, r, nums);
}


int main() {

    vector<int> nums = {9, 4, 7, 6, 3, 1, 5}  ;
    int n = nums.size();

    cout << "Before Sorting Array: " << endl;
    for (int i = 0; i < n; i++) {
        cout << nums[i] << " "  ;
    }
    cout << endl;

    mergeSort(0, n - 1, nums);

    cout << "After Sorting Array: " << endl;
    for (int i = 0; i < n; i++) {
        cout << nums[i] << " "  ;
    }
    cout << endl;
    return 0 ;
}
```