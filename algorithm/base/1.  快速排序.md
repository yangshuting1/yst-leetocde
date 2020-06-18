### 典型算法——快速排序

将数组进行排序


### 思路

快速排序算法通过多次比较和交换来实现排序
设置一个基准值，将小于基准数的放在基准数前，大于的放在基准数后面. 以此迭代循环。


#### 解题思想:

1. 首先找到一个基准数，设置两个指针，分别从右和从左进行和基准对比
2. 从右开始，如果值大于基准数，下边-1. 继续比较，如果值小于基准数，进行交换。
3. 从左开始，如果值小于基准数，下边+1. 继续比较，如果大小于基准数，进行交换。
4. 重复上述过程，可以看出，这是一个递归定义。通过递归将左侧部分排好序后，再递归排好右侧部分的顺序。当左、右两个部分各数据排序完成后，整个数组的排序也就完成了

### 时间复杂度

O (nlogn)

### 代码
```java
 public static void quickSearch(int[] array, int L, int R) {
        int pivot = array[L];
        int left = L;
        int right = R;
        if(L >= R){
            return;
        }
        while (left < right) {
            while (left < right && array[right] >= pivot) {
                right--;
            }
            if (left < right) {
                array[left] = array[right];
            }
            while (left < right && array[left] <= pivot) {
                left++;
            }
            if (left < right) {
                array[right] = array[left];
            }
            if(left >= right){
                array[left] = pivot;

            }
        }
        quickSearch(array, L, right - 1);
        quickSearch(array, left + 1, R);
    }
```
