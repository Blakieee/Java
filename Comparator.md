## DIfference Between comapre and compareTo:


如果需要进行排序，可结合compareTo() 和 compare() 方法。

> ==compareTo()==:  对象须实现 ==Comparable== 接口 （必须有可比性）

> ==compare()== : ==Comparator== 接口中定义的方法，具体实现时可调用compareTo() 方法。

**二者返回值类似，0 表示相同，负数表示排在前，正数表示排在后。**

都是排序，有什么特别的区别吗？

> compareTo(): Java 称之为Lexicographically 排序，以String对象为例，从源码可看到，比较的是某一index上的字符的Unicode编码值。
- 每个index上的字符都相同且字符串长度相等，返回 0
- 某个index上的字符没有对应的另一字符串Index，返回 字符串长度差值
- 某个index上的字符有对应Index但是Unicode值不同，返回二者Unicode值的差值

很明显, ==compareTo() 使用比较局限==，适合作为low level的底层调用。

> ==compare() 则可更灵活==，比如按照产品的销售区域，价格，销量等多种方式来排序，则可在类中重写compare()方法，或使用匿名类实现该方法，便于以后的sort方法。



## Example


```java
import java.util.*;

class Dog implements Comparator<Dog>, Comparable<Dog> {
   private String name;
   private int age;
   Dog() {
   }

   Dog(String n, int a) {
      name = n;
      age = a;
   }

   public String getDogName() {
      return name;
   }

   public int getDogAge() {
      return age;
   }

   // Overriding the compareTo method
   public int compareTo(Dog d) {
      return (this.name).compareTo(d.name);
   }

   // Overriding the compare method to sort the age 
   public int compare(Dog d, Dog d1) {
      return d.age - d1.age;
   }
}

public class Example {

   public static void main(String args[]) {
      // Takes a list o Dog objects
      List<Dog> list = new ArrayList<Dog>();

      list.add(new Dog("Shaggy", 3));
      list.add(new Dog("Lacy", 2));
      list.add(new Dog("Roger", 10));
      list.add(new Dog("Tommy", 4));
      list.add(new Dog("Tammy", 1));

```



```java
	  Collections.sort(list);   // Sorts the array list

      for(Dog a: list)   // printing the sorted list of names
         System.out.print(a.getDogName() + ", ");
```



```java
	// Sorts the array list using comparator
      Collections.sort(list, new Dog());
      System.out.println(" ");
      
      for(Dog a: list)   // printing the sorted list of ages
         System.out.print(a.getDogName() +"  : "+ a.getDogAge() + ", ");
   }
}
```





Output:

```java
Lacy, Roger, Shaggy, Tammy, Tommy,
Tammy  : 1, Lacy  : 2, Shaggy  : 3, Tommy  : 4, Roger  : 10,
```