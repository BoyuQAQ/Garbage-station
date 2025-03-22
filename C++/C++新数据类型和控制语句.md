1. 
2. bool类型
    1. 含义：表示真和假，打印的值只有0和1
    2. 占用1个字节
    3. 一般用在函数返回值或者充当标记开关等使用。
3. 引用类型：理解称为起别名
    1. 充当函数参数，防止拷贝本的产生
    2. 充当函数返回值类型，增加左值使用
    3. 右值引用：固定写法:int&&
        1. 必须传入常量：最显著特点为当前的值可以改变形参的值

```c++
int 张三=0;
int& 小宝贝=张三；//表示张三还有另一个名字叫做小宝贝
```

## 整型

作用：整型变量表示的是整数类型的数据

C++能够表示整型的类型有以下几种方式，**区别在于所占内存空间不同**

| 数据类型            |                  占用空间                   | 取值范围         |
| ------------------- | :-----------------------------------------: | ---------------- |
| short(短整型)       |                    2字节                    | (-2^15~ 2^15-1)  |
| int(整型)           |                    4字节                    | (-2^31 ~ 2^31-1) |
| long（长整形)       | windows为4字节Linux为4字节(32位)8字节(64位) | (-2^31 ~ 2^31-1) |
| long long(长长整形) |                    8字节                    | (-2^63 ~ 2^63-1) |

由于其占用内存空间不同，其所能表示的数值范围也不相同

### sizeof关键字

作用：利用sizeof关键字可以统计数据类型所占内存大小

语法：sizeof(数据类型 /变量)

```c++
#include <iostream>
using namespace std;
int main() {
	short num1 = 10;//短整型(-32768~32767)
	int num2 = 20;//整型
	long num3 = 10;
	cout << "short占用内存空间为：" << sizeof(num1) << endl;
	cout << "int占用内存空间为：" << sizeof(num2) << endl;
	cout << "long占用内存空间为：" << sizeof(num3) << endl;
	system("pause");
}
```

## 实型（浮点型）

作用：用于表示小数 

浮点型变量分为两种：

 	1.  单精度float
 	2.  双精度double

两者的区别在于表示的有效数字范围不同

| 数据类型 | 占用空间 | 有效数字范围    |
| -------- | -------- | --------------- |
| float    | 4字节    | 7位有效数字     |
| double   | 8字节    | 15~16位有效数字 |

```c++
#include <iostream>
using namespace std;
int main() {
	float f1 = 3.1415926f; //一定要在数值后加一个f，否则默认为double类型
	cout << "f1=" << f1 << endl;
    cout << "float所占内存空间位：" << sizeof(f1) << endl;

	double d1 = 3.1415926;
	cout << "d1=" << d1 << endl;
	//目前来说，C++最多显示的小数位数是6位
     cout << "double所占内存空间位：" << sizeof(d1) << endl;
	system("pause");
}	
```

### 表示小数的另一种方式：科学计数法

```c++
#include <iostream>
using namespace std;
int main() {
	float f2 = 3e2; //3*10^2
	cout << "f2=" << f2 << endl;

	float  f3 = 3e-2; //3*0.1^2
	cout << "f3=" << f3 << endl;
	system("pause");
}
```

en:为10的n次方

e-n:为0.1的n次方

## 字符型

作用：字符型变量用于显示单个字符

语法：char ch =‘a’;

> 注意1：在显示字符型变量时，用单引号将字符括起来，不要用双引号

> 注意2：单引号内只能有一个字符，不可以是字符串

* C和C++中字符型变量只占用一个字节。
* 字符型变量并不是把字符本身放到内存总存储，而是将对应的ASCII编码放入到存储单元。

```c++
#include <iostream>
using namespace std;
int main() {
	// 1、字符型变量创建方式
	char ch = 'a';
	cout << ch << endl;
	// 2、字符型变量所占内存大小
	cout << "char型所占内存:"<< sizeof(char) << endl;
	//3、字符型变量常见错误
	char ch1 = "ab";//创建字符型变量时候，要用单引号，不能用双引号 
	char ch2 = 'abcdef';//字符型变量只能存放一个字符
	//4、字符型变量对应ASCII编码
	cout << (int)ch << endl;
	system("pause");
}
```

## 转义字符

作用：用于表示一些不能显示出来的ASCII字符

现阶段常用的转义字符有：``

1. 

2. | 转义字符 | 含义                               | ASCII码值（十进制） |
    | -------- | ---------------------------------- | ------------------- |
    | `\a`     | 警报                               | 007                 |
    | `\b`     | 退格(BS)，将当前位置移到前一列     | 008                 |
    | `\f`     | 换页(FF)，将当前位置移到下页开头   | 012                 |
    | `\n`     | 换行(LF)，将当前位置移到下一行开头 | 010                 |
    | `\r`     | 回车(CR)，将当前位置移到本行开头   | 013                 |
    | `\t`     | 水平制表(HT) （跳到下一个TAB位置） | 009                 |
    | `\v`     | 垂直制表(VT)                       | 011                 |
    | `\\`     | 代表一个反斜线字符 `\`             | 092                 |
    | `\'`     | 代表一个单引号（撇号）字符         | 039                 |
    | `\"`     | 代表一个双引号字符                 | 034                 |
    | `\?`     | 代表一个问号                       | 063                 |
    | \0       | 数字0                              | 000                 |
    | \ddd     | 8进制转义字符，d范围0~7            | 3位8进制            |

| `\xhh` | 16进制转义字符，h范围0-9, A-F | 3位16进制 |
| ------ | ----------------------------- | --------- |
|        |                               |           |

## 字符串型

作用：用于表示一串字符

#### 两种风格

1. C风格字符串：char 变量名[] = “字符串值”

```c++
int main(){
    char str1[]="hello world";
    cout << str1 <<endl;
    system("pause");
    return 0;
}
```

> 注意：C风格的字符串要用双引号括起来

2. C++风格字符串：string 变量名=“字符串值”

```c++
#include <iostream>
#include <string> //用C++风格字符串时候，要包含这个头文件
using namespace std;
int mian(){
    string str2="hello world";
    cout << str2 << endl;
    system("pause");
}
```

> 注意：C++风格字符串，需要加入头文件#include `<string>`

## 布尔型bool

作用：布尔数据类型代表真或假的值

bool类型只有两个值：

* true  — 真（本质是1)
* false — 假 (本质是0)

bool类型占1字节大小

```c++
#include <iostream>
using namespace std;
int main() {
	//1、创建bool数据类型
	bool flag = true;//true代表真
	cout << flag << endl;
	flag = false;//false代表假
	cout << flag << endl;
	cout << "bool类型所占内存空间" << sizeof(flag) << endl;
	system("pause");
}
```

## 数据的输入

作用：用于从键盘获取数据

关键字：cin

语法：cin >> 变量

```c++
#include <iostream>
#include <string>
using namespace std;
int main() {
	// 1、整型
	int a = 0;
	cout << "请给整型变量a赋值：" << endl;
	cin >> a;
	cout << "a = " << a << endl;
	// 2、浮点型
	float f = 3.14f;
	cout << "请给浮点型变量f赋值：" << endl;
	cin >> f;
	cout << "f = " << f << endl;
	// 3、字符型
	char ch = 'A';
	cout << "请给字符型变量ch赋值：" << endl;
	cin >> ch;
	cout << "ch = " << ch << endl;
	// 4、字符串型
	string str = "Hello, C++!";
	cout << "请给字符串型变量str赋值：" << endl;
	cin >> str;
	cout << "str = " << str << endl;
	// 5、布尔型	
	bool b = true;
	cout << "请给布尔型变量b赋值：" << endl;
	cin >> b;
	cout << "b = " << b << endl;
	system("pause");
}
```

## 运算符

 作用：用于执行代码的运算

| 运算符类型 | 作用                                   |
| ---------- | -------------------------------------- |
| 算术运算符 | 用于处理四则运算                       |
| 赋值运算符 | 用于将表达式的幅值给变量               |
| 比较运算符 | 用于表达式的比较，并返回一个真值或假植 |
| 逻辑运算符 | 用于根据表达式的值返回真值或假植       |



### 算术运算符

| 运算符 | 术语       | 示例        | 结果      |
| ------ | ---------- | ----------- | --------- |
| +      | 正号       | +3          | 3         |
| -      | 负号       | -3          | -3        |
| +      | 加         | 10 + 5      | 15        |
| -      | 减         | 10 - 5      | 5         |
| *      | 乘         | 10 * 5      | 50        |
| /      | 除         | 10 / 5      | 2         |
| %      | 取模(取余) | 10 % 3      | 1         |
| ++     | 前置递增   | a=2; b=++a; | a=3; b=3; |
| ++     | 后置递增   | a=2; b=a++; | a=3; b=2; |
| --     | 前置递减   | a=2; b=--a; | a=1; b=1; |
| --     | 后置递减   | a=2; b=a--; | a=1; b=2; |

```c++
#include <iostream>
#include <string>
using namespace std;
int main() {
	//加减乘除
	int a1 = 10;
	int b1 = 3;
	cout << a1 + b1 << endl;
	cout << a1 - b1 << endl;
	cout << a1 * b1 << endl;
	cout << a1 / b1 << endl;//两个整数相除，结果是整数，会将小数部分去掉
	int a3 = 10;
	int b3 = 0;
	//cout << a3 / b3 << endl;//除数不能为0
	double d1 = 0.5;
	double d2 = 0.22;
	cout << d1 / d2 << endl;//运算结果也可以是小数
	system("pause");
}
```

### 赋值运算符

| 运算符 | 术语   | 示例       | 结果      |
| ------ | ------ | ---------- | --------- |
| =      | 赋值   | a=2; b=3;  | a=2; b=3; |
| +=     | 加等于 | a=0; a+=2; | a=2;      |
| -=     | 减等于 | a=5; a-=3; | a=2;      |
| *=     | 乘等于 | a=2; a*=2; | a=4;      |
| /=     | 除等于 | a=4; a/=2; | a=2;      |
| %=     | 模等于 | a=3; a%=2; | a=1;      |

```c++
#include <iostream>
#include <string>
using namespace std;
int main() {
	//赋值运算符
	int a = 100;
	cout << "a= " << a << endl;
	// +=
	a = 10;
	a += 2;//a=a+2
	cout << "a+=2= " << a << endl;
	// -=
	a = 10;
	a -= 2;//a=a-2
	cout << "a-=2= " << a << endl;
	// *=
	a = 10;
	a *= 2;//a=a*2
	cout << "a*=2= " << a << endl;
	// /=
	a = 10;
	a /= 2;//a=a/2
	cout << "a/=2= " << a << endl;
	// %=
	a = 10;
	a %= 2;//a=a%2
	cout << "a%=2= " << a << endl;
	system("pause");
}
```

### 比较运算符

作用：用于表达式的比较，并返回一个真值或假植

| 运算符 | 术语     | 示例   | 结果 |
| ------ | -------- | ------ | ---- |
| ==     | 相等于   | 4 == 3 | 0    |
| !=     | 不等于   | 4 != 3 | 1    |
| <      | 小于     | 4 < 3  | 0    |
| >      | 大于     | 4 > 3  | 1    |
| <=     | 小于等于 | 4 <= 3 | 0    |
| >=     | 大于等于 | 4 >= 1 | 1    |

```c++
#include <iostream>
using namespace std;
int main() {
	//比较运算符
	//==
	int a = 10;
	int b = 20;
	cout << (a == b) << endl; 
	//!=
	int a = 10;
	int b = 20;
	cout << (a != b) << endl;
	//>
	int a = 10;
	int b = 20;
	cout << (a > b) << endl;
	//<
	int a = 10;
	int b = 20;
	cout << (a < b) << endl;
	//>=
	int a = 10;
	int b = 20;
	cout << (a >= b) << endl;
	//<=
	int a = 10;
	int b = 20;
	cout << (a <= b) << endl;
	return 0;
	system("pause");
}
```

### 逻辑运算符

作用：用于根据表达式的值返回真值或假值

| 运算符 | 术语 | 示例     | 结果                                                         |
| ------ | ---- | -------- | ------------------------------------------------------------ |
| !      | 非   | !a       | 如果 a 为假，则 !a 为真；如果 a 为真，则 !a 为假。           |
| &&     | 与   | a && b   | 如果 a 和 b 都为真，则结果为真，否则为假。                   |
| \|\|   | 或   | a \|\| b | 如果 a 和 b 有一个为真，则结果为真；二者都为假时，结果为假。 |

```c++
#include <iostream>
using namespace std;
int main() {
	//逻辑运算符 非
	int a = 10;
	cout << !a << endl;
	cout << !!a << endl;
	system("pause");

	//逻辑运算符 与
	int b = 10;
	int c = 20;
	cout << (b && c) << endl;
	cout << (b && 0) << endl;
	cout << (0 && 0) << endl;

	//逻辑运算符 或
	int d = 10;
	int e = 20;
	cout << (d || e) << endl;
	cout << (d || 0) << endl;
	cout << (0 || 0) << endl;
	return 0;
}
```

## 程序流程结构

C/C++支持最基本的三种程序运行结构：顺序结构、选择结构、循环结构

* 顺序结构：程序按顺序执行，不发生跳转
* 选择结构：依据条件是否满足，有选择的执行相应功能
* 循环结构：依据条件是否满足，循环多次执行某段代码

### 选择结构

#### if语句

if语句的三种形式

* 单行格式if语句

    * 格式：if(条件){条件满足执行的语句}

    * 

    * ```mermaid
        graph TD;
            开始 --> 判断条件;
            判断条件 -->|true| 执行语句;
            执行语句 --> 结束;
            判断条件 -->|false| 结束;

* 多行格式if语句

    * 格式:if(体哦见){条件满足执行的语句}else{条件不满足执行的语句}

    * 

    * ```mermaid
        graph TD;
            开始 --> 判断条件;
            判断条件 -->|true| 执行语句1;
            判断条件 -->|false| 执行语句2;
            执行语句1 --> 结束;
            执行语句2 --> 结束;

* 多条件的if语句

    * 格式：fi(条件1){条件1满足执行的语句}else if(条件2){条件2满足执行的语句}…else{都不满足执行的语句}

    * 

    * ```mermaid
        graph TD;
            开始 --> 判断条件1;
            判断条件1 -->|true| 执行语句1;
            判断条件1 -->|false| 判断条件2;
            判断条件2 -->|true| 执行语句2;
            判断条件2 -->|false| 判断条件3;
            判断条件3 -->|true| 执行语句3;
            判断条件3 -->|false| 执行默认语句;
            执行语句1 --> 结束;
            执行语句2 --> 结束;
            执行语句3 --> 结束;
            执行默认语句 --> 结束;

### 嵌套if语句

在if语句中，可以嵌套使用if语句，达到更精确的条件判断

给一个案例：案例需求如下

* 提示用户输入一个高考考试分数，根据分数做出如下判断
* 分数如果大于600分视为考上一本，大于500分考上二本，大于400考上三本，其余视为为考上本科
* 在一本分数中，如果大于700分，考入北大，大于650分，考入清华，大于600考入人大。

```c++
#include <iostream>
using namespace std;
int main() {
	int score;
	cout << "请输入学生成绩：" << endl;
	cin >> score;
	if (score > 600)
	{
		if (score > 700)
		{
			cout << "恭喜你考上了清华大学" << endl;
		}
		else if (score > 650)
		{
			cout << "恭喜你考上了北大" << endl;
		}
		else if (score > 600)
		{
			cout << "恭喜你考上了人大" << endl;
		}
		else
		{
			cout << "恭喜你考上了一本大学" << endl;
		}
	}
	else if (score > 500)
	{
		cout << "恭喜你考上了二本大学" << endl;
	}
	else if (score > 400)
	{
		cout << "恭喜你考上了三本大学" << endl;
	}
	else
	{
		cout << "对不起，你未考上本科大学" << endl;
	}
	return 0;
}
```

## 三目运算符

作用：通过三目运算符实现简单的判断

语法：表达式1?表达式2：表达式3

解释：

​	如果表达式1的值为真，执行表达式2，并返回表达式2的结果；

​	如果表达式1的值为假，执行表达式3，并返回表达式3的结果；

 ## goto语句

作用：可以无条件跳转语句

语法：`goto 标记`

解释：如果标记的名称存在，执行到goto语句时，会跳转到标记的位置

但是会非常影响代码的逻辑结构，不方便连续阅读

```c++
#include <iostream>
using namespace std;
int main() {
	// goto语句
	cout << "1.txt" << endl;
	cout << "2.txt" << endl;
	goto FLAG;
	cout << "3.txt" << endl;
	cout << "4.txt" << endl;
FLAG:
	cout << "5.txt" << endl;
	cout << "6.txt" << endl;
	return 0;
}
```

