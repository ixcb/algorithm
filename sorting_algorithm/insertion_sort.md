# 插入排序

```python
def insertion_sort(arr):
    arr_len = len(arr)
    for i in range(1, arr_len):
        key = arr[i]
        j = i - 1
        while j >= 0:
            if arr[j] > key:
                arr[j + 1] = arr[j]
                arr[j] = key
            j -= 1
    return arr
```
