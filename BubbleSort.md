# BubbleSort #
## 两两比较相邻记录的关键字，如果反序则交换
### 普通冒泡算法
```java
public static void Bubble(int [] a){
		int i,j;
		int len=a.length-1;
		for(i=0;i<len;i++){
			for(j=len-1;j>=i;j--){
				//如果相邻两个，前一个数大于后一个数，则交换位置
				if(a[j]>a[j+1]){
					int temp=a[j+1];
					a[j+1]=a[j];
					a[j]=temp;
				}
			}
		}
		System.out.println();
		for (int k : a) {
			System.out.print(k+"    ");
		}
	}
```
### 优化冒泡算法
```java
public static void BubbleOpt(int[] a){
		int i,j;
		boolean flag=true;			 //flag作为标识
		int len=a.length-1;
		long startTime=System.currentTimeMillis();
		for(i=0;i<len && flag;i++){  //flag为false退出循环
			flag=false;			  //初始化flag为false
			for(j=len-1;j>=i;j--){
				if(a[j]>a[j+1]){
					int temp=a[j+1];
					a[j+1]=a[j];
					a[j]=temp;
					flag=true;  //如果数据交换，flag为true
				}
			}
		}
		long endTime=System.currentTimeMillis();
		System.out.println();
		System.out.println("运行时间："+(endTime-startTime));
		System.out.println();
		for (int k : a) {
			System.out.print(k+"    ");
		}
	}
```
### 最好的情况，排序的表本身是有序的，那么就有n-1次比较，时间复杂度为O(n).最坏的情况，待排序的表是逆序的，此时需要比较(1/2)*n(n-1)次，并做等数量级的数据移动，总的时间复杂度为O(n^2).