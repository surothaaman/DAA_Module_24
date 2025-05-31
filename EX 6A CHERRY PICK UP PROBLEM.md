# EX 6A CHERRY PICK UP PROBLEM
## DATE:26.04.2025
## AIM:
To Create a python program for the following problem statement.
You are given an n x n grid representing a field of cherries, each cell is one of three possible integers.
0	means the cell is empty, so you can pass through,
1	means the cell contains a cherry that you can pick up and pass through, or
-1 means the cell contains a thorn that blocks your way.
Return the maximum number of cherries you can collect by following the rules below:
Starting at the position (0, 0) and reaching (n - 1, n - 1) by moving right or down through valid path cells (cells with value 0 or 1).
After reaching (n - 1, n - 1), returning to (0, 0) by moving left or up through valid path cells.
When passing through a path cell containing a cherry, you pick it up, and the cell becomes an empty cell 0. If there is no valid path between (0, 0) and (n - 1, n - 1), then no cherries can be collected.

## Algorithm:
```
1.Initialize a 3D DP table dp[row][col1][col2] to store the maximum cherries collected by two robots at positions col1 and col2 in row row.
2.Set the base case with both robots starting at the top row, one at column 0 and the other at the last column.
3.Iterate through each row from top to bottom.
4.For each possible column position of both robots, compute the current cherries picked (avoid double-count if both robots are on the same cell).
5.Update dp[row][col1][col2] by checking all possible previous positions (col1 ± 1, col2 ± 1) from the row above.
6.Return the maximum cherries collected when both robots reach the last row.
```
## Program:
```
To implement the program for Cherry pickup problem.


Developed by: M.PAVITHRA
Register Number:212222100032
class Solution(object):
    def cherryPickup(self, grid):
        ROW_NUM = len(grid)
        COL_NUM = len(grid[0])
        dp = [[[float('-inf')] * COL_NUM for _ in range(COL_NUM)] for _ in range(ROW_NUM)]
        dp[0][0][COL_NUM - 1] = grid[0][0] + grid[0][COL_NUM - 1]
        for i in range(1, ROW_NUM):
            for j1 in range(COL_NUM):
                for j2 in range(COL_NUM):
                    curr_cherries = grid[i][j1]
                    if j1 != j2:
                        curr_cherries += grid[i][j2]
                    for prev_j1 in range(j1 - 1, j1 + 2):
                        for prev_j2 in range(j2 - 1, j2 + 2):
                            if 0 <= prev_j1 < COL_NUM and 0 <= prev_j2 < COL_NUM:
                                prev_cherries = dp[i - 1][prev_j1][prev_j2]
                                dp[i][j1][j2] = max(dp[i][j1][j2], curr_cherries + prev_cherries)
        
        return max(0, dp[ROW_NUM - 1][0][COL_NUM - 1])
        
grid=[[3,1,1],
      [2,5,1],
      [1,5,5],
      [2,1,1]]
ob=Solution()
print(ob.cherryPickup(grid))
```

## Output:

![Screenshot 2025-05-06 114433](https://github.com/user-attachments/assets/02d18f39-8107-461a-aea7-6361adda4773)

## Result:
Thus the above program was executed successfully for finding the maximum number of cherries from grid.
