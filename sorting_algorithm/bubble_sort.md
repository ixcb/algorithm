#冒泡排序
------
```python
def bubble_sort(arr):
    arr_len = len(arr)
    for i in range(0, arr_len-1):
        for j in range(i+1, arr_len):
            if arr[i] > arr[j]:
                arr[i], arr[j] = arr[j], arr[i]
    return arr
```
