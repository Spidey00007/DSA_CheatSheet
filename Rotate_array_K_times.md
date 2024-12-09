## :heart_on_fire: The std::reverse function operates on a half-open range [start, end). This means:       :heart_on_fire:
It includes the element at start.
It excludes the element at end.


### :hotsprings: Rotate array k times left:

```                                                       
// Reverse the first k elements (0 to k-1)
reverse(nums.begin(), nums.begin() + k);

// Reverse the remaining elements (k to n-1)
reverse(nums.begin() + k, nums.end());

// Reverse the entire array (0 to n-1)
reverse(nums.begin(), nums.end());
```

### :rocket: Rotate array k times right:

```                                                
// Reverse the first part (0 to n-k-1)
reverse(nums.begin(), nums.begin() + (n - k));

// Reverse the second part (n-k to n-1)
reverse(nums.begin() + (n - k), nums.end());

// Reverse the entire array
reverse(nums.begin(), nums.end());
```