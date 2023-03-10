# 第二章 Java基本语法

## 2.1 关键字和保留字

### 关键字(keyword)的定义和特点

- 定义：被Java语言赋予了特殊含义，用做专门用途的字符串（单词）
- 特点：关键字中所有字母都为小写
- 官方地址： https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html

![keyword1](./Figures/keyword1.png)

![keyword2](./Figures/keyword2.png)

### 保留字(reserved word)

Java保留字：现有Java版本尚未使用，但以后版本可能会作为关键字使用。自己命名标识符时要避免使用这些保留字 goto 、const。

## 2.2 标识符(Identifier)

### 标识符：

- Java 对各种**变量**、**方法**和**类**等要素命名时使用的字符序列称为标识符
- 技巧：凡是自己可以起名字的地方都叫标识符。

### 定义合法标识符规则：

- 由26个英文字母大小写，0-9 ，_或 $ 组成
- 数字不可以开头。
- 不可以使用关键字和保留字，但能包含关键字和保留字。
- Java中严格区分大小写，长度无限制。
- 标识符不能包含空格。

### Java中的名称命名规范

- 包名：多单词组成时所有字母都小写：xxxyyyzzz
- 类名、接口名：多单词组成时，所有单词的首字母大写：XxxYyyZzz
- 变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz
- 常量名：所有字母都大写。多单词时每个单词用下划线连接：XXX_YYY_ZZZ
- 注意1：在起名字时，为了提高阅读性，要尽量有意义，“见名知意”。
- 注意2：Java采用Unicode字符集，因此标识符也可以使用汉字声明，但是不建议使用。

## 2.3 变量

### 变量的概念

<img src="./Figures/var_basic.png" alt="变量" style="zoom:80%;" />

- 内存中的一个存储区域
- 该区域的数据可以在同一类型范围内不断变化
- 变量是程序中最基本的存储单元。包含**变量类型**、**变量名**和存储的值

### 变量的作用

用于在内存中保存数据

### 使用变量注意

- Java中每个变量必须先声明，后使用
- 使用变量名来访问这块区域的数据
- 变量的作用域：其定义所在的一对{ }内
- 变量只有在其作用域内才有效
- 同一个作用域内，不能定义重名的变量

### 声明变量

语法：<数据类型> <变量名称>
例如：int var;

### 变量的赋值

语法：<变量名称> = <值>
例如：var = 10;

### 声明和赋值变量

语法： <数据类型> <变量名> = <初始化值>
例如：int var = 10;

### 变量的分类-按数据类型

![变量的分类-按数据类型](./Figures/var_type1.png)

### 变量的分类-按声明的位置的不同

- 在方法体外，类体内声明的变量称为成员变量。
- 在方法体内部声明的变量称为局部变量。
- 注意：二者在初始化值方面的异同：
  同：都有生命周期
  异：局部变量除形参外，需显式初始化。

![变量的分类-按声明的位置的不同](./Figures/var_type2.png)

### 基本数据类型

#### 整型 byte、short、int、long

**声明long型变量，必须以"l"或"L"结尾。**

| 类型  | 占用存储空间    | 表数范围                 |
| ----- | --------------- | ------------------------ |
| byte  | 1字节=8位(bite) | -128 ~ 127                |
| long  | 8字节           | $-2^{63}$ ~ $2^{63} - 1$ |
| short | 2字节           | $-2^{15}$ ~ $2^{15} - 1$ |
| int   | 4字节           | $-2^{31}$ ~ $2^{31} - 1$ |

```java
class VariableTest1 {
    public static void main(String[] args) {
        // 1. 整型：byte(1byte=8bit), short(2byte), int(4byte), long(8byte)
        // 1.1 byte范围：-128 ~ 127
        byte b1 = 12;
        byte b2 = -128;
        System.out.println(b1);
        System.out.println(b2);
        // 1.2 声明long型变量，必须以"l"或"L"结尾
        short s1 = 128;
        int i1 = 1264;
        long l1 = 3414234324l;
        System.out.println(s1);
        System.out.println(i1);
        System.out.println(l1);
    }
}
```

#### 浮点类型 float、double

- 浮点型常量有两种表示形式：

  十进制数形式：如：5.12、512.0f、.512 (必须有小数点）

  科学计数法形式：如：5.12e2、512E2、100E-2

- float：单精度，尾数可以精确到7位有效数字。很多情况下，精度很难满足需求。

- double：双精度，精度是float的两倍。通常采用此类型。

- **Java 的浮点型常量默认为double型，声明float型常量，须后加‘f’或‘F’。**

| 类型   | 占用存储空间 | 表数范围               |
| ------ | ------------ | ---------------------- |
| float  | 4字节        | -3.0403E38 ~ 3.0403E38 |
| double | 8字节        | -1.789E308 ~ 1.789E308 |

```java
class VariableTest1 {
    public static void main(String[] args) {
        // 2. 浮点型：float(4字节), double(8字节)
        // float 表示数值的范围比long大
        double d1 = 123.3;
        System.out.println(d1 + 1);

        float f1 = 12.3f;
        System.out.println(f1);
        // 通常，定义浮点类型变量时，使用double型
    }
}
```

#### 字符类型 char

- char 型数据用来表示通常意义上“字符”(2字节)
- Java中的所有字符都使用Unicode编码，故一个字符可以存储一个字母，一个汉字，或其他书面语的一个字符。
- 字符型变量的三种表现形式：
  字符常量是用**单引号**(‘ ’)括起来的单个字符。例如：char c1 = 'a'; char c2= '中'; char c3 = '9';
   Java中还允许使用**转义字符**‘\’来将其后的字符转变为特殊字符型常量。例如：char c3 = ‘\n’; // '\n'表示换行符
  直接使用 **Unicode** 值来表示字符型常量：‘\uXXXX’。其中，XXXX代表一个十六进制整数。如：\u000a 表示 \n。
- char类型是可以进行运算的。因为它都对应有Unicode码。

```java
class VariableTest1 {
    public static void main(String[] args) {
        // 3. 字符型：char(2字节)
        // 定义char型变量，通常使用一对''
        char c1 = 'a';
        c1 = 'A';
        System.out.println(c1);

        char c2 = '1';
        char c3 = '中';
        System.out.println(c2);
        System.out.println(c3);
        /*表示方式：
         3.1 声明一个字符 
         3.2 转义字符
         3.3 直接使用 Unicode 值来表示字符型常量
         */
        char c4 = '\n';
        c4 = '\t';
        System.out.print("Hello" + c4);
        System.out.println("world");

        char c6 = '\u0043';
        System.out.println(c6);
    }
}
```

#### 布尔类型 boolean

- boolean 类型用来判断逻辑条件，一般用于程序流程控制：
   if条件控制语句；
   while循环控制语句；
   do-while循环控制语句；
   for循环控制语句；
- boolean类型数据只允许取值true和false，无null。
   不可以使用0或非 0 的整数替代false和true，这点和C语言不同。

Java虚拟机中没有任何供boolean值专用的字节码指令，Java语言表达所操作的boolean值，在编译之后都使用java虚拟机中的int数据类型来代替：true用1表示，false用0表示。———《java虚拟机规范 8版》

```java
class VariableTest1 {
    public static void main(String[] args) {
        // 4. 布尔类型: boolean
        // 只能取两个值: true、false
        boolean bb1 = true;
        System.out.println(bb1);

        boolean isMarried = false;
        if(isMarried) {
            System.out.println("你就不能参加单身party了！");
        } else {
            System.out.println("你可以参加单身party！");
        }
    }
}
```

#### 基本数据类型与String间转换

 基本数据类型之间的运算规则（7种，不包括boolean）

##### 自动类型提升

容量小的类型自动转换为容量大的数据类型。
		byte、char、short --> int --> long --> float --> double
当byte、char、short做运算时，结果为int类型

```java
class VariableTest2 {
    public static void main(String[] args) {
        byte b1 = 2;
        int i1 = 12;
        int i2 = b1 + i1;
        System.out.println(i2); // 14

        float f = b1 + i1;
        System.out.println(f); // 14.0

        short s1 = 123;
        double d1 = s1;
        System.out.println(d1); // 123.0

        //***************特别地**************
        // byte、char、short做运算时，结果为int类型
        char c1 = 'a';
        int i3 = 10;
        int i4 = c1 + i3;
        System.out.println(i4); // 107

        short s2 = 10;
        // char s3 = c1 + s2; // 编译不通过

        byte b2 = 10;
        // char c3 = c1 + b2; // 编译不通过

        // short s4 = b1 + b2; // 编译不通过
    }
}
```

##### 强制类型转换

 强制类型转换：自动类型提升运算的逆运算

- 需要使用强转符：()

- 注意：强制类型转换，可能导致精度损失

```java
class VariableTest3 {
    public static void main(String[] args) {
        // 精度损失示例1
        double d1 = 12.9;
        int i1 = (int)d1; // 截断
        System.out.println(i1); // 12

        // 没有精度损失
        long l1 = 123;
        short s1 = (short)l1;
        System.out.println(s1); // 123

        // 精度损失示例2
        int i2 = 128;
        byte b = (byte)i2;
        System.out.println(b); // -128
    }
}
```

##### 两种编码情况

```java
class VariableTest4 {
    public static void main(String[] args) {
        // 1. 编码情况 1
        long l = 123123;
        System.out.println(l);

        // long l1 = 215656565565656; // 编译失败：过大的整数
        long l1 = 215656565565656l;

        //******************************
        float f1 = 12.3; // 编译失败

        // 2. 编码情况 2
        byte b = 12;
        // byte b1 = b + 1; // 编译失败：默认 int 型
        // float f2 = b + 12.3; 编译失败：默认 double 型
    }
}
```

### 字符串类型 String

- String不是基本数据类型，属于引用数据类型

- 声明String类型变量时，使用一对""

- String可以和8种基本数据类型变量做运算，且运算只能是连接运算：+，运算的结果仍然是String类型

```java
class VariableTest5 {
    public static void main(String[] args) {
        String s1 = "Hello world!";
        System.out.println(s1);

        String s2 = "a";
        String s3 = "";

        // char c = ''; // 编译不通过

        //**************************
        int number = 1001;
        String numberStr = "学号";
        String info = numberStr + number;
        boolean b1 = true;
        String info1 = info + b1;
        System.out.println(info1);

        // 练习1
        char c = 'a';
        int num = 10;
        String str = "hello";
        System.out.println(c + num + str);   // 107hello
        System.out.println(c + str + num);   // ahello10
        System.out.println(c + (num + str)); // a10hello
        System.out.println((c + num) + str); // 107hello
        System.out.println(str + num + c);   // hello10a

        // 练习2
        // * *
        System.out.println("*\t*");
        
        String s4 = 123 + "";
        int num1 = Integer.parseInt(s4);
        System.out.println(num1); // 123
    }
}
```

### 进制与进制间的转换



## 2.4 运算符

运算符是一种特殊的符号，用以表示数据的运算、赋值和比较等。

- 算术运算符
- 赋值运算符
- 比较运算符（关系运算符）
- 逻辑运算符
- 位运算符
- 三元运算符

### 算术运算符

*+ - + - \* / % (前)++ (后)++ (前)-- (后)-- +*

```java
public class Aritest {
    public static void main(String[] args) {
        // 除号：/
        int num1 = 12;
        int num2 = 5;
        int result1 = num1 / num2;
        System.out.println(result1); // 2

        int result2 = num1 / num2 * num2;
        System.out.println(result2); // 10

        double result3 = num1 / num2;
        System.out.println(result3); // 2.0

        double result4 = num1 / num2 + 0.0; // 2.0
        System.out.println(result4);
        double result5 = num1 / (num2 + 0.0); // 2.4
        double result6 = (double)num1 / num2; // 2.4
        System.out.println(result5);
        System.out.println(result6);

        // 取余：%
        // 结果的符号与被模数的符号相同
        // 开发中，经常使用 % 判断是否能被除尽
        int m1 = 12;
        int n1 = 5;
        System.out.println("m1 % n1 = " + m1 % n1); // 2
        
        int m2 = -12;
        int n2 = 5;
        System.out.println("m2 % n2 = " + m2 % n2); // -2
        
        int m3 = 12;
        int n3 = -5;
        System.out.println("m3 % n3 = " + m3 % n3); // 2
        
        int m4 = -12;
        int n4 = -5;
        System.out.println("m4 % n4 = " + m4 % n4); // -2

        // (前)++：先自增 1，后运算
        // (后)++：先运算，后自增 1
        int a1 = 10;
        int b1 = ++a1;
        System.out.println("a1 = " + a1 + ", b1 = " + b1); // 11, 11

        int a2 = 10;
        int b2 = a2++;
        System.out.println("a2 = " + a2 + ", b2 = " + b2); // 11, 10
        
        // 注意：
        short s1 = 10;
        // s1 = s1 + 1; // 编译失败
        // s1 = (short)(s1 + 1); // 编译成功
        s1++; // 自增 1，不会改变变量本身的数据类型
        System.out.println(s1);

        // 问题：
        byte bb1 = 127;
        bb1++;
        System.out.println("bb1 = " + bb1); // -128

        // (前)--：先自减 1，后运算
        // (后)--：先运算，后自减 1
        int a4 = 10;
        int b4 = --a4;
        System.out.println("a4 = " + a4 + ", b4 = " + b4); // 9, 9

        int a5 = 10;
        int b5 = a5--;
        System.out.println("a5 = " + a5 + ", b5 = " + b5); // 9, 10
    }
}
```

### 赋值运算符

*= += -= \*= /= %=*

```java
public class SetValueTest {
    public static void main(String[] args) {
        // =
        int i1 = 10;
        int j1 = 10;

        int i2, j2;
        i2 = j2 = 10;

        int i3 = 10, j3 = 20;

        // ********************************
        int num1 = 10;
        num1 += 2;
        System.out.println(num1);

        int num2 = 12;
        num2 %= 5;
        System.out.println(num2);

        short s1 = 10;
        // s1 = s1 + 2; // 编译失败
        s1 += 2; // 不会改变变量本身的数据类型
        System.out.println(s1);

        // 开发中，如果希望变量实现 +2 的操作，有几种方法？（前提：int num = 10;）
        // 方式一：num = num + 2;
        // 方式二：num += 2; (推荐)

        // 开发中，如果希望变量实现 +1 的操作，有几种方法？（前提：int num = 10;）
        // 方式一：num = num + 1;
        // 方式二：num += 1;
        // 方式三：num++; (推荐)

        // 练习 1
        int i = 1;
        i *= 0.1;
        System.out.println(i); // 0
        i++;
        System.out.println(i); // 1

        // 练习 2
        int m = 2;
        int n = 3;
        n *= m++;
        System.out.println("m = " + m); // 3
        System.out.println("n = " + n); // 6

        // 练习 3
        int n1 = 10;
        n1 += (n1++) + (++n1);
        System.out.println(n1); // 32
    }
}
```

### 比较运算符

*== != > < >= <= instanceof*

- 比较运算符的结果是 boolean 类型
- 区分 == 和 =

```java
public class CompareTest {
    public static void main(String[] args) {
        int i = 10;
        int j = 20;
        System.out.println(i == j); // false
        System.out.println(i = j);  // 20

        boolean b1 = true;
        boolean b2 = false;
        System.out.println(b2 == b1); // false
        System.out.println(b2 = b1);  // true
    }
}
```

### 逻辑运算符

逻辑运算符都是操作 **boolean** 类型的变量

|     a     |     b     |  a&b  | a&&b  | a\|b  | a\|\|b |  !a   |  a^b  |
| :-------: | :-------: | :---: | :---: | :---: | :----: | :---: | :---: |
| **true**  | **true**  | true  | true  | true  |  true  | false | false |
| **true**  | **false** | false | false | true  |  true  | false | true  |
| **false** | **true**  | false | false | true  |  true  | true  | true  |
| **false** | **false** | false | false | false | false  | true  | false |

*区分 & 和 &&*

- 相同点 1：& 和 && 的运算结果相同

- 相同点 2：当符号左边是 true 时，二者都会执行符号右边的运算
- 不同点：当符号左边是 false 时，& 继续执行符号右边的运算，&& 不再执行
- 开发中，推荐使用 &&

*区分 | 和 ||*

- 相同点 1：| 和 || 的运算结果相同
- 相同点 2：当符号左边是 false 时，二者都会执行符号右边的运算
- 不同点：当符号左边是 true 时，| 继续执行符号右边的运算，|| 不再执行
- *开发中，推荐使用 ||

```java
public class LogicTest {
    public static void main(String[] args) {
        
        // 区分 & 和 &&
        // 相同点 1：& 和 && 的运算结果相同
        // 相同点 2：当符号左边是 true 时，二者都会执行符号右边的运算
        // 不同点：当符号左边是 false 时，& 继续执行符号右边的运算，&& 不再执行
        // 开发中，推荐使用 &&
        boolean b1 = true;
        b1 = false;
        int num1 = 10;
        if(b1 & (num1++ > 0)) {
            System.out.println("我现在在北京");
        } else {
            System.out.println("我现在在南京");
        }

        System.out.println("num1 = " + num1);

        boolean b2 = true;
        b2 = false;
        int num2 = 10;
        if(b2 && (num2++ > 0)) {
            System.out.println("我现在在北京");
        } else {
            System.out.println("我现在在南京");
        }

        System.out.println("num2 = " + num2);

        // 区分 | 和 ||
        // 相同点 1：| 和 || 的运算结果相同
        // 相同点 2：当符号左边是 false 时，二者都会执行符号右边的运算
        // 不同点：当符号左边是 true 时，| 继续执行符号右边的运算，|| 不再执行
        // 开发中，推荐使用 ||
        boolean b3 = false;
        b3 = true;
        int num3 = 10;
        if(b3 | (num3++ > 0)) {
            System.out.println("我现在在北京");
        } else {
            System.out.println("我现在在南京");
        }

        System.out.println("num3 = " + num3);

        boolean b4 = false;
        b4 = true;
        int num4 = 10;
        if(b4 || (num4++ > 0)) {
            System.out.println("我现在在北京");
        } else {
            System.out.println("我现在在南京");
        }

        System.out.println("num4 = " + num4);
    }
}
```

### 位运算符

- 位运算符操作的都是整型的数据
- << 在一定范围内，每向左移一位，相当于 \* 2
- 在一定范围内，每向右移一位，相当于 / 2

| 运算符 |    运算    | 范例        |
| :----: | :--------: | :---------- |
|   <<   |    左移    | 3 << 2 = 12 |
|   >>   |    右移    | 3 >> 1 = 1  |
|  >>>   | 无符号右移 | 3 >>> 1 = 1 |
|   &    |   与运算   | 6 & 3 = 2   |
|   \|   |   或运算   | 6 \| 3 = 7  |
|   ^    |  异或运算  | 6 ^ 3 = 5   |
|   ~    |  取反运算  | ~6 = -7     |

```java
public class BitTest {
    public static void main(String[] args) {
        int i = 21;
        System.out.println("i << 2 = " + (i << 2));
        System.out.println("i << 3 = " + (i << 3));

        System.out.println("i << 26 = " + (i << 26));
        System.out.println("i << 27 = " + (i << 27));

        int m = 12;
        int n = 5;
        System.out.println("m & n = " + (m & n));
        System.out.println("m | n = " + (m | n));
        System.out.println("m ^ n = " + (m ^ n));

        // 练习：交换两个变量的值
        int num1 = 10;
        int num2 = 20;
        System.out.println("num1 = " + num1 + ", num2 = " + num2);

        // 方式一：定义临时变量
        int temp = num1;
        num1 = num2;
        num2 = temp;
        System.out.println("num1 = " + num1 + ", num2 = " + num2);

        // 方式二：
        // 好处：不用定义临时变量
        // 弊端：相加操作可能超出存储范围、有局限性（只适用于数值类型）
        num1 = num1 + num2;
        num2 = num1 - num2;
        num1 = num1 - num2;
        System.out.println("num1 = " + num1 + ", num2 = " + num2);

        // 方式三
        num1 ^= num2;
        num2 ^= num1;
        num1 ^= num2;
        System.out.println("num1 = " + num1 + ", num2 = " + num2);
    }
}
```

### 三元运算符

结构：(条件表达式)?表达式1：表达式2；

说明：

- 条件表达式的结果为 boolean 类型
- 根据条件表达式真或假，决定执行表达式 1，还是表达式 2
  如果表达式为 true，则执行表达式 1。
  如果表达式为 false，则执行表达式 2。
- 表达式 1 和 表达式 2 要求是一致的
- 三元运算符可以嵌套使用

凡是可以使用三元运算符的地方，都可以改写为 if-else

如果程序既可以用三元运算符，又可以用 if-else，优先选择三元运算符

```java
public class TripleTest {
    public static void main(String[] args) {
        // 获取两个整数的较大值
        int m = 12;
        int n = 5;

        int max = (m > n)? m : n;
        System.out.println(max);

        double num = (m > n)? 2 : 1.0;
        System.out.println(num);

        n = 12;
        String maxStr = (m > n)? "m大" : ((m == n)? "m和n相等" : "n大");
        System.out.println(maxStr);

        //*********************************************
        int n1 = 12;
        int n2 = 30;
        int n3 = -43;

        int max1 = (n1 > n2)? n1 : n2;
        max1 = (max1 > n3)? max1 : n3;
        System.out.println("三个数中的最大值为：" + max1);
    }
}
```

## 2.5 程序流程控制

### 分支结构

#### if-else

三种结构

- 第一种：

 if(条件表达式){

 	执行表达式

 }



- 第二种：二选一

 if(条件表达式){

 	执行表达式 1

 } else {

 	执行表达式 2

 }



- 第三种：n 选一

 if(条件表达式)

​	执行表达式 1

 } else if(条件表达式) {

​	执行表达式 2

 } else if(条件表达式) {

​	执行表达式 3

}

 ...

 else {

​	执行表达式 n

}

```java
public class IfTest {
    public static void main(String[] args) {
        // 举例 1
        int heartBeats = 79;
        if(heartBeats < 60 || heartBeats > 100) {
            System.out.println("需要做进一步检查");
        }

        System.out.println("检查结束");

        // 举例 2
        int age = 23;
        if(age < 18) {
            System.out.println("你还可以看动画片");
        } else {
            System.out.println("你可以看成人电源了");
        }

        // 举例 3
        age = 33;
        if(age < 0) {
            System.out.println("您输入的数据非法");
        } else if (age < 18) {
            System.out.println("青少年时期");
        } else if (age < 35) {
            System.out.println("青壮年时期");
        } else if (age < 60) {
            System.out.println("中年时期");
        } else if (age < 120) {
            System.out.println("老年时期");
        } else {
            System.out.println("你是要成仙啊~");
        }
    }
}
```

#### if语句例题1

岳小鹏参加Java考试，他和父亲岳不群达成承诺：如果：
成绩为100分时，奖励一辆BMW；
成绩为(80，99]时，奖励一台iphone xs max；
当成绩为[60,80]时，奖励一个 iPad；
其它时，什么奖励也没有。
请从键盘输入岳小鹏的期末成绩，并加以判断

##### 从键盘获取数据

从键盘获取不同类型的变量：需要使用Scanner类

 具体实现步骤：

- 导包：import java.util.Scanner
- Scanner实例化
- 调用Scanner类的相关方法（next() / nextXxx()），获取指定类型的变量

 *注意：*

  需要根据相应的方法，来输入指定类型的值。如果输入的数据类型与要求的类型不匹配时，会报异常：InputMisMatchException

```java
import java.util.Scanner;

class ScannerTest {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        System.out.println("请输入你的姓名：");
        String name = scan.next();
        System.out.println(name);

        System.out.println("请输入你的芳龄：");
        int age = scan.nextInt();
        System.out.println(age);

        System.out.println("请输入你的体重：");
        double weight = scan.nextDouble();
        System.out.println(weight);

        System.out.println("你是否已婚？（true/false）");
        boolean isMarried = scan.nextBoolean();
        System.out.println(isMarried);

        // 对于 char 型的获取，Scanner没有提供相关方法，只能获取一个字符串
        System.out.println("请输入你的性别：（男/女）");
        String gender = scan.next();
        char genderChar = gender.charAt(0); // 获取索引为0位置上的字符
        System.out.println(genderChar);
    }
}
```

```java
import java.util.Scanner;

class IfTest {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        System.out.println("请输入岳小鹏期末成绩：(0-100)");
        int score = scan.nextInt();

        if (score == 100) {
            System.out.println("奖励一辆BMW");
        } else if (score > 80 && score <= 99) {
            System.out.println("奖励一台iphone xs max");
        } else if (score >= 60 && score <= 80) {
            System.out.println("奖励一个 iPad");
        } else {
            System.out.println("什么奖励也没有");
        }
    }
}
```

#### if语句例题2

 编写程序：由键盘输入三个整数分别存入变量num1、num2、num3

 对它们进行排序(使用 if-else if-else)，并且从小到大输出。

```java
import java.util.Scanner;

class IfTest2 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("请输入第一个整数：");
        int num1 = scanner.nextInt();
        System.out.println("请输入第二个整数：");
        int num2 = scanner.nextInt();
        System.out.println("请输入第三个整数：");
        int num3 = scanner.nextInt();

        if (num1 >= num2) {
            if (num3 >= num1) {
                System.out.println(num2 + "," + num1 + "," + num3);
            } else if (num3 <= num2) {
                System.out.println(num3 + "," + num2 + "," + num1);
            } else {
                System.out.println(num2 + "," + num3 + "," + num1);
            }
        } else {
            if (num3 >= num2) {
                System.out.println(num1 + "," + num2 + "," + num3);
            } else if (num3 <= num1) {
                System.out.println(num3 + "," + num1 + "," + num2);
            } else {
                System.out.println(num1 + "," + num3 + "," + num2);
            }
        }
    }
}
```

 if-else结构是可以相互嵌套的。

 如果if-else结构中的执行语句只有一行时，对应的一对}可以省略的。但是，不建议省略。

#### switch-case结构

 - 根据switch表达式中的值，依次匹配各个case中的常量。一旦匹配成功，则进入相应case结构中，执行相应语句。
   执行完毕后，则仍然继续向下执行其他case结构中的执行语句，直到遇到break关键字或此switch-case结构末尾结束为止。
 - break，可以使用在switch-case结构中，表示一旦执行到此关键字，就跳出switch-case结构。
 - switch结构中的表达式，只能是如下的6种数据类型之一：byte、short、char、int、枚举类型（JDK5.0新增）、String（JDK7.0新增）
 - case 之后只能是常量，不能是范围。
 - break关键字是可选的。
 - default相当于if-else中的else，是可选的，而且位置是灵活的。

```java
class SwitchCaseTest {
    public static void main(String[] args) {

        int num = 1;

        switch (num) {
        case 0:
            System.out.println("zero");
            break;
        case 1:
            System.out.println("one");
            break;
        case 2:
            System.out.println("two");
            break;
        case 3:
            System.out.println("three");
            break;
        default:
            System.out.println("other");
        }

        String season = "summer";
        switch (season) {
        case "spring":
            System.out.println("春暖花开");
            break;
        case "summer":
            System.out.println("夏日炎炎");
            break;
        case "autumn":
            System.out.println("秋高气爽");
            break;
        case "winter":
            System.out.println("冬雪皑皑");
            break;
        default:
            System.out.println("季节输入有误");
            break;
        }
    }
}
```

##### 例题1

对学生成绩大于60分的，输出“合格”。低于60分的，输出“不合格”。

##### 例题2

根据用于指定月份，打印该月份所属的季节。 3,4,5 春季 6,7,8 夏季 9,10,11 秋季 12, 1, 2 冬季

```java
class SwitchCaseTest1 {
    public static void main(String[] args) {

        int score = 78;

        switch (score / 60) {
            case 0:
                System.out.println("不合格");
                break;
            case 1:
                System.out.println("合格");
                break;
        }

        int month = 12;
        switch (month) {
            case 3:
            case 4:
            case 5:
                System.out.println("春季");
                break;
            case 6:
            case 7:
            case 8:
                System.out.println("夏季");
                break;
            case 9:
            case 10:
            case 11:
                System.out.println("秋季");
                break;
            case 12:
            case 1:
            case 2:
                System.out.println("冬季");
                break;
        }
    }
}
```

##### 练习

 从键盘分别输入年、月、日，判断这一天是当年的第几天

注：判断一年是否是闰年的标准：

 1）可以被4整除，但不可被100整除

 或

 2）可以被400整除

```java
import java.util.Scanner;
class SwitchCaseExer {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输入year：");
        int year = scan.nextInt();
        
        System.out.println("请输入month：");
        int month = scan.nextInt();

        System.out.println("请输入day：");
        int day = scan.nextInt();

        boolean isLeap = false;
        if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
            isLeap = true;
        }

        int sumDays = 0;

        switch (month) {
            case 12:
                sumDays += 30;
            case 11:
                sumDays += 31;
            case 10:
                sumDays += 30;
            case 9:
                sumDays += 31;
            case 8:
                sumDays += 31;
            case 7:
                sumDays += 30;
            case 6:
                sumDays += 31;
            case 5:
                sumDays += 30;
            case 4:
                sumDays += 31;
            case 3:
                // sumDays += 28;
                if (isLeap) {
                    sumDays += 29;
                } else {
                    sumDays += 28;
                }
            case 2:
                sumDays += 31;
            case 1:
                sumDays += day;
        }
        System.out.println(year + "年" + month + "月" + day + "日是当年的第" + sumDays + "天");

        scan.close();
    }
}
```

### 循环结构

循环语句分类

- for 循环
- while 循环
- do-while 循环

循环语句的四个组成部分

- ① 初始化条件
- ② 循环条件（boolean类型）
- ③ 循环体
- ④ 迭代条件

#### for循环

for 循环的结构

for (①; ②; ④) {

​	③；

}

```java
class ForTest {
    public static void main(String[] args) {

        for (int i = 1; i <= 5; i++) {
            System.out.println("Hello World!");
        }

        int num = 1;
        for (System.out.println('a'); num <= 3; System.out.println('c'), num++) {
            System.out.print('b');
        } // a\nbc\nbc\nbc

        System.out.println();

        // 例题：遍历 100 以内的偶数，输出所有偶数的和，输出偶数的个数
        int sum = 0;   // 记录所有偶数的和
        int count = 0; // 记录偶数的个数
        for (int i = 1; i <= 100; i++) {
            if (i % 2 == 0) {
                System.out.println(i);
                sum += i;
                count++;
            }
        }
        System.out.println("sum = " + sum);
        System.out.println("count = " + count);
    }
}
```

编写程序从1循环到150，并在每行打印一个值，

另外在每个3的倍数行上打印出“foo”,

在每个5的倍数行上打印“biz”,

在每个7的倍数行上打印输出“baz”。

```java
class ForTest1 {
    public static void main(String[] args) {

        for (int i = 1; i <= 150; i++) {
            System.out.print(i + "\t");

            if (i % 3 == 0) {
                System.out.print("foo");
            }

            if (i % 5 == 0) {
                System.out.print("biz");
            }

            if (i % 7 == 0) {
                System.out.print("baz");
            }

            System.out.println();
        }
    }
}
```

题目：输入两个正整数m和n，求其最大公约数和最小公倍数。
比如：12和20的最大公约数是4，最小公倍数是60。
说明：break关键字的使用

```java
import java.util.Scanner;
class ForTest {
    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);

        System.out.println("请输入第一个正整数：");
        int m = scan.nextInt();

        System.out.println("请输入第二个正整数：");
        int n = scan.nextInt();

        // 最大公约数
        int min = (m <= n)? m : n;
        for (int i = min; i >= 1; i--) {
            if (m % i ==0 && n % i == 0) {
                System.out.println("最大公约数为：" + i);
                break;
            }
        }

        // 最小公倍数
        int max = (m >= n)? m : n;
        for (int i = max; i <= m*n; i++) {
            if (i % m ==0 && i % n == 0) {
                System.out.println("最小公倍数为：" + i);
                break;
            }
        }

        scan.close();
    }
}
```

#### while循环

while 循环的结构

①

while ② {

​	③;

​	④;

}

```java
class WhileTest {
    public static void main(String[] args) {

        // 遍历 100 以内的所有偶数
        int i = 1;
        while (i <= 100) {
            if (i % 2 == 0) {
                System.out.println(i);
            }
            i++;
        }

    }
}
```

#### do-while循环

 do-while 循环的结构
 ①;
 do {
    ③;
    ④;
 } while (②);

```java
class DoWhileTest {
    public static void main(String[] args) {

        // 遍历 100 以内的所有偶数，并计算所有偶数的和及偶数的个数
        int num = 1;
        int sum, count;
        sum = count = 0;
        do {
            if (num % 2 == 0) {
                System.out.println(num);
                sum += num;
                count++;
            }
            num++;
        } while (num <= 100);

        System.out.println("总和为：" + sum);
        System.out.println("个数为：" + count);

        System.out.println();

        //**************do-while至少执行一次******************
        int number = 10;
        while (number > 10) {
            System.out.println("hello:while");
            number--;
        }

        number = 10;
        do {
            System.out.println("hello:do-while");
            number--;
        } while (number > 10);
    }
}
```

##### 练习

 题目：
 从键盘读入个数不确定的整数，并判断读入的正数和负数的个数，输入为0时结束程序。

```java
import java.util.Scanner;
class ForWhileTest {
    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);

        int countPositive = 0; // number of positive
        int countNegative = 0; // number of negative
        while (true) { // for (;;)
            int number = scan.nextInt();

            if (number > 0) {
                countPositive++;
            } else if (number < 0) {
                countNegative++;
            } else {
                break;
            }
        }

        System.out.println("输入的正数个数：" + countPositive);
        System.out.println("输入的负数个数：" + countNegative);

        scan.close();

    }
}
```

#### 嵌套循环

嵌套循环：将一个循环结构 A 声明在另一个循环结构 B 的循环体中

外层循环：循环结构 B

内层循环：循环结构 A

*说明*：设外层循环次数为 m 次，内层为 n 次，则内层循环体实际上需要执行 m\*n 次

```java
class ForForTest {
    public static void main(String[] args) {

        // 输出
        /*

         ******

         */
        for (int i = 1; i <= 6; i++) {
            System.out.print("*");
        }

        System.out.println("\n");

        // 输出
        /*

         ******
         ******
         ******
         ******

         */
        for (int i = 1; i <= 4; i++) {
            for (int j = 1; j <= 6; j++) {
                System.out.print("*");
            }
            System.out.println();
        }

        System.out.println();

        // 输出
        /*

         *
         **
         ***
         ****
         *****

         */
        for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }

        System.out.println();

        // 输出
        /*

         ****
         ***
         **
         *

         */
        for (int i = 1; i <= 4; i++) {
            for (int j = 1; j <= 5-i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }

        System.out.println();

        // 输出
        /*

         *
         **
         ***
         ****
         *****
         ****
         ***
         **
         *

         */
        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= 5-Math.abs(i - 5); j++) {
                System.out.print("*");
            }
            System.out.println();
        }

        // 输出
        /*

             *
            * *
           * * *
          * * * *
         * * * * *
          * * * *
           * * *
            * *
             *

         */
        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= Math.abs(5-i); j++) {
                System.out.print(" ");
            }
            for (int k = 1; k <= 5-Math.abs(i - 5); k++) {
                System.out.print("* ");
            }
            System.out.println();
        }

    }
}
```

##### 例题1

 九九乘法表
 1 * 1 = 1
 1 * 2 = 2    2 * 2 = 4
 ...
 1 * 9 = 9    2 * 9 = 18    ...    9 * 9 = 81

```java
class NineNineTable {
    public static void main(String[] args) {

        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(j + " × " + i + " = " + (i * j) + "\t");
            }
            System.out.print("\n");
        }

    }
}
```

##### 例题2

100以内的所有质数
质数：素数，只能被1和它本身整除的自然数。 --> 从2开始，到这个数-1结束为止，都不能被这个数本身整除。

###### 方式一

```java
class PrimeNumberTest {
    public static void main(String[] args) {

        boolean isFlag = true;

        // 获取当前时间距 1970-01-01 00:00:00 的毫秒数
        long start = System.currentTimeMillis();

        int count = 0;

        for (int i = 2; i <= 100000; i++) {
            for (int j = 2; j <= Math.sqrt(i); j++) { // 优化二：对质数有效
                if (i % j == 0) {
                    isFlag = false;
                    break; // 优化一：只对非质数有效
                }
            }

            if (isFlag) {
                // System.out.println(i);
                count++;
            }
            // reset flag
            isFlag = true;
        }

        long end = System.currentTimeMillis();

        System.out.println("质数的个数为：" + count); // 7712 - 优化一：break: 704 - 优化二: 17
        System.out.println("所花费的时间为：" + (end - start)); // 8847 - 优化一：break: 1370 - 优化二: 731

    }
}
```

###### 方式二

```java
class PrimeNumberTest1 {
    public static void main(String[] args) {

        // 获取当前时间距 1970-01-01 00:00:00 的毫秒数
        long start = System.currentTimeMillis();

        int count = 0;

        label:
        for (int i = 2; i <= 100000; i++) {
            for (int j = 2; j <= Math.sqrt(i); j++) {
                if (i % j == 0) {
                    continue label;
                }
            }
            // 能执行到此处的，都是质数
            count++;
        }

        long end = System.currentTimeMillis();

        System.out.println("质数的个数为：" + count);
        System.out.println("所花费的时间为：" + (end - start)); // 17

    }
}
```



#### 特殊关键字的使用：break、continue

使用范围：
    break: switch-case 和 循环结构中
    continue: 循环结构中

作用：
   break: 结束当前循环
   continue: 结束当次循环

说明：break 和 continue 后不能声明执行语句

```java
class BreakContinueTest {
    public static void main(String[] args) {

        for (int i = 1; i <= 10; i++) {
            if (i % 4 == 0) {
                // break; // 1 2 3
                continue; // 1 2 3 5 6 7 9 10
            }
            System.out.println(i);
        }

        System.out.println("\n");

        //****************************************
        label:
        for (int i = 1; i <= 4; i++) {
            for (int j = 1; j <= 10; j++) {
                if (j % 4 == 0) {
                    // break; // 默认跳出最近的一层循环
                    // continue;

                    // break label; // 跳出指定标识的一层循环
                    continue label;
                }

                System.out.print(j);
            }
            System.out.println();
        }

    }
}
```

#### 特殊流程控制语句：return

- return：并非专门用于结束循环的，它的功能是结束一个方法。当一个方法执行到一个return语句时，这个方法将被结束。
- 与break和continue不同的是，return直接结束整个方法，不管这个return处于多少层循环之内。