# 归并排序

## 维基百科
> 归并排序（英语：Merge sort，或mergesort），是创建在归并操作上的一种有效的排序算法，效率为O(n log n)。1945年由约翰·冯·诺伊曼首次提出。该算法是采用分治法（Divide and Conquer）的一个非常典型的应用，且各层分治递归可以同时进行。
>
> ### 递归法
> 原理如下（假设序列共有n个元素）：
> 1. 将序列每相邻两个数字进行归并操作，形成 **floor(n/2)** 个序列，排序后每个序列包含两个元素
> 2. 将上述序列再次归并，形成 **floor(n/4)** 个序列，每个序列包含四个元素
> 3. 重复步骤2，直到所有元素排序完毕。

```python
def merge(left, right):
    i, j = 0, 0
    result = []
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result += left[i:]
    result += right[j:]
    return result

def merge_sort(arr):
    arr_len = len(arr)
    if arr_len <= 1:
        return arr
    mid = arr_len / 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)
```
