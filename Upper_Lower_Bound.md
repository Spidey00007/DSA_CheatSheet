## :memo: upper_bound(), lower_bound() in sorted vector, ordered set, ordered map :outbox_tray:
### Vector
```cpp
vector<int> vec{10,20,30,30,20,10,10,20};
vector<int> up  = upper_bound(begin(vec), end(vec), 35);//returns iterator to first element "greater" than 35
vector<int> low = lower_bound(begin(vec), end(vec), 35);//returns iterator to first element "greater or equal" to 35
cout << "upper_bound at position " << (up - vec.begin()) << '\n';
cout << "lower_bound at position " << (low - vec.begin()) << '\n';
```

### Set
```cpp
st.upper_bound(35); //returns iterator to first element "greater" than 35
st.lower_bound(35); //returns iterator to first element "greater or equal" than 35
```

### Map
```cpp
mp.upper_bound(35); //returns iterator to first element "greater" than 35
mp.lower_bound(35); //returns iterator to first element "greater or equal" than 35
```

Practice problem : [My Calendar I](https://leetcode.com/problems/my-calendar-i/description/)