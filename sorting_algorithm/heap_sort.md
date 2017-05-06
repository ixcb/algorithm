# 堆排序

## 维基百科
> 堆排序（Heapsort）是指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。
>
> ### 堆节点的访问
>
>通常堆是通过一维数组来实现的。在数组起始位置为0的情形中：
> * 父节点i的左子节点在位置(2*i+1);
> * 父节点i的右子节点在位置(2*i+2);
> * 子节点i的父节点在位置floor((i-1)/2);
>
> ### 堆的操作
> 在堆的数据结构中，堆中的最大值总是位于根节点(在优先队列中使用堆的话堆中的最小值位于根节点)。堆中定义以下几种操作：
> * 最大堆调整（Max_Heapify）：将堆的末端子节点作调整，使得子节点永远小于父节点
> * 创建最大堆（Build_Max_Heap）：将堆所有数据重新排序
> * 堆排序（HeapSort）：移除位在第一个数据的根节点，并做最大堆调整的递归运算

```python
# 最大堆调整
def heapify(arr, start, end):
    lchild = 2 * start + 1
    rchild = 2 * start + 2
    max_index = start
    if lchild < end and arr[lchild] > arr[max_index]:
        max_index = lchild
    if rchild < end and arr[rchild] > arr[max_index]:
        max_index = rchild
    if max_index != start:
        arr[max_index], arr[start] = arr[start], arr[max_index]
        heapify(arr, max_index, end)

def heap_sort(arr):
    arr_len = len(arr)
    # 创建最大堆
    for start in range((arr_len-2)/2, -1, -1):
        heapify(arr, start, arr_len)
    # 堆排序
    for end in range(arr_len-1, 0, -1):
        arr[0], arr[end] = arr[end], arr[0]
        heapify(arr, 0, end)
```
