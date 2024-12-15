### :memo: next_permutation ➡️

It gives the next lexicographically greater permutation.
So, if the container is already the greatest permutation (descending order), it returns nothing.

This function rearranges the elements in the range [nums.begin(), nums.end()) to the next lexicographically greater permutation. It returns true if the next permutation is generated and false if the sequence is already the largest permutation (in this case the sequence is rearranged to the smallest permutation).


vector<int> vec{1, 2, 3, 4};
    
if(next_permutation(begin(vec), end(vec)))
    cout << "Next permutation available" << endl;

for(int &x : vec)
    cout << x << " ";
    
//Output : 1, 2, 4, 3

Also : prev_permutation() - It gives just the previous lexicographically smaller permutation.
    Leetcode - 31  : Next Permutation

### 🌋 Code implementation of std: next_permutation :desert:
```cpp
void nextPermutation(vector<int>& nums) {
    int index = -1, n=nums.size();
    for(int i=n-2; i>=0; i--) {
        if(nums[i] < nums[i+1]) {
            index = i;
            break;
        }
    }
    if(index == -1) {
        reverse(nums.begin(), nums.end());
        return;
    }
    for(int i=n-1; i>index; i--) {
        if(nums[i] > nums[index]) {
            swap(nums[i], nums[index]);
            break;
        }
    }
    reverse(nums.begin()+index+1, nums.end());
}
```