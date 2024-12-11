### ♻️ Methods of checking perfect square

🔱 Method 1:
```
	int x=sqrt(c-n*n);
	if(x*x == c-n*n) return true;
```

⚜️ Method 2:
```
    double sqrtNum = sqrt(num);
    return floor(sqrtNum) == ceil(sqrtNum);
```
		
⚕️ Method 3:
```
	double x=sqrt(num);
	return x==int(x);
```


:octocat: NOTE : Time complexity of sqrt(x) is O(logn)