# 题目描述 #
在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
```java
public class Solution {
    public boolean Find(int target, int [][] array) {
        int len = array.length-1;//数组的横向长度
        int j= 0;
        while((len >= 0)&& (j < array[len].length)){//target在数组的中（长宽度）
            if(array[len][j] > target){
                len--;//array[len][0]>target;len--; 上一行
            }else if(array[len][j] < target){
                j++;//array[len][0]<target;j++;下一列
            }else{
                return true;
            }
        }
        return false;
    }
}
```