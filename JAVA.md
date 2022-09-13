# JAVA



## Why Java?

1. Simple
2. Object - Oriented
3. Cross Platform
4. High Performance
5. Distributive App
6. Dynamic
7. Multi-thread
8. Security
9. Robust



## Four Java Versions

1. Java Platform, Enterprise Edition (Java EE)
2. Java Platform, Standard Edition (Java SE)
3. Java Platform, Micro Edition (Java ME)
4. Java FX



## JDK JRE JVM

1. JDK: Java Development Kit
2. JRE: Java Runtime Environment
3. JVM: Java Virtual Machine

![Relationships](https://javabeginnerstutorial.com/wp-content/uploads/2015/07/JDK_JRE_JVM-1.jpg)



## Compiled Language VS Interpreted Language

- Compiled Language(C, C++, Java):
- Interpreted Language(Python, JS)

```java
We generally write a computer program using a high-level language. A high-level language is one that is understandable by us, humans. This is called source code.

However, a computer does not understand high-level language. It only understands the program written in 0's and 1's in binary, called the machine code.

To convert source code into machine code, we use either a compiler or an interpreter.

  Source: https://www.programiz.com/article/difference-compiler-interpreter
```

![Java Compile Process](https://sp-ao.shortpixel.ai/client/to_avif,q_glossy,ret_img,w_839/https://simplesnippets.tech/wp-content/uploads/2018/03/java-execution-flow-diagram.png)

[Java Compiler Process More](https://simplesnippets.tech/execution-process-of-java-program-in-detail-working-of-just-it-time-compiler-jit-in-detail/)



## Data Type

### 	Primary type

1. **byte** (1 byte) (-128 to 127)
2. **short** (2 byte) (-32,768 to 32,767)
3. **int** (4 byte) (-2,147,483,648 to 2,147,483,647)
4. **long** (8 byte) (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)
5. **float** (4 byte) (example int i = 0.1f)
6. **double** (8 byte) (example int i = 0.1)
7. **char** (2 byte)
8. **boolean** (1 byte)

```java
Base:
Binary: 0b
Octal: 0
Hexadecimal: 0x
```

```java
Float is not a good approach to use float for precise values, such as currency.
```

[Unicode]: https://unicode-table.com/en/




### 	Reference Type
			1. Class
			2. Interface
			3. Array



## Casting

	### Widening Casting(**automatic**)

Widening casting is done automatically when passing a smaller size type to a larger size type:

### Narrowing Casting(**manual**)

Narrowing casting must be done manually by placing the type in parentheses in front of the value:

### Priority:

```java
'byte` -> `short` -> `char` -> `int` -> `long` -> `float` -> `double
```

### Char <=> Int

```java
char c = 'a';
int d = c+1;
System.out.println(d); //98
System.out.println((char) d); //b
```



## Types of Variables

1. **Local Variable:** defined within a block or method or constructor is called a local variable.

2. **Instance Vairable:** non-static variables and are declared in a class outside of any method, constructor, or block. 

3. **Static/Class Variable:**  known as class variables

   
### **Differences** between the Instance variables and the Static variables:
| Differences: |
| --- |
| 1, **Each object will have its own copy of an instance variable, whereas we can only have one copy of a static variable per class,** irrespective of how many objects we create. |
| 2, Changes made in an instance variable using one object will not be reflected in other objects as each object has its own copy of the instance variable. In the case of a static variable, changes will be reflected in other objects as static variables are common to all objects of a class. |
| 3, We can access instance variables through object references, and static variables can be accessed directly using the class name. |


Example:


```java
class GFG
{
    // Static variable
    static int a; 
    
    // Instance variable
    int b;        
} 
```

## Operators


| postfix              | `*expr*++ *expr*--`                              |
| -------------------- | ------------------------------------------------ |
| unary                | `++*expr* --*expr* +*expr* -*expr* ~(reverse) !` |
| multiplicative       | `* / %`                                          |
| additive             | `+ -`                                            |
| shift                | `<< >> >>>`                                      |
| relational           | `< > <= >= instanceof`                           |
| equality             | `== !=`                                          |
| bitwise AND          | `&`                                              |
| XOR                  | `^`                                              |
| bitwise inclusive OR | `|`                                              |
| logical AND          | `&&`                                             |
| logical OR           | `||`                                             |
| ternary              | `? :`                                            |
| assignment           | `= += -= *= /= %= &= ^= |= <<= >>= >>>=`         |

```java
Usage of ?:
String type = score<60:"pass":"fail";
```

### Difference between ++i and i++
++i and i++ both increment the value of i by 1 but in a different way. If ++ precedes the variable, it is called pre-increment operator and it comes after a variable, it is called post-increment operator.

```java
int i = 3;
int a = i++; // a = 3, i = 4
int b = ++a; // b = 4, a = 4
```



### Difference between >> and >>>

5: 0000 0000 0000 0000 0000 0000 0000 0101



5>>3： 0000 0000 0000 0000 0000 0000 0000 0000        // (filled with 0)

 -5： 1111 1111 1111 1111 1111 1111 1111 1011
-5>>3 = -1：  1111 1111 1111 1111 1111 1111 1111 1111   // (filled with 1)
-5 >>> 3 = 536870911：  0001 1111 1111 1111 1111 1111 1111 1111   // (filled with 0)

## Package

```java
package pkg1[.pkg2[.pkg3]];
import package1[.package2].(classname|*);
```



## JavaDoc

**Defination:** a tool which comes with JDK and it is used for **generating Java code documentation in HTML format from Java source code** 



Generate commene for methods in Java doc:

```java
enter /**, then press enter
```



## JAVADoc in HTML:

```java
command in terminal:

javadoc -encoding UTF-8 -charset UTF-8 Doc.java
```



### The javadoc Tags

The javadoc tool recognizes the following tags −

|      Tag      |                         Description                          |                        Syntax                        |
| :-----------: | :----------------------------------------------------------: | :--------------------------------------------------: |
|    @author    |                 Adds the author of a class.                  |                  @author name-text                   |
|    {@code}    | Displays text in code font without interpreting the text as HTML markup or nested javadoc tags. |                     {@code text}                     |
|  {@docRoot}   | Represents the relative path to the generated document's root directory from any generated page. |                      {@docRoot}                      |
|  @deprecated  | Adds a comment indicating that this API should no longer be used. |              @deprecated deprecatedtext              |
|  @exception   | Adds a **Throws** subheading to the generated documentation, with the classname and description text. |          @exception class-name description           |
| {@inheritDoc} | Inherits a comment from the **nearest** inheritable class or implementable interface. |  Inherits a comment from the immediate surperclass.  |
|    {@link}    | Inserts an in-line link with the visible text label that points to the documentation for the specified package, class, or member name of a referenced class. |          {@link package.class#member label}          |
| {@linkplain}  | Identical to {@link}, except the link's label is displayed in plain text than code font. |       {@linkplain package.class#member label}        |
|    @param     | Adds a parameter with the specified parameter-name followed by the specified description to the "Parameters" section. |          @param parameter-name description           |
|    @return    |     Adds a "Returns" section with the description text.      |                 @return description                  |
|     @see      | Adds a "See Also" heading with a link or text entry that points to reference. |                    @see reference                    |
|    @serial    |  Used in the doc comment for a default serializable field.   |   @serial field-description \| include \| exclude    |
|  @serialData  | Documents the data written by the writeObject( ) or writeExternal( ) methods. |             @serialData data-description             |
| @serialField  |          Documents an ObjectStreamField component.           | @serialField field-name field-type field-description |
|    @since     | Adds a "Since" heading with the specified since-text to the generated documentation. |                    @since release                    |
|    @throws    |        The @throws and @exception tags are synonyms.         |            @throws class-name description            |
|   {@value}    | When {@value} is used in the doc comment of a static field, it displays the value of that constant. |             {@value package.class#field}             |
|   @version    | Adds a "Version" subheading with the specified version-text to the generated docs when the -version option is used. |                @version version-text                 |





## Scanner

We can use Scanner to get users' inputs.

```java
Scanner s = new Scanner(System.in);
```

By using Scanner's next() and nextLine() to get input strings. Before that, we need to use hasNext()/hasNextLine() to determie whether there is incoming data.



```java
import javax.swing.*;
import java.util.Scanner;

public class Demo1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Use method Next to get input");

        if (scanner.hasNext()) {
            // receive use method next
            String str = scanner.next();
            System.out.println(str);
        }

        // If we don't clos IO class objects, they will continue to use System resource
        scanner.close();
    }
}

```



**Difference between next() and nextLine():**

​	Using `next()` will only return what comes before the delimiter (defaults to whitespace). `nextLine()` automatically moves the scanner down after returning the current line.

we can also use nextInt() nextFloat()...



## Switch

support types:

- bytpe 
- short
- int
- char
- String(JDK 7)

```java
switch (grade) {
  case 'A':
    ...;
    break;
  case 'B':
    ...;
    break;
  ...............;
  default:
    ...;
    // no break for default;
}
```

## Goto:

**break/continue with label:**

```java
label:
for (int i = 0; i < MAX_I; i++) {
    for (int j = 0; j < MAX_J; j++) {
        // do stuff
        break label;
    }
}
```

## Static:

## Overload:

two or more methods may have the same name if they differ in parameters 

- Method Names MUST be SAME
- Parameters MUST be DIFFERENTL (different number of parameters, different types of parameters, or both)
- return type can be same/different
- Just return type diffrent is not enough



## Command Line Arguments in Java

```java
package com.journaldev.examples;

public class CommandLineArguments {

	public static void main(String[] args) {
		System.out.println("Number of Command Line Argument = "+args.length);
		
		for(int i = 0; i< args.length; i++) {
			System.out.println(String.format("Command Line Argument %d is %s", i, args[i]));
		}
	}

}
```

## Varargs: Arbitrary Number of Arguments

There should be only one vararg in a method: it must be the last variable, any other variables should before that variable.

```java
public void myMethod(String... strings) {
    for (String whatever : strings) {
        // do what ever you want
    }

    // the code above is equivalent to
    for (int i = 0; i < strings.length; i++) {
        // classical for. In this case you use strings[i]
    }
}
```

## Array

### Declaration:

```java
datatype[] arr; // prefer
datatype arr[]; // same, but not recommend
```

### Initialization:

```java
datatype[] arr = new datatype[];
```

### get length:

```java
arr.length
```

### 2D Array

```java
int[][] array = {{1,2}, {2,3},{3,4},{4,5}}

```

### Arrays Lib:

```java
import java.util.Arrays;

//command+left lick can show Arryas' code
//click structure on bottom left to see all methods

int i = 1;

// arrary to string
System.out.println(Arrays.toString(i));


// sort array
// sort itself directly
int[] a = {4,3,2,1}''
Arrays.sort(a);

// fill array a with val
Arrays.fill(a, val);

// fill array a from pos1 to pos2 with val
int pos1 = 1;
int pos2 = 3;
Arrays.fill(a, po1, po2, val);
```



##  Memory

stack(栈)

heap(堆)

![stack & heap](/Users/blake/Desktop/java/pictures/stacknheap.png)





## What is object-oriented programming?

OOP organizes software design around data, or objects, rather than functions and logic. An object can be defined as a data field that has unique attributes and behavior.



Main Principles of OOP:

### What are the main principles of OOP?

Object-oriented programming is based on the following principles:

- **Encapsulation**(Private, getter, setter) This principle states that <u>all important information is contained inside an object and only select information is exposed.</u> The implementation and state of each object are privately held inside a defined class. Other objects do not have access to this class or the authority to make changes. They are only able to call a list of public functions or methods. This characteristic of data hiding provides greater program security and avoids unintended data corruption.

  - **high cohesion**, **low Coupling**: 
    - **Defination:**
      - **High cohesion**: Elements within one class/module should functionally belong together and do one particular thing.
      - **Loose coupling**: Among different classes/modules should be minimal dependency.

    - **Benefits**:
      - Hide neccessary details
      - Enhance secutity
      - Unify API
      - Enhace level of maintenance

    - use **Private** key word
    - use **getter/setter**
    - press Control+Return to auto-create getter/setter

- **Abstraction** <u>Objects only reveal internal mechanisms that are relevant for the use of other objects, hiding any unnecessary implementation code.</u> The derived class can have its functionality extended. This concept can help developers more easily make additional changes or additions over time.

  - cannot new an abstract class like new Animal()

  - we can use normal methods in an abstract class

  - abstract methods are in abstract class

  - ```java
    // Abstract class
    abstract class Animal {
      // Abstract method (does not have a body)
      public abstract void animalSound();
      // Regular method
      public void sleep() {
        System.out.println("Zzz");
      }
    }
    
    // Subclass (inherit from Animal)
    class Pig extends Animal {
      public void animalSound() {
        // The body of animalSound() is provided here
        System.out.println("The pig says: wee wee");
      }
    }
    
    class Main {
      public static void main(String[] args) {
        Pig myPig = new Pig(); // Create a Pig object
        myPig.animalSound();
        myPig.sleep();
      }
    }
    
    ```

    

- [**Inheritance**](https://www.techtarget.com/whatis/definition/inheritance)**.**(extends, Object, parents' fields, override, this, super. ) <u>Classes can reuse code from other classes.</u> Relationships and subclasses between objects can be assigned, enabling developers to reuse common logic while still maintaining a unique hierarchy. This property of OOP forces a more thorough data analysis, reduces development time and ensures a higher level of accuracy.

  - **One parent can have many children. But one child can only have one parent**

  - use keyword "**extends**" 

  - press **control+h** to see object structure

  - **super VS this**

    -  "**super**": 
      - parent class 
      - super  invoke parent class's constructor
      - super must be constructor's 1st line
      - super can only exist in children classes' constructors
      - super and this cannot invoke constructor simultaneously 

    - "**this**": current class
    - different
      - this can be used without inheritance
      - super must be used with inheritance
      - super(): constructor for parent class
      - This():  constructor for current class

  - Alt+insert: Override a method

  - Override:

    -  inheritance relationship must exist: child overrides parent **METHODS**
    - parameter list must be the same
    - access modifier can be **bigger** but not **smaller**: public>Protected>Default>private
    - throw exception: can be **smaller** but not **bigger**: ClassNotFoundException-->Exception(bigger)
    - methods for parent and children must be the same

  - Why Override:

    - children do not need all parent classes' functions (Alt+Insert : Override)

  - Difference Between Static and Non-static Methods:

    - Static:

      - Invokation relates to left 

      - ```java
        public static void main(String[] args) {
          A a = new A();
          a.test();
          
          B b = new A();
          b.test();
        }
        
        // static here
        public class A extends B{
          public static void test() {
            System.out.println("A=>test");
          }
        }
        
        // static here
        public class B{
          public static void test() {
            System.out.println("B=>test");
          }
        }
        
        // ouput, AB here
        A=>test
        B=>test
        ```

        

    - Non-static

      - Involation relates to right

      - ```java
        public static void main(String[] args) {
          A a = new A();
          a.test();
          
          B b = new A();
          b.test();
        }
        
        // override here, 
        public class A extends B{
          @Override
          public void test() {
            System.out.println("A=>test");
          }
        }
        
        
        public class B{
          public void test() {
            System.out.println("B=>test");
          }
        }
        
        // ouput, AA here
        A=>test
        A=>test
        ```

      - **FINAL** class can not be inherited. 

- [**Polymorphism**](https://www.techtarget.com/whatis/definition/polymorphism)**.**(parents' reference to children objects, instanceof) <u>Objects are designed to share behaviors and they can take on more than one form.</u> The program will determine which meaning or usage is necessary for each execution of that object from a parent class, reducing the need to duplicate code. A child class is then created, which extends the functionality of the parent class. Polymorphism allows different types of objects to pass through the same interface.

  - Polymorphism is for methods, not variables
  - There's relationship between parent and child. ERROR: ClassCastException
  - Inheritance, need to Override. Parent pointer to child object
  - cannot override:
    1. Static method belongs to class, not instance
    2. final
    3. private

  ```java 
  public class Person {
    public void run() {
      System.out.println("dad");
    }
  } 
  
  public class Student extends Person {
    @Override
    public void run() {
      System.out.println("son");
    }
    
    public void eat() {
       System.out.println("eat");
    }
  } 
  
  public static void main(String[] args) {
    // student can invoke methods of itself or parent class
    Student s1 = new Student();
    // parent (Person) class can point to a child class, but cannot use child class's methods
    Person s2 = new Student();
    
    s2.run();
    s1.run();
    
    // output-> son son
    
    
    // left side determines which methods the object can use. 
    // right side doesn't have big effect
    s2.eat(); // child ovrride 
    //^error
    
    
  ((Student) s2).eat() //this works
  }
  ```

- Check parent-child relationship: "instanceof" keyword

- ```java
  System.out.println(X instance of Y) 
    // XY has no relationship -> ERROR
    // X is Y's Son -> true
    // X is Y's parent -> false
  ```

- ![Casting](/Users/blake/Desktop/java/pictures/casting.png)

- Upcasting:  the [typecasting](https://www.geeksforgeeks.org/type-conversion-java-examples/) **of a child object to a parent object**. Upcasting can be done **implicitly**. Upcasting gives us the flexibility to access the parent class members but it is not possible to access all the child class members using this feature. Instead of all the members, we can access some specified members of the child class. For instance, we can access the overridden methods.

- Downcasting: downcasting means the typecasting of a **parent object to a child object**. **Downcasting cannot be implicit.**

- ```java
  // Java program to demonstrate
  // Upcasting Vs Downcasting
  
  // Parent class
  class Parent {
      String name;
  
      // A method which prints the
      // signature of the parent class
      void method()
      {
          System.out.println("Method from Parent");
      }
  
      void parent()
      {
          System.out.println("parent");
      }
  }
  
  // Child class
  class Child extends Parent {
      String id;
  
      // Overriding the parent method
      // to print the signature of the
      // child class
      @Override void method()
      {
          System.out.println("Method from Child");
      }
  
      void child()
      {
          System.out.println("child");
      }
  }
  
  
  
  // Demo class to see the difference
  // between upcasting and downcasting
  public class Hello {
  
      // Driver code
      public static void main(String[] args)
      {
          // Upcasting:
          Parent p = new Child();
          System.out.println("1============================");
          // use child var: NO
          // use child unique method: NO
          // use child method(override in child): YES
  //        p.id = "upcasting: child id"; // ERROR
  //        p.child(); // ERROR
          p.method();
  
          System.out.println("2============================");
          // Parent:
          // use parent var: YES
          // use parent unique method: YES
          // use parent method(override in child): YES  // use child's override method
          p.name = "upcasting: parent name";
          p.parent();
          p.method();
  
  
  
  
          System.out.println("3============================");
          // Downcasting:
          Parent p1 = new Parent();
  //        Child c = (Child) p1; // ERROR: DOWNCASTING ONLY CAST A REAL CHILD OBJECT TO CHILD CLASS
          Child c = (Child) p;
          
          // use child var:
          // use child unique method:
          // use child method(override in child):
          c.id = "downcasting: child id";
          c.child();
          c.method();
  
          System.out.println("4============================");
          // Parent:
          // use parent var: YES
          // use parent unique method: YES
          // use parent method(override in child): YES  // use child's override method
          p.name = "downcasting: parent name";
          p.parent();
          p.method();
      }
  }
  
  
  ```



## Interface:

an interface is an abstract type that contains a collection of methods and constant variables

- an interface cannot be instantiated 

- define some methods, let different classes implement it

- var: public static final

- method: public abstract

- Implements keyword can implement different interfaces

- difference between implements and extends:

  	- extends is for *extending* a class.
  	
  	- implements is for *implementing* an interface

```java
interface FirstInterface {
  public void myMethod(); // interface method
}

interface SecondInterface {
  public void myOtherMethod(); // interface method
}

// DemoClass "implements" FirstInterface and SecondInterface
class DemoClass implements FirstInterface, SecondInterface {
  public void myMethod() {
    System.out.println("Some text..");
  }
  public void myOtherMethod() {
    System.out.println("Some other text...");
  }
}

class Main {
  public static void main(String[] args) {
    DemoClass myObj = new DemoClass();
    myObj.myMethod();
    myObj.myOtherMethod();
  }
}

```



## Pass by Value/Reference

 **passed by reference**: When a parameter is **passed by reference**, the caller and the callee **use the same variable** for the parameter. If the callee modifies the parameter variable, the effect is visible to the caller's variable.

**passed by value**: When a parameter is **passed by value**, the caller and callee have **two independent variables** with the same value. If the callee modifies the parameter variable, the effect is not visible to the caller.



### Constructor

	1.  same name as class name
	1.   there is no return value

### Effect

	1. use "new" to constuct an object
	1. initialize an object's value

### Care

  		1. after making Parameterized Constructor, if default constructor is needed, we need to make another default constuctor



## Static

### Static Variable:

Classname.staticVar; // OK

Classname.NonstaticVar; // No

Object.staticVar; // OK

Object.staticVar; // OK

```java
private static int age; // static var, mainly used in multi-thread programming
private double score; // non-static var

public static void main() {
  Student s1 = new Student();
  
  System.out.println(Student.age);
  System.out.println(Student.score); // ****** ERROR: not static var
  System.out.println(s1.age);
  System.out.println(s1.score);
  
}
```



### Static Methods 

```java
public class Person {
  // execute order: 1-2-3
  
  // 2
  {
     System.out.println("non-static block");
  }
  
  // 1
  {
     System.out.println("static block");
  }
  
  //3
  public Person() {
  	System.out.println("Constructor");   
  }
  
  public static void main(String[] args) {
    Person person1 = new Person(); // static block -> non-static block-> Constructor 
    System.out.println("========================");
    Person person2 = new Person(); // non-static block-> Constructor 
  }
}
```





### Inner Class

```java
public class Outer {
  private int id = 10;
  public void out(){
    System.out.println("out method");
  }
  
  // if change the following "public class Inner" to "public static class Inner":
  // getID() has ERROR: Static black loads first before id is initialized
  public class Inner {
  	public void out(){
  	  System.out.println("inner method");
	  }
    
    public void getID() {
      System.out.println(id);
    }
  }
}
```



```java
public class Application {
  public static void main(String[] args) {
    Outer outer  = new Outer();
    // ***** way to create an object for inner class
    Outer.Inner inner = outer.new Inner();
    inner.in();
  }
}
```



## Multi class
java can have a lot of classes, but there should be only one Public class

```java
Public class Outer {
  
}

class A {
  public static void main (String[] args) {
    
  }
}
```



## Error an exception

### Error:

- Error are due to **lack of system resource**
- And it is **non-recoverable**
- All error fall into **unchecked exception** category, as it is raised due to **lack of system resources** at runtime
- It is **out of programming scope** as such type of error can’t predicted, may be well planned care can be taken to avoid these kind of Error

### Exception

- Exception are due to **programmatic logic**
- And it is **recoverable**
- Exception are categorized into **checked exception and unchecked exception**



### Difference between error an exception

Error is catactrophic. This is something cannot be handled and processed by the program itself. JVM will terminate this process. 

Generally speaking, exception will be handled by the program . We should try our best to handle this kind of exception



### Difference Between Checked(可检查异常,非运行时异常,编译异常) and Unchecked(不检查,运行时异常) Exceptions in Java

To summarize, the difference between a checked and unchecked exception is:

- A **checked exception** is caught at **compile** time whereas a **runtime/unchecked exception** is, as it states, at runtime.
- A checked exception must be handled either by re-throwing or with a **`try catch` block**, whereas an unchecked isn’t required to be handled.
- A runtime exception is a programming error and is fatal whereas a checked exception is an exception condition within your code’s logic and can be recovered or re-tried from.
- unchecked example: 1/0, classnotfound, nullpointer, unknowntype, indexoutofbound
- checked example: 

![errorException](/Users/blake/Desktop/java/errorException.png)(Resource: https://www.benchresources.net/exception-hierarchy-in-java/)



## Exception Handle:

There are five keywords: **try, catch, finally, throw, throws**

**try, catch, finally, throw:**

```java
int a = 1;
int b = 0;

try() {
  if (b==0) {
    throw new ArithmeticException(); 
  }
} catch() {
  
} catch() {
  
} catch(bigger Throwable) {
  
} finally {
  // default execution
}
```

throws:

```java
public static void writeToFile() throws IOException {
    BufferedWriter bw = new BufferedWriter(new FileWriter("myFile.txt"));
    bw.write("Test");
    bw.close();
}

public static void main(String[] args) {
try {
        writeToFile();
    } catch (IOException ioe) {
        ioe.printStackTrace();
    }
}
```



## Self-defined Exception

```java
public class MyException extends Exception{
  private int detail;
  
  public MyException(int a) {
    this.detail = a;
  }
  
  @Override
  public String toString() {
    return "MyException(" + detail + ")";
  }
}


public class Test() {
  static void test(int a) throws MyException {
    if (a>10) {
      throw new MyException(a);
    }
    System.out.println("Ok");
  }
  
  public static void main(String[] args) {
    try() {
      test(1);
    } catch (MyException e) {
      System.out.println("MyException =>" + e);
    }
  }
}
```



### Additional:

1. Difference between OVERLOAD and OVERRIDE:

   1. `override`: subclass method overrides base class method means:

      1. in different range (in derived class and base class)
      2. the same function name
      3. the same function signature
      4. the return type conforms covariance

      In Java, when you override a method, you could add `@Override` annotation on that method, this will let the compiler to help you check out whether you actually override a method or just mistake or misspell something.

      

   2. `overload`: function overloading means:

      1. the same range (in the same class)
      2. the same function name
      3. different function signature
