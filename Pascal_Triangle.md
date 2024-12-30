# :flying_saucer: Pascal Triangle :rocket:
<img align="center" alt="Pascal Triangle" height="250" width="200" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif">

### :construction: Find the element at that place where Row and Column number given (indexing from 1)


`r = Row - 1 <br>` <br>
`c = Column - 1`

Required element is: `nCr = n! / (r! * (n - r)!)`

#### :tornado: Code for above question

```cpp
#include <bits/stdc++.h>
using namespace std;

int nCr(int n, int r) {
    long long res = 1;

    // calculating nCr:
    for (int i = 0; i < r; i++) {
        res = res * (n - i);
        res = res / (i + 1);
    }
    return res;
}

int pascalTriangle(int r, int c) {
    int element = nCr(r - 1, c - 1);
    return element;
}

int main()
{
    int r = 5; // row number
    int c = 3; // col number
    int element = pascalTriangle(r, c);
    cout << "The element at position (r,c) is: "
            << element << "n";
    return 0;
}
```

<hr></hr>
### :tornado: Print Nth row of pascal triangle

<img align="center" alt="Pascal trianlge element shortcut" height="350" width="400" src="https://static.takeuforward.org/wp/uploads/2023/04/Screenshot-2023-04-30-214245.png">

#### :zap: Code for above question
```cpp
#include <bits/stdc++.h>
using namespace std;

void pascalTriangle(int n) {
    long long ans = 1;
    cout << ans << " "; // printing 1st element

    //Printing the rest of the part:
    for (int i = 1; i < n; i++) {
        ans = ans * (n - i);
        ans = ans / i;
        cout << ans << " ";
    }
    cout << endl;
}

int main()
{
    int n = 5;
    pascalTriangle(n);
    return 0;
}
```
<hr></hr>

### :snowman: Code to print pascal triangle
```cpp
#include <bits/stdc++.h>
using namespace std;

int nCr(int n, int r) {
    long long res = 1;

    // calculating nCr:
    for (int i = 0; i < r; i++) {
        res = res * (n - i);
        res = res / (i + 1);
    }
    return (int)(res);
}

vector<vector<int>> pascalTriangle(int n) {
    vector<vector<int>> ans;

    //Store the entire pascal's triangle:
    for (int row = 1; row <= n; row++) {
        vector<int> tempLst; // temporary list
        for (int col = 1; col <= row; col++) {
            tempLst.push_back(nCr(row - 1, col - 1));
        }
        ans.push_back(tempLst);
    }
    return ans;
}

int main()
{
    int n = 5;
    vector<vector<int>> ans = pascalTriangle(n);
    for (auto it : ans) {
        for (auto ele : it) {
            cout << ele << " ";
        }
        cout << "n";
    }
    return 0;
}
```

:comet: Output: <br>
1 <br>
1 1 <br>
1 2 1 <br>
1 3 3 1 <br>
1 4 6 4 1