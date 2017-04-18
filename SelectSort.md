# SelectSort #
## 选择排序法，通过n-1次关键字间的比较，从n-i+1个记录中选出关键字最小的记录，并和第i个记录交换
```java
public static void SelSort(int[] a){
		int i,j,min;
		int len=a.length;
		for(i=0;i<len;i++){
				min=i;  //将当前下标定义为最小值下标
			for(j=i+1;j<len;j++){  //循环之后的数据
				if(a[min]>a[j]){
					min=j;  //如果有小于当前最小值的关键字，将此关键字的下标赋值给min
				}
			}
			if(i!=min){  //若min不等于i，说明找到最小值，交换
				int temp=a[i];
				a[i]=a[min];
				a[min]=temp;
			}
		}
		for (int k : a) {
			System.out.print(k+"     ");
		}
	}
```
### 选择排序最大的特点就是交换移动次数相当少，节约相应的时间.无论最好最坏情况，其比较次数都是一样多，即(1/2)*n(n-1).对于交换次数而言，最好的情况，交换次数为0次，最差的时候为n-1，最终的排序时间为比较和交换的总和，总的时间复杂度依然为O(n^2)，简单排序性能略优于冒泡排序.