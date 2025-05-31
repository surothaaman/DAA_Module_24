# EX 6B KNAPSACK PROBLEM
## DATE:29.04.2025
## AIM:
To demonstrate a python program using dynamic programming for 0/1 knapsack problem.

## Algorithm:
```
1.Initialize a 2D DP table K[n+1][W+1] where n is the number of items and W is the knapsack capacity.
2.Loop through each item and capacity, starting from 0.
3.If the item index or capacity is 0, set value to 0 (base case).
4.If the current item's weight is less than or equal to the current capacity, compute the maximum of including or excluding the item.
5.Else, inherit the value from the previous item for the same capacity.
6.After filling the table, return K[n][W] as the maximum value that can be carried.
```
## Program:
```

To implement the program for 0/1 knapsack problem.


Developed by: M.PAVITHRA
Register Number:212222100032
def knapSack(W, wt, val, n):
    ########## Add your code here #########
    K = [[0 for x in range(W + 1)] for x in range(n + 1)]
    for i in range(n + 1):
        for w in range(W + 1):
            if i == 0 or w == 0:
                K[i][w] = 0
            elif wt[i-1] <= w:
                K[i][w] = max(val[i-1]+ K[i-1][w-wt[i-1]],K[i-1][w])
            else:
                K[i][w] = K[i-1][w]
 
    return K[n][W]

x=int(input())
y=int(input())
W=int(input())
val=[]
wt=[]
for i in range(x):
    val.append(int(input()))
for y in range(y):
    wt.append(int(input()))

n = len(val)
print('The maximum value that can be put in a knapsack of capacity W is: ',knapSack(W, wt, val, n))
```

## Output:
![Screenshot 2025-05-06 114853](https://github.com/user-attachments/assets/47637dfb-95fd-4273-adb1-d876101cd06f)

## Result:
Thus the program was executed successfully for finding the maximum value that can be put in a knap sack of capacity .
