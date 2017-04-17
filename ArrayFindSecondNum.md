# 题目描述
### 寻找一个无序一维数组的次大位数，要求时间复杂度为O(n)    
```java
public class NumBig {
	public static void main(String[] args) {
		int[]a=new int[] {3,5,7,6,9,4,2,7};
		int len=a.length-1;
		int big=a[0];
		int bbig=a[1];
		for(int i=2;i<=len;i++){
			if(big<a[i]){
				big=a[i];
			}else if(bbig<a[i]){
				bbig=a[i];
			}
		}
		System.out.println(big);
		System.out.println(bbig);
	}

}

```
