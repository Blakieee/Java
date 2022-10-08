

## GUI

Component

- Window
- Dialog(弹窗)
- Panel
- Text window
- list window
- button
- picture
- Listen Event
- Mouse
- Keyboard
- 

### 1 Introduction

Core of GUI: Swing AWT (Interface is ugly)

![ContainerArch](/Users/blake/Desktop/JavaNotes/Java/pictures/ContainerArch.png)

| S.NO | **AWT**                                                      | **Swing**                                                    |
| :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 1.   | Java AWT is an API to develop GUI applications in Java       | Swing is a part of Java Foundation Classes and is used to create various applications. |
| 2.   | The components of Java AWT are heavy weighted.               | The components of Java Swing are light weighted.             |
| 3.   | Java AWT has comparatively less functionality as compared to Swing. | Java Swing has more functionality as compared to AWT.        |
| 4.   | The execution time of AWT is more than Swing.                | The execution time of Swing is less than AWT.                |
| 5.   | The components of Java AWT are platform dependent.           | The components of Java Swing are platform independent.       |
| 6.   | MVC pattern is not supported by AWT.                         | MVC pattern is supported by Swing.                           |
| 7.   | AWT provides comparatively less powerful components.         | Swing provides more powerful components.                     |

(Source: https://www.geeksforgeeks.org/difference-between-awt-and-swing-in-java/)


### 2 AWT

#### 2.1 What is AWT(abstract window tools)? 
1. it includes a lot of classes and API

2. Component: Button, TestArea, Label...

3. Container(for components): 
	- Window
		- Frame
	- Dialog
		- Panel
		- Applet

#### 2.2 Component and Container

##### 1. Frame

```java
		   package com.haochen.module1;
		     
		     import java.awt.*;
		     
		     public class TestFrame {
		     
		         public static void main(String[] args) {
		             // Frame Object
		             Frame frame = new Frame("Frame");
		     
		             frame.setVisible(true);
		     
		             frame.setSize(400, 400);
		     
		             frame.setBackground(Color.BLACK);
		     
		             frame.setLocation(200,200);
		     
		             frame.setResizable(false);
		         }
		     }
		     
```

```java
		     package com.haochen.module1;
		    
		     import java.awt.*;
		     
		     public class TestFrame2 {
		         public static void main(String[] args) {
		             new MyFrame(100, 100, 200, 200, Color.BLUE);
		             new MyFrame(300, 100, 200, 200, Color.BLUE);
		             new MyFrame(100, 300, 200, 200, Color.BLUE);
		             new MyFrame(300, 300, 200, 200, Color.BLUE);
		         }
		     }
		     
		     class MyFrame extends Frame {
		         static int id = 0;
		     
		         public MyFrame(int x, int y, int w, int h, Color color) {
		             super("MyFrame+" + (++id));
		             setBackground(color);
		             setBounds(x,y,w,h);
		             setVisible(true);
		         }
		     }
		     
```


​     
##### 2. Panel
```java
package com.shuai.lesson1;
import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.awt.event.WindowListener;
//Panel 可以看成一个空间，但是不能单独存在，得放在Frame上
public class TsetPanel {
    public static void main(String[] args) {
       //窗口
        Frame frame = new Frame();
        //布局的概念
        //面板
        Panel panel = new Panel();
        /*设置布局  不设置会默认置顶
        未设置Layout时，java默认为flowLayout布局的，
         设置为null即为清空布局管理器，之后添加组件，常常是设置组件左上角坐标相
         对于容器左上角（0，0）的x,y值来确定组件的位置，即使更改容器大小也不会
         改变位置。这种方式常常用于窗体大小固定的容器里。*/
       frame.setLayout(null);
        //坐标
        frame.setBounds(300,300,500,500);
        frame.setBackground(new Color(59, 164, 125));
        //panel 设置坐标，相对于Frame的坐标
        panel.setBounds(50,50,200,200);
        panel.setBackground(new Color(90, 46, 30));
        //frame.add(panel)frame添加面板
        frame.add(panel);//Panel经过三层继承，最终继承了Component
        frame.setVisible(true);
        //监听时间，监听窗口关闭事件   System.exit(0)
        //适配器模式： new 重写的太多了  new其子类 本来new WindowsListener的，但是要重写的实在太多了
        frame.addWindowListener(new WindowAdapter() {
           //窗口点击关闭的时候需要做的事情
            @Override
            public void windowClosing(WindowEvent e) {
                //结束程序
                System.exit(0);
            }
        });
    }
}
```
#### 2.3 Layout Manage
##### 1, Flow Layout:  from left to right

```java
package com.shuai.lesson1;
import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
public class TsetFlowLayout {
    public static void main(String[] args) {
        Frame frame = new Frame();
        //组件-按钮
        Button button1 = new Button("button1");
        Button button2 = new Button("button2");
        Button button3 = new Button("button3");
        //设置为流式布局
        //frame.setLayout(new FlowLayout());默认是中
        //frame.setLayout(new FlowLayout(FlowLayout.LEFT));
        frame.setLayout(new FlowLayout(FlowLayout.RIGHT));
        frame.setSize(200,200);
        frame.setVisible(true);
        frame.add(button1);
        frame.add(button2);
        frame.add(button3);
        frame.addWindowListener(new WindowAdapter() {
            //窗口点击关闭的时候需要做的事情
            @Override
            public void windowClosing(WindowEvent e) {
                //结束程序
                System.exit(0);
            }
        });
    }
}
```



##### 2, BorderLayout: South, North, West, East

```java
package com.shuai.lesson1;
import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
public class TestBorderLayout {
    public static void main(String[] args) {
        Frame frame = new Frame("TestBorderLayout");
        Button east = new Button("East");
        Button west = new Button("West");
        Button south = new Button("South");
        Button north = new Button("North");
        Button center = new Button("Center");
        frame.add(east,BorderLayout.EAST);
        frame.add(west ,BorderLayout.WEST);
        frame.add(south ,BorderLayout.SOUTH);
        frame.add(north ,BorderLayout.NORTH);
        frame.add(center,BorderLayout.CENTER);
        frame.setSize(300,300);
        frame.setVisible(true);
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
               System.exit(0);
            }
        });
    }
}
      
```


​    
##### 3, Grid Layout


 ```java
package com.shuai.lesson1;
import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
public class TestGridLayout {
    public static void main(String[] args) {
        Frame frame = new Frame("TsetGridLayout");
        Button button1 = new Button("button1");
        Button button2 = new Button("button2");
        Button button3 = new Button("button3");
        Button button4 = new Button("button4");
        Button button5 = new Button("button5");
        Button button6 = new Button("button6");
        frame.setLayout(new GridLayout(3,2));
        frame.add(button1);
        frame.add(button2);
        frame.add(button3);
        frame.add(button4);
        frame.add(button5);
        frame.add(button6);
        frame.pack();//让布局变得好看
        frame.setVisible(true);
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
 ```

##### 4, Grid Practise

```java
package com.shuai.lesson1;
import jdk.nashorn.api.tree.NewTree;
import java.awt.*;
import java.io.FileOutputStream;
public class TestLayoutLianxi {
    public static void main(String[] args) {
        Frame frame = new Frame("TestLayoutLianxi");
        frame.setSize(400,300);
        frame.setLocation(300,300);
        frame.setBackground(Color.BLUE);
        frame.setVisible(true);
        frame.setLayout(new GridLayout(2,1));
        Panel panel1 = new Panel(new BorderLayout());
        Panel panel2 = new Panel(new GridLayout(2,1));
        Panel panel3 = new Panel(new BorderLayout());
        Panel panel4 = new Panel(new GridLayout(2,2));
        Button button1 = new Button("BUTTON1");
        Button button2 = new Button("BUTTON2");
        Button button3 = new Button("BUTTON3");
        Button button4 = new Button("BUTTON4");
        Button button5 = new Button("BUTTON5");
        Button button6 = new Button("BUTTON6");
        Button button7 = new Button("BUTTON7");
        Button button8 = new Button("BUTTON8");
        Button button9 = new Button("BUTTON9");
        Button button10 = new Button("BUTTON10");
        panel1.add(button1,BorderLayout.EAST);
        panel1.add(button2,BorderLayout.WEST);
        panel2.add(button3);
        panel2.add(button4);
        panel1.add(panel2,BorderLayout.CENTER);
        panel3.add(button5,BorderLayout.EAST);
        panel3.add(button6,BorderLayout.WEST);
        panel4.add(button7);
        panel4.add(button8);
        panel4.add(button9);
        panel4.add(button10);
        panel3.add(panel4,BorderLayout.CENTER);
        frame.add(panel1);
        frame.add(panel3);
    }
}

```




#### 2.4 Event Listener:

```java
package com.shuai.lesson2;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
public class TestActionEvent {
    public static void main(String[] args) {
        //按下按钮，触发一些事件
        Frame frame = new Frame();
        Button button1 = new Button("button1");
        //因为addActionListener需要ActionListener，因此我们需要构造一个ActionListener
        MyActionListener myActionListener = new MyActionListener();
        button1.addActionListener(new MyActionListener());
        frame.add(button1, BorderLayout.CENTER);
        frame.pack();
        frame.setVisible(true);
        windowsClosing(frame);
    }
    //关闭窗体的事件
    private static void windowsClosing(Frame frame){
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
//事件监听
    static class MyActionListener implements ActionListener {
        @Override
        public void actionPerformed(ActionEvent e) {
            System.out.println("11");
        }
    }
}

```

Mutiples buttons share same listener:

```java
package com.shuai.lesson2;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.FileOutputStream;
public class TestActionEvent2 {
    public static void main(String[] args) {
        //两个按钮，实现同一个监听
        Frame frame = new Frame("1111");
        Button button1 = new Button("start");
        Button button2 = new Button("stop");
        //可以显示的定义出发会返回的命令，如果不显示定义，则会走默认值
        //可以多个按钮只写一个监听类
        button1.setActionCommand("3333");
        My my = new My();
        button1.addActionListener(my);
        button2.addActionListener(my);
        frame.add(button1, BorderLayout.WEST);
        frame.add(button2, BorderLayout.EAST);
        frame.pack();
        frame.setVisible(true);
    }
    static class My implements ActionListener {
        @Override
        public void actionPerformed(ActionEvent e) {
            //e.getActionCommand()获得按钮的信息
            System.out.println("按钮被点击了：msg" + e.getActionCommand());
        }
    }
}
```



#### 2.5 TextField listens TextField

```java
package com.shuai.lesson2;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
public class TestText01 {
    public static void main(String[] args) {
        //启动！只负责启动
        new MyFrame();
}
}
class MyFrame extends Frame{
    public MyFrame(){
        TextField textField = new TextField();
        add(textField);
        //监听这个文本框输入的文字
        //按下回车键，就会触发这个输入框的事件，在下边的重写方法中重写的语句为  获得输入框的文本并打印
        textField.addActionListener(new My());
        //设置替换编码
        textField.setEchoChar('*');
        setVisible(true);
        pack();
    }
}
class My implements ActionListener{
    @Override
    public void actionPerformed(ActionEvent e) {
        TextField text = (TextField) e.getSource();//获得一些资源,返回的一个对象
        System.out.println(text.getText());//获得输入框的文本
        //每次都设置为空 即每次文本框输入完以后，都会全部删除清零
        text.setText("");
    }
}

```

#### 2.6 Calculator

Inner Class Version:

```java
package com.shuai.lesson2;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.TextEvent;
public class TestCALC {
    public static void main(String[] args) {
        new Calculator().loadFrame();
    }
}
//计算器类
//方法
class Calculator extends Frame {
    //属性
    TextField textField;
    TextField textField1;
    TextField textField2;
    //方法
    public void loadFrame() {
        //3个文本框
        textField = new TextField(10);//字符数
        textField1 = new TextField(10);//字符数
        textField2 = new TextField(20);//字符数
        //1 个按钮
        Button button = new Button("=");
        button.addActionListener(new MyAL());
        //1个标签
        Label label = new Label("+");
        setLayout(new FlowLayout());
        add(textField);
        add(label);
        add(textField1);
        add(button);
        add(textField2);
        pack();
        setVisible(true);
    }
      private   class MyAL implements ActionListener {
            @Override
            public void actionPerformed(ActionEvent e) {
                //1.获得加数和被加数
                //2.将这个值加法运算后，放到第三个框
                //3.清除前两个框
                int text = Integer.parseInt(textField.getText());
                int text1 = Integer.parseInt(textField1.getText());
                textField2.setText("" + (text1 + text));
                textField.setText("");
                textField.setText("");
            }
    }

```

#### 2.7 Paint

```java
package com.hong.gUI.awt_;
import java.awt.*;
/**
 * 画笔
 */
public class Paint_ {
    public static void main(String[] args) {
        new MyPaint().loadFrame();
    }
}
class MyPaint extends Frame{
    public void loadFrame(){
        setTitle("Paint");
        setBounds(200,200,600,500);
        setVisible(true);
    }
    //画笔方法 paint创建窗口后，默认只执行一次
    @Override
    public void paint(Graphics g) {
        //设置画笔颜色
        g.setColor(Color.red);
        g.drawOval(100,100,100,100);
        g.fillOval(50,50,100,100);
        g.setColor(Color.GREEN);
        g.fillRect(150,200,100,100);
        //养成习惯，画笔用完，将它还原成最初的颜色
        g.setColor(Color.BLACK);
    }
}
```



#### 2.8 Mouse Listener

```java
package com.hong.gUI.awt_.listener_;
import java.awt.*;
import java.awt.event.MouseAdapter;
import java.awt.event.MouseEvent;
import java.util.ArrayList;
import java.util.Iterator;
/**
 * 鼠标监听事件
 */
public class MouseListener_ {
    public static void main(String[] args) {
        new MyFrame("画图--鼠标监听事件");
    }
}
//窗口类，主类
class MyFrame extends Frame{
    //画画需要画笔，需要监听鼠标当前的位置，需要一个集合来存储这个点(X,Y)坐标
    ArrayList<Point> points;
    public MyFrame(String title){
        super(title);
        setBounds(50,400,500,600);
        setVisible(true);
        points=new ArrayList();
        //鼠标监听器，正对这个窗口
        this.addMouseListener(new MyMouseListener());
    }
    @Override
    public void paint(Graphics g) {
        //画画，遍历集合，打印这个点
        Iterator<Point> iterator = points.iterator();//利用迭代器遍历
        while (iterator.hasNext()){
            Point point=iterator.next();
            g.setColor(Color.PINK);
            g.fillOval(point.x,point.y,10,10);
        }
    }
    //适配器模式
    private class MyMouseListener extends MouseAdapter{
        //鼠标监听事件：按下   弹起    按住不放
        @Override
        public void mousePressed(MouseEvent e) {
            //鼠标按下时，运行这个方法
            MyFrame frame=(MyFrame) e.getSource();
            //当我们点击的时候，就会在界面上产生一个点！画
            //这个点就是鼠标的坐标
            points.add(frame.getMousePosition());//等于(e.getPoint())和(new Point(e.getX(),e.getY()))
            //因为paint方法只会自动调用一次，所以通过repaint刷新后重新调用paint方法
            //每次点击鼠标都需要重新画一次
            repaint();//先刷新（清空）窗口，如何再调用paint
        }
    }
}
```

#### 2.9 Window Listener

```java
package com.hong.gUI.awt_.listener_;
import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
/**
 * Windowlistener 窗口监听事件
 */
public class WindowTest_ {
    public static void main(String[] args) {
        new WindowFrame("WindowListener");
    }
}
class WindowFrame extends Frame {
    public WindowFrame(String title) {
        super(title);
        setBounds(100,100,200,200);
        setBackground(Color.pink);
        setVisible(true);
//        addWindowListener(new MyWindowLister());
        this.addWindowListener(
                //匿名内部类
            new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                //当你点击关闭窗口按钮时就会执行该事件，在这里不设置System.exit(0)就不会关闭
                System.out.println("windowClosing");
                //System.exit(0);
            }
            @Override
            public void windowClosed(WindowEvent e) {
                //窗口关闭后，再运行的事件,一般不常用
                System.out.println("windowClosed");
            }
            @Override
            public void windowActivated(WindowEvent e) {
                //窗口激活事件：也就是当你点击到这个窗口内时，就是窗口激活了
                //鼠标点击窗口外的地方（窗口变灰了），也就是离开了窗口
                WindowFrame source =(WindowFrame) e.getSource();
                source.setTitle("被再次激活了");
                System.out.println("windowActivated");
            }
        });
    }
/*
    class MyWindowLister extends WindowAdapter{
        @Override
        public void windowClosing(WindowEvent e) {
            //当按下关闭按钮后，就会执行这个方法
            setVisible(false);//将窗口隐藏
            try {
                Thread.sleep(1000);
            } catch (InterruptedException interruptedException) {
                interruptedException.printStackTrace();
            }
            System.exit(0);//正常退出(0)
        }
    }*/
}
```

#### 2.10 Keyboard Listener

```java
package com.hong.gUI.awt_.listener_;
import java.awt.*;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
/**
 * 键盘监听事件
 */
public class KeyListener_ {
    public static void main(String[] args) {
        new KeyFrame("KeyListener");
    }
}
//键
class KeyFrame extends Frame{
    public KeyFrame(String title) {
        super(title);
        setBounds(10,10,300,500);
        setVisible(true);
        //在这个窗口监听键盘事件
        this.addKeyListener(new KeyAdapter() {
            @Override
            public void keyPressed(KeyEvent e) {//键盘按下
                int keyCode=e.getKeyCode();
                //获得键盘下的键是哪一个，当前的码
                System.out.println(keyCode+":"+(char)keyCode);
                //不需要去记录这个数值，直接使用静态属性 KeyEvent.VK_XXX
                if (keyCode==KeyEvent.VK_UP){
                    System.out.println("你按下了上键");
                }
            }
        });
    }
}
```

### 3 Swing



#### 3.1 Window,Panel

```java
package com.hong.gUI.swing_;
import javax.swing.*;
import java.awt.*;
/**
 * JFrame窗口
 * 在顶层容器（窗口）下直接添加非Swing的重组件是没有用的，必须要放到一个容器内，才可添加
 * 与AWT组件不同，Swing组件不能直接添加到顶层容器中，它必须添加到一个与Swing顶层容器相关联的内容面板（content pane）上，
 * 内容面板是一个顶层容器包含的一个普通容器，它是一个轻量级组件。
 * 基本规则：把Swing组件放入一个顶层Swing容器的内容面板上，避免使用非Swing的重量级组件
 */
public class JFrame_1 {
    //init()  初始化方法  Applet与这个有关
    public void init(){
        //顶级窗口
        JFrame jFrame = new JFrame("JFrame");
        jFrame.setVisible(true);
        jFrame.setBounds(100,400,300,300);
        jFrame.setBackground(Color.BLUE);//在顶层容器下，需要一个与顶层容器相关的内容面板来设置面板颜色
        //设置一个标签  设置文字
        JLabel jLabel = new JLabel("欢迎来到java-JFrame窗口",SwingConstants.CENTER);//后面参数是设置为居中显示
        jFrame.add(jLabel,BorderLayout.NORTH);
        jLabel.setBackground(Color.BLUE);
        //设置一个按钮
        JButton button = new JButton("button");
        button.setBackground(Color.cyan);
        jFrame.add(button,BorderLayout.CENTER);
        //关闭事件  不设置可以点击关闭按钮，但是程序不结束，窗口只是隐藏了
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);//3==JFrame.EXIT_ON_CLOSE==WindowConstants.EXIT_ON_CLOSE
    }
    public static void main(String[] args) {
        //建立一个窗口
        new JFrame_1().init();
    }
}

```



#### 3.2 Dialog

```java
package com.lijin.demo02;
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
//弹窗
public class TestDialog {
    public static void main(String[] args) {
        new Dialog1();
    }
}
//主窗口
class Dialog1 extends JFrame{
    public Dialog1(){
        this.setVisible(true);
        this.setBounds(100,100,300,300);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        //Jframe放东西，容器
        Container container = this.getContentPane();
        //绝对布局
        container.setLayout(null);
        //按钮
        JButton jButton = new JButton("弹出对话框");//创建
        jButton.setBounds(30,30,200,50);
        container.add(jButton);
        //点击这个按钮的时候，弹出一个弹窗（监听事件）
        jButton.addActionListener(new AbstractAction() {  //监听器
            @Override
            public void actionPerformed(ActionEvent e) {
                //弹窗
                new Dialog2();
            }
        });
        container.add(jButton);
    }
}
//弹窗的窗口
class Dialog2 extends JDialog{
    public Dialog2(){
        this.setVisible(true);
        this.setBounds(100,100,500,500);
        //弹窗中默认有此事件
        //this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        Container container = this.getContentPane();
        container.setLayout(null);
        container.add(new Label("label test"));
    }
}

```



#### 3.3 Label

```java
package com.lijin.demo03;
import javax.swing.*;
import java.awt.*;
//图标
public class TestIcon {
    public static void main(String[] args) {
        new Icon1(100,100).init();
    }
}
class Icon1 extends JFrame implements Icon{
    //属性
    private int width;
    private int high;
    public Icon1(){}//无参构造
    public Icon1(int width,int high){
        this.width = width;
        this.high = high;
    }
    //方法
    public void init(){
        setBounds(100,100,300,300);
        Icon1 icon1 = new Icon1(15,15);
        //图标放在标签上，也可以放在按钮上
        JLabel jLabel = new JLabel("label test",icon1,SwingConstants.CENTER);
        Container container = getContentPane();
        container.add(jLabel);
        this.setVisible(true);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    @Override
    public void paintIcon(Component c, Graphics g, int x, int y) {
        g.fillOval(x,y,width,high);
    }
    @Override
    public int getIconWidth() {
        return this.width;
    }
    @Override
    public int getIconHeight() {
        return this.high;
    }
}

```



#### 3.4 Panel

```java
package com.lijin.demo04;
import javax.swing.*;
import java.awt.*;
public class TestJPane extends JFrame {
    public TestJPane()  {
        Container container = this.getContentPane();
        container.setLayout(new GridLayout(2,1,10,10));  //间距
        JPanel jPanel = new JPanel(new GridLayout(1,3));
        JPanel jPanel1 = new JPanel(new GridLayout(1,3));
        JPanel jPanel2 = new JPanel(new GridLayout(1,3));
        JPanel jPanel3 = new JPanel(new GridLayout(1,3));
        jPanel.add(new JButton("1"));
        jPanel.add(new JButton("2"));
        jPanel.add(new JButton("3"));
        jPanel1.add(new JButton("1"));
        jPanel1.add(new JButton("2"));
        jPanel1.add(new JButton("3"));
        jPanel2.add(new JButton("1"));
        jPanel2.add(new JButton("2"));
        jPanel2.add(new JButton("3"));
        jPanel3.add(new JButton("1"));
        jPanel3.add(new JButton("2"));
        jPanel3.add(new JButton("3"));
        container.add(jPanel);
        container.add(jPanel1);
        container.add(jPanel2);
        container.add(jPanel3);
        setVisible(true);
        setBounds(100,100,300,300);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new TestJPane();
    }
}

```



##### JScrollPanel

```java
package com.lijin.demo03;
import javax.swing.*;
import java.awt.*;
import java.net.URL;
public class TestImageIcon extends JFrame {
    public static void main(String[] args) {
        new TestImageIcon();
    }
    public TestImageIcon()  {
        //获取图片地址     url是一个具体的地址
        JLabel jLabel = new JLabel("ImageIcon");
        URL url = TestImageIcon.class.getResource("1.jpg");//获取当前类下的资源
        ImageIcon imageIcon = new ImageIcon(url);//命名避免冲突
        jLabel.setIcon(imageIcon);//图片饭在jLabel上
        jLabel.setHorizontalAlignment(SwingConstants.CENTER);
        Container container = getContentPane();
        container.add(jLabel);
        setVisible(true);
        setBounds(100,100,300,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
}

```



#### 3.5 Button

```java
package com.lijin.demo05;
import com.lijin.demo03.TestImageIcon;
import javax.swing.*;
import java.awt.*;
import java.net.URL;
//按钮
public class TestJButton extends JFrame {
    public TestJButton() {
        Container container = this.getContentPane();
        //将图片变为一个图标
        URL url = TestJButton.class.getResource("1.jpg");
        ImageIcon icon = new ImageIcon(url);
        //把图片放在按钮上
        JButton jButton = new JButton();
        jButton.setIcon(icon);
        jButton.setToolTipText("图片按钮");
        container.add(jButton);
        setVisible(true);
        setBounds(100,100,300,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new TestJButton();
    }
}
```

Single Choice



```java
package com.lijin.demo05;
import javax.swing.*;
import java.awt.*;
import java.net.URL;
//多选
public class TestJButton1 extends JFrame {
    public TestJButton1() {
        Container container = this.getContentPane();
        //单选框
        JRadioButton jRadioButton1 = new JRadioButton("1");
        JRadioButton jRadioButton2 = new JRadioButton("2");
        JRadioButton jRadioButton3 = new JRadioButton("3");
        //由于单选框只能选一个所以我们要分组，一个组中只能选一个
        ButtonGroup group = new ButtonGroup();
        group.add(jRadioButton1);
        group.add(jRadioButton2);
        group.add(jRadioButton3);
        container.add(jRadioButton1,BorderLayout.CENTER);
        container.add(jRadioButton2,BorderLayout.NORTH);
        container.add(jRadioButton3,BorderLayout.SOUTH);
        setVisible(true);
        setBounds(100,100,300,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new TestJButton1();
    }
}
```



multi choice

```java
package com.lijin.demo05;
import javax.swing.*;
import java.awt.*;
//多选框
public class TestJButton2 extends JFrame {
    public TestJButton2() {
        Container container = this.getContentPane();
        JCheckBox jCheckBox = new JCheckBox("1");
        JCheckBox jCheckBox1 = new JCheckBox("2");
        container.add(jCheckBox,BorderLayout.SOUTH);
        container.add(jCheckBox1,BorderLayout.NORTH);
        setVisible(true);
        setBounds(100,100,300,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new TestJButton2();
    }
}
```



#### 3.6 Menu

##### Drop Down menu

```java
package com.lijin.demo06;
import javax.swing.*;
import java.awt.*;
//下拉框
public class TestJCombobox extends JFrame {
    public TestJCombobox() {
        Container container = this.getContentPane();
        JComboBox jComboBox = new JComboBox();
        jComboBox.addItem(null);
        jComboBox.addItem("正在上映");
        jComboBox.addItem("已下架");
        jComboBox.addItem("即将上映");
        container.add(jComboBox);
        this.setBounds(100,100,300,300);
        this.setBackground(Color.CYAN);
        setVisible(true);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new TestJCombobox();
    }
}
```

##### List

```java
package com.lijin.demo06;
import javax.swing.*;
import java.awt.*;
//列表框
public class TestJCombobox1 extends JFrame {
    public TestJCombobox1() {
        Container container = this.getContentPane();
        //生成列表内容
        String[] contents = {"1","2","3"};
        //列表需要放入内容
        JList jList = new JList(contents);
        container.add(jList);
        setVisible(true);
        setBounds(100,100,300,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new TestJCombobox1();
    }
}
```

#### 3.7 TextField

Textfield

```java
package com.lijin.demo06;
import javax.swing.*;
import java.awt.*;
//文本框
public class TestText1 extends JFrame {
    public TestText1() {
        Container container = getContentPane();
        JTextField jTextField = new JTextField("yuyan");
        JTextField jTextField1 = new JTextField("lijin",20);
        //布局
        container.add(jTextField,BorderLayout.NORTH);
        container.add(jTextField1,BorderLayout.SOUTH);
        setVisible(true);
        setBounds(100,100,300,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new TestText1();
    }
}
```



Passwordfield

```java
package com.lijin.demo06;
import javax.swing.*;
import java.awt.*;
//密码框
public class TestText2 extends JFrame {
    public TestText2() {
        Container container = getContentPane();
        JPasswordField jPasswordField = new JPasswordField();   //有默认值，但也可以设置
        //jPasswordField.setEchoChar('+');
        container.add(jPasswordField);
        setVisible(true);
        setBounds(100,100,300,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new TestText2();
    }
}
```



### 4, Snake

Frame

keyboard listener

timer







### Questions:

#### 1, Frame and Panel Diff?

- Panel is an internal region to a frame or another panel that helps to group multiple components together 
- a Frame is a resizable, movable independent window with a title bar which contains all other components.

https://blog.csdn.net/weixin_38719347/article/details/72794404









