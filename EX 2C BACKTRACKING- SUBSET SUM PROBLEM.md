# EX 2C BACKTRACKING- SUBSET SUM PROBLEM

## DATE: 05-05-2025

## AIM:

To demonstrate that the sum of the subset of a given set is equal to the given sum.

## Algorithm

1. Initialize a count to 0 and start with index 0.

2. If the current index equals the array size, check if the sum is 0 and increment the count if true.

3. Recursively include or exclude the current element and adjust the sum accordingly.

4. Return the total count of valid subsets.

5. Print the final result after processing all elements.

## Program:

```python
# Program to implement Subset sum problem.


def subsetSum(arr, n, i,sum, count):
    if i == n:
        if sum == 0:
            return count + 1
        return count

    count = subsetSum(arr, n, i + 1, sum - arr[i], count)

    count = subsetSum(arr, n, i + 1, sum, count)

    return count

arr=[]
size=int(input())
for j in range(size):
    value=int(input())
    arr.append(value)
sum = int(input())
n = len(arr)

print(subsetSum(arr, n, 0, sum, 0))

```

## Output:

<img width="741" height="764" alt="image" src="https://github.com/user-attachments/assets/3bdfb278-eb8c-4e50-9daf-27901b5777b4" />

## Result:

The Subset Sum program executed successfully, and the result was determined based on whether a subset matching the target sum was found or not.
