# 选择排序

### 算法步骤
1. 首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置。
2. 再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。
3. 重复步骤2，直到所有元素均排序完毕。

```python
def selection_sort(arr):
    arr_len = len(arr)
    for i in range(arr_len-1):
        min_index = i
        for j in range(i+1, arr_len):
            if arr[min_index] > arr[j]:
                min_index = j
        arr[min_index], arr[i] = arr[i], arr[min_index]
    return arr
```
