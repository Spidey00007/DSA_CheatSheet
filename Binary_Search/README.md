### Making prefix sum

```
vector<int> prefix(n);
for(int i=1; i<nums.size(); i++) {
	prefix[i] = prefix[i-1] + nums[i];
}

```

### Accessing prefix sum in range of (left & right)

```
sum=prefix[right]-prefix[left]+nums[l];

```
