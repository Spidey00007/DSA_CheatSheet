### :cyclone: Making prefix sum

```cpp
vector<int> prefix(n);
// Initialize first element
prefix[0] = nums[0];
for(int i=1; i<nums.size(); i++) {
	prefix[i] = prefix[i-1] + nums[i];
}

```

### :dragon: Accessing prefix sum in range of (left & right)

```cpp
sum=prefix[right]-prefix[left]+nums[left];

```
