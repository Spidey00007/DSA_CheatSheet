### :trollface: Practice : 1636. Sort Array by Increasing Frequency

```cpp
class Solution {
public:
    vector<int> frequencySort(vector<int>& nums) {
        unordered_map<int,int> mp;
        for(int &num:nums) {
            mp[num]++;
        }
        auto lambda=[&](int &a, int &b) {
            if(mp[a]==mp[b]) return a>b;  // when freq is same then greater no will come before
            return mp[a]<mp[b];   // Else smaller freq will come first
        };
        sort(nums.begin(), nums.end(), lambda);
        return nums;
    }
};
```

```cpp		
class Solution {
public:
    vector<int> frequencySort(vector<int>& nums) {
        vector<int> vec(201, 0);
        for(int &num:nums) {
            vec[num+100]++;
        }
        auto lambda=[&] (int &a, int &b) {
            if(vec[a+100]==vec[b+100]) return a>b;
            return vec[a+100]<vec[b+100];
        };
        sort(nums.begin(), nums.end(), lambda);
        return nums;
    }
};
```