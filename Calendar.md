# 日历表 #
## 当前月份的日历 ##
```java
import java.text.DateFormatSymbols;
import java.util.Calendar;
import java.util.GregorianCalendar;

public class CalendarTest {
	public static void main(String[] args) {
		//构造d作为当前时间
		GregorianCalendar d=new GregorianCalendar();
		int today=d.get(Calendar.DAY_OF_MONTH);
		int month=d.get(Calendar.MONTH);
		//设置d为一个月的开始
		d.set(Calendar.DAY_OF_MONTH, 1);
		int weekday=d.get(Calendar.DAY_OF_WEEK);//当月的第一天是在周几
		//一周的第一天
		int firstDayOfWeek= d.getFirstDayOfWeek();//1
		//indent设置首行的缩进
		int indent=0;
		while(weekday!=firstDayOfWeek){
			indent++;
			d.add(Calendar.DAY_OF_MONTH, -1);
			weekday=d.get(Calendar.DAY_OF_WEEK);
		}
		
		//打印工作日
		String[] weekdayNames=new DateFormatSymbols().getShortWeekdays();
		do
		{
			System.out.printf("%4s",weekdayNames[weekday]);
			d.add(Calendar.DAY_OF_MONTH, 1);
			weekday=d.get(Calendar.DAY_OF_WEEK);
		}while(weekday!=firstDayOfWeek);
		System.out.println();
		
		for(int i=1;i<=indent;i++){//现在看第一行如果字体大，所以把缩进再放大一点
			System.out.print("           ");  //首行的缩进距离
		}
		d.set(Calendar.DAY_OF_MONTH,1);
		do
		{
			//打印天
			int day=d.get(Calendar.DAY_OF_MONTH);
			System.out.printf("%8d",day);    //这里，因为我的eclipse字体设置很小，所以统一的都很小
			//标记当前天数* 原来是这样，你的字体设置很大，所以星期几就很大，所以对应下面的数字间距也要很大
			if(day==today){
				System.out.print("*");
			}
			else{
				System.out.print(" ");
			}
			
			d.add(Calendar.DAY_OF_MONTH,1);
			weekday=d.get(Calendar.DAY_OF_WEEK);
			if(weekday==firstDayOfWeek) System.out.println();
		}
		while(d.get(Calendar.MONTH)==month)	;
		
		if(weekday!=firstDayOfWeek){
			System.out.println();
		}
	}


}


```
