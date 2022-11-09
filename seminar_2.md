# Arrays

## module 1: the sum of the elements of the main and side diagonals

```python
def diag_sum(a):
    result = 0
    for i in range(len(a)):
        if i == len(a) - 1 - i:
            result += a[i][i]
        else:
            result += (a[i][i] + a[i][len(a) - 1 - i])
    return result
```
## module 2: merge sort for 2 lines

```python
def merge(str_1, str_2):
    sort_arr, i, j, k = [0 for _ in range(len(str_1) + len(str_2))], 0, 0, 0
    while i < len(str_1) and j < len(str_2):
        if str_1[i] <= str_2[j]:
            sort_arr[k] = str_1[i]
            i += 1
        else:
            sort_arr[k] = str_2[j]
            j += 1
        k += 1

    if i < len(str_1):
        sort_arr[k:] = str_1[i:]
    elif j < len(str_2):
        sort_arr[k:] = str_2[j:]

    return sort_arr
```

## module 3: calculating squares for sorted string whith sorting at the end
```python
def square(numbers):
    for i in range(len(numbers)):
        if numbers[i] >= 0:
            pos = i + 1
            break

    negative = [numbers[i] ** 2 for i in range(pos - 1, -1, -1)]
    positive = [numbers[i] ** 2 for i in range(pos, len(numbers))]

    return merge(negative, positive)
```
## module 4: reductions of repetitions
```python
def cut(string):
    num, count, ans = string[0], 1, []
    for i in range(len(string) - 1):
        if string[i + 1] == string[i]:
            count += 1
        else:
            ans.append(num)
            if count != 1:
                ans.append(count)
            num = string[i + 1]
            count = 1
    ans.append(num)
    if count != 1:
        ans.append(count)
    return ans
```
## calling all functions
```python
if __name__ == '__main__':
    arr = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    print('number 1: ', diag_sum(arr))

    first, second = [1, 20, 30], [30, 40]
    print('number 2: ', merge(first, second))

    start = [-10, -3, 0, 4, 7]
    print('number 4: ', square(start))

    str1 = ["a", "b", "b", "c", "c", "c"]
    str2 = ["d", "a", "b", "c"]
    str3 = ["c", "c", "c"]

    print('number 3:')
    print(*cut(str1), sep='')
    print(*cut(str2), sep='')
    print(*cut(str3), sep='')
```