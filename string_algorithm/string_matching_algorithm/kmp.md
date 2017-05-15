# KMP算法

[字符串匹配的KMP算法](http://www.ruanyifeng.com/blog/2013/05/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm.html)

```python
def get_partial_table(pattern):
    p_len = len(pattern)
    partial_table = [-1] * p_len
    k, j = -1, 0
    while j < p_len-1:
        if k == -1 or pattern[j] == pattern[k]:
            j += 1
            k += 1
            if pattern[j] != pattern[k]:
                partial_table[j] = k
            else:
                partial_table[j] = partial_table[k]
        else:
            k = partial_table[k]
    return partial_table

def kmp_match(string, pattern):
    i, j = 0, 0
    s_len, p_len = len(string), len(pattern)
    partial_table = get_partial_table(pattern)

    while i < s_len and j < p_len:
        if j == -1 or string[i] == pattern[j]:
            i += 1
            j += 1
        else:
            j = partial_table[j]

    if j == p_len:
        return i-j
    else:
        return -1
```
