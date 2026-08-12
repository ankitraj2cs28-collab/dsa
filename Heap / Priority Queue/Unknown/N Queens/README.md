# N Queens

| Field | Value |
|-------|-------|
| **Platform** | LeetCode |
| **Difficulty** | Unknown |
| **Language** | cpp |
| **Solved On** | August 12, 2026 |
| **Link** | [View Problem](https://leetcode.com/problems/n-queens/) |
| **Runtime** | 0 ms |
| **Memory** | 10.4 MB |

## 🏆 Top Community Optimal Approach

<details>
<summary>Click to expand</summary>

**Title**: [C++] 4ms Heavily Commented Clean Solution | Fast & Easy | Explanation
**Author**: [@vector_long_long](https://leetcode.com/vector_long_long/)
**Upvotes**: 179 👍
**Link**: [View Original Post](https://leetcode.com/problems/n-queens/solutions/810358/)

---

```
class Solution {
public:
    vector<vector<string>> ret;
    bool is_valid(vector<string> &board, int row, int col){
        // check col
        for(int i=row;i>=0;--i)
            if(board[i][col] == \'Q\') return false;
        // check left diagonal
        for(int i=row,j=col;i>=0&&j>=0;--i,--j)
            if(board[i][j] == \'Q\') return false;
        //check right diagonal
        for(int i=row,j=col;i>=0&&j<board.size();--i,++j)
            if(board[i][j] == \'Q\') return false;
        return true;
    }
    void dfs(vector<string> &board, int row){
        // exit condition
        if(row == board.size()){
            ret.push_back(board);
            return;
        }
        // iterate every possible position
        for(int i=0;i<board.size();++i){
            if(is_valid(board,row,i)){
                // make decision
                board[row][i] = \'Q\';
                // next iteration
                dfs(board,row+1);
                // back-tracking
                board[row][i] = \'.\';
            }
        }
    }
    vector<vector<string>> solveNQueens(int n) {
		// return empty if n <= 0
        if(n <= 0) return {{}};
        vector<string> board(n,string(n,\'.\'));
        dfs(board,0);
        return ret;
    }
};
```

</details>
