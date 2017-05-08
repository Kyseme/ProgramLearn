# reflect学习 #
## 获取方法和字段 ##
```java
	//循环里面所有的构造方法
	public static void printConstrutors(Class c1){
		Constructor[] constructors=c1.getDeclaredConstructors();
		for (Constructor c : constructors) {
			String name=c.getName();
			System.out.print("   ");
			String modifiers=Modifier.toString(c.getModifiers());
			if(modifiers.length()>0)System.out.print(modifiers+" ");
			System.out.print(name+"(");
			
			Class[] pramaTypes=c.getParameterTypes();
			for (int i = 0; i < pramaTypes.length; i++) {
				if(i>0)System.out.print(",");
				System.out.print(pramaTypes[i].getName());
			}
			System.out.println(");");
		}
	}
```
```java
	//循环里面所有的方法
	public static void printMethods(Class c1){
		Method[] methods=c1.getDeclaredMethods();
		for (Method m : methods) {
			//此 Method 对象所表示的方法的正式返回类型
			Class retType=m.getReturnType();
			//String name=m.getName();
			System.out.print("   ");
			String modifiers=Modifier.toString(c1.getModifiers());
			if(modifiers.length()>0)System.out.print(modifiers+" ");
			System.out.print(retType.getName()+"(");
			
			Class[] pramaTypes=m.getParameterTypes();
			for (int i = 0; i < pramaTypes.length; i++) {
				if(i>0)System.out.print(",");
				System.out.print(pramaTypes[i].getName());
			}
			System.out.println(");");
			
		}
	}
```
```java
	//循坏所有字段
	public static void printFields(Class c1){
		//返回 Field 对象的一个数组，这些对象反映此 Class 对象所表示的类或接口所声明的所有字段
		Field[] fields=c1.getDeclaredFields();
		for (Field f : fields) {
			//字段的类型
			Class type=f.getType();
			String name=f.getName();
			System.out.print("   ");
			String modifiers=Modifier.toString(c1.getModifiers());
			if(modifiers.length()>0)System.out.print(modifiers+" ");
			System.out.println(type.getName()+"  "+name);
		}
	}
```
测试函数
```java
	public static void main(String[] args) {
		String name;
		if(args.length>0)name=args[0];
		else{
			Scanner in=new Scanner(System.in);
			System.out.println("enter class name(eg java.lang.String)");
			name=in.next();
		}
		try {
			Class c1=Class.forName(name);
			Class superc1=c1.getSuperclass();
			//getModifiers  返回此类或接口以整数编码的 Java 语言修饰符
			//Modifier 类提供了 static 方法和常量，对类和成员访问修饰符进行解码
			String modifiers=Modifier.toString(c1.getModifiers());
			if(modifiers.length()>0)System.out.println(modifiers+" ");
			System.out.println("class:"+name);
			if(superc1!=null && superc1!=Object.class)
				System.out.println("extends"+superc1.getName());
			System.out.print("\n{\n");
			printConstrutors(c1);
			System.out.println();
			printMethods(c1);
			System.out.println();
			System.out.println("-----");
			printFields(c1);
			System.out.println("-----");
			System.out.println("}");
			
		} catch (Exception e) {
			e.printStackTrace();
		}
		System.exit(0);
	}
```