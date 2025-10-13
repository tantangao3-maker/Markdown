# 数据类型

|  数据类型   |                      描述                      |            大小（字节）            |                 示例                 |
| :---------: | :--------------------------------------------: | :--------------------------------: | :----------------------------------: |
|     int     |                      整形                      |                 4                  |             int a = 10;              |
|    char     |         字符型，通常用于存储ASCII 字符         |                 1                  |           char std = 'a';            |
|    float    |                浮点型（单精度）                | 4（约 ±3.4e±38（6-7 位有效数字）） |           float PI = 3.14;           |
|   double    |                  双精度浮点数                  | 8（约 ±1.7e±308（15 位有效数字）） |      double e = 2.71828182846;       |
|    long     |                     长整型                     |                4或8                |         long int a = 100000;         |
|    bool     |              布尔类型，表示真或假              |                 1                  |           bool b = false;            |
|    void     |                     无类型                     |                 4                  |           void main（）；            |
|    数组     |               相同类型元素的集合               |                                    |    int arr[5] = {1, 2, 3, 4, 5};     |
|    指针     |             存储变量内存地址的类型             |                                    |            int* ptr = &x;            |
|    引用     |                   变量的别名                   |                                    |            int& ref = x;             |
|    函数     |            函数类型，表示函数的签名            |                                    |       int func(int a, int b);        |
|   结构体    | 用户定义的数据类型，可以包含多个不同类型的成员 |                                    | **struct** Point { int x; int y; };  |
|     类      |    用户定义的数据类型，支持封装、继承和多态    |                                    |        class MyClass { ... };        |
|   联合体    |             多个成员共享同一块内存             |                                    | **union** Data { int i; float f; };  |
|    枚举     |             用户定义的整数常量集合             |                                    | **enum** Color { RED, GREEN, BLUE }; |
|   typedef   |               为现有类型定义别名               |                                    |          typedef int MyInt;          |
|    using    |        为现有类型定义别名（C++11 引入）        |                                    |          using MyInt = int;          |
| std::string |                   字符串类型                   |                                    |       std::string s = "Hello";       |
| std::vector |                    动态数组                    |                                    |  `std::vector<int> v = {1, 2, 3};`   |

# 常量

## 整数常量

整数常量可以是十进制、八进制或十六进制的常量。<br>0x表示十六进制，0表示八进制，不带后缀默认为十进制<br>整数常量也可以带一个后缀，是**U**和**L**的组合，**U**表示无符号整数(unsigned),**L**表示长整数(long)。后缀可以是大写也可以是小写，U和L的顺序任意
> 212         // 合法的 
> 215u        // 合法的 
> 0xFeeL      // 合法的 
> 078         // 非法的：8 不是八进制的数字 
> 032UU       // 非法的：不能重复后缀

>85         // 十进制
>0213       // 八进制 
>0x4b       // 十六进制 
>30         // 整数 
>30u        // 无符号整数 
>30l        // 长整数 
>30ul       // 无符号长整数

## 浮点常量

浮点常量由整数、小数点、小数部分和指数部分组成。<br>可以使用小数形式或者指数形式表示浮点常量。<br>e 或 E 被称为阶码标志，e 或 E 后面的有符号整数被称为阶码。阶码代表 10 的阶码次方。如3*10<sup>2</sup>=3e2

>3.14159       // 合法的 
>314159E-5L    // 合法的 
>510E          // 非法的：不完整的指数
>210f          // 非法的：没有小数或指数
>.e55          // 非法的：缺少整数或分数

## 布尔常量

* true值代表真(c中可用非0的数表示，如1)
* false值代表假(c中可用0表示)

我们不能单纯把true看成1，false看成0。

## 字符常量（转义字符）

| 转义序列    | 含义                       |
| :--------: | :------------------------: |
| \\\\       | \字符                     |
| \\'        | '字符                      |
| \\"        | "字符                      |
| \?         | ?字符                      |
| \a         | 警报铃声                   |
| \b         | 退格键                     |
| \f         | 换页符                     |
| \n         | 换行符                     |
| \r         | 回车                       |
| \t         | 水平制表符                 |
| \v         | 垂直制表符                 |
| \ooo       | 一到三位的八进制数         |
| \xhh       | 一个或多个数字的十六进制数 |

## 字符串常量

cpp中字符串字面值或常量是在双引号`""`中的。<br>一个字符串包含普通的字符、转义序列和通用的字符<br>可以用`\`做分隔符，把一个很长的字符串常量进行分行

```cpp
cout << "hello \
world" << endl;		//一般情况下输出为：hello world
```
```输出
hello world
```

## define 预处理器

`#define identifier value`

```cpp
#include <iostream>
using namespace std;
 
#define LENGTH 10   	//可以用LENGTH替换10
#define WIDTH  5		 
#define NEWLINE '\n'	//用NEWLINE替换'\n'
 
int main()
{
 
   int area;  
   
   area = LENGTH * WIDTH;
   cout << area;
   cout << NEWLINE;
   return 0;
}
```
```输出
50

```

## const 关键字

可以使用const前缀声明指定类型的常量。<br>`const type variable = value;`<br>需要注意的是，这里的常量是不能跟改的

```cpp
#include <iostream>
using namespace std;
 
int main()
{
   const int  LENGTH = 10;
   const int  WIDTH  = 5;
   const char NEWLINE = '\n';
   int area;  
   
   area = LENGTH * WIDTH;
   cout << area;
   cout << NEWLINE;
   return 0;
}
```

# 运算符

## 算术运算符

假设变量***A为10***，变量***B为20***，则：
| 运算符 | 描述 | 实例 |
| :-------: | :----: | :----: |
| + | 把两个数相加 | A + B 将得到30 |
| - | 从第一个操作数中减去第二个操作数 | A - B 将得到-10 |
| * | 把两个操作数相乘 | A * B 将得到200 |
| / | 分子除以分母 | B / A 将得到2 |
| % | 取模运算符，整除后的余数 | B % A 将得到0 |
| ++ | **自增运算符**，整数值增加1 | A++ 将得到11 |
| -- | **自减运算符**，整数值减少1 | A-- 将得到9 |

## 关系运算符

假设变量***A为10***，变量***B为20***，则：
|    运算符    |                             描述                             |       实例        |
| :----------: | :----------------------------------------------------------: | :---------------: |
|      ==      |        检查两个操作数的值是否相等，如果相等则条件为真        | (A == B) 不为真。 |
| !=(!和=组合) |       检查两个操作数的值是否相等，如果不相等则条件为真       |  (A != B) 为真。  |
|      >       |    检查左操作数的值是否大于右操作数的值，如果是则条件为真    | (A > B) 不为真。  |
|      <       |    检查左操作数的值是否小于右操作数的值，如果是则条件为真    |  (A < B) 为真。   |
| >=(>和=组合) | 检查左操作数的值是否大于或等于右操作数的值，如果是则条件为真 |  (A >= B) 不为真  |
| <=(<和=组合) | 检查左操作数的值是否小于或等于右操作数的值，如果实则条件为真 |   (A <= B) 为真   |

## 逻辑运算符

假设变量***A为1***(true)，变量***B为0**(false)，则：

| 运算符 |                             描述                             |       实例        |
| :----: | :----------------------------------------------------------: | :---------------: |
|   &&   |    称为逻辑与运算符。如果两个操作数都true，则条件为true。    | (A && B) 为false  |
|  \|\|  | 称为逻辑或运算符。如果两个操作数中有任意一个true，则条件为true。 | (A \|\| B) 为true |
|   !    | 称为逻辑非运算符。如果两个操作数中有任意一个true，则条件为true。 | !(A && B) 为true  |

## 位运算符

位运算符作用于为，并逐位执行操作。&、|和^的真值表如下：

|       p       |       q       |   p & q   |  P \| q   |   p ^ q   |
| :-----------: | :-----------: | :-------: | :-------: | :-------: |
|       0       |       0       |     0     |     0     |     0     |
|       0       |       1       |     0     |     1     |     1     |
|       1       |       1       |     1     |     1     |     0     |
|       1       |       0       |     0     |     1     |     1     |

下表显示c++支持的为运算符，假设A为60(0011 1100)，B为13(0000 1101)，则：

| 运算符 |                             描述                             |                             实例                             |
| :----: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|   &    | 按位与操作，按二进制位进行"与"运算。运算规则：<br>`0&0=0;    0&1=0;    1&0=0;     1&1=1;` |              (A & B) 将得到 12，即为 0000 1100               |
|   \|   | 按位或运算符，按二进制位进行"或"运算。运算规则：<br>`0|0=0;    0|1=1;    1|0=1;     1|1=1;` |              (A \| B) 将得到 61，即为 0011 1101              |
|   ^    | 异或运算符，按二进制位进行"异或"运算。运算规则：<br>`0^0=0;    0^1=1;    1^0=1;     1^1=0;` |              (A ^ B) 将得到 49，即为 0011 0001               |
|   ~    | 取反运算符，按二进制位进行"取反"运算。运算规则：<br>`~1=-2;    ~0=-1;` | (~A ) 将得到 -61，即为 1100 0011，一个有符号二进制数的补码形式。 |
|   <<   | 二进制左移运算符。将一个运算对象的各二进制位全部左移若干位（左边的二进制位丢弃，右边补0）。 |              A << 2 将得到 240，即为 1111 0000               |
|   >>   | 二进制右移运算符。将一个数的各二进制位全部右移若干位，正数左补0，负数左补1，右边丢弃。 |               A >> 2 将得到 15，即为 0000 1111               |

## 赋值运算符

| 运算符 |                             描述                             |              实例               |
| :----: | :----------------------------------------------------------: | :-----------------------------: |
|   =    |       简单的赋值运算符，把右边操作数的值赋给左边操作数       | C = A + B 将把 A + B 的值赋给 C |
|   +=   | 加且赋值运算符，把右边操作数加上左边操作数的结果赋值给左边操作数 |     C += A 相当于 C = C + A     |
|   -=   | 减且赋值运算符，把左边操作数减去右边操作数的结果赋值给左边操作数 |     C -= A 相当于 C = C - A     |
|   *=   | 乘且赋值运算符，把右边操作数乘以左边操作数的结果赋值给左边操作数 |     C *= A 相当于 C = C * A     |
|   /=   | 除且赋值运算符，把左边操作数除以右边操作数的结果赋值给左边操作数 |     C /= A 相当于 C = C / A     |
|   %=   |      求模且赋值运算符，求两个操作数的模赋值给左边操作数      |     C %= A 相当于 C = C % A     |
|  <<=   |                       左移且赋值运算符                       |    C <<= 2 等同于 C = C << 2    |
|  >>=   |                       右移且赋值运算符                       |    C >>= 2 等同于 C = C >> 2    |
|   &=   |                      按位与且赋值运算符                      |     C &= 2 等同于 C = C & 2     |
|   ^=   |                     按位异或且赋值运算符                     |     C ^= 2 等同于 C = C ^ 2     |
|  \|=   |                      按位或且赋值运算符                      |    C \|= 2 等同于 C = C \| 2    |

# 循环

## 循环类型

|                           循环类型                           |                             描述                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| [while 循环](https://www.runoob.com/cplusplus/cpp-while-loop.html) | 当给定条件为真时，重复语句或语句组。它会在执行循环主体之前测试条件。 |
| [for 循环](https://www.runoob.com/cplusplus/cpp-for-loop.html) |        多次执行一个语句序列，简化管理循环变量的代码。        |
| [do...while 循环](https://www.runoob.com/cplusplus/cpp-do-while-loop.html) |  除了它是在循环主体结尾测试条件外，其他与 while 语句类似。   |
| [嵌套循环](https://www.runoob.com/cplusplus/cpp-nested-loops.html) | 您可以在 while、for 或 do..while 循环内使用一个或多个循环。  |

## 循环语句控制

|                           控制语句                           |                             描述                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| [break 语句](https://www.runoob.com/cplusplus/cpp-break-statement.html) | 终止 **loop**（循环） 或 **switch**（多分支） 语句，程序流将继续执行紧接着 loop 或 switch 的下一条语句。 |
| [continue 语句](https://www.runoob.com/cplusplus/cpp-continue-statement.html) |      引起循环跳过主体的剩余部分，立即重新开始测试条件。      |
| [goto 语句](https://www.runoob.com/cplusplus/cpp-goto-statement.html) | 将控制转移到被标记的语句。但是不建议在程序中使用 goto 语句。 |

# 判断

## 判断语句

|                             语句                             |                             描述                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|   [if 语句](https://www.runoob.com/cplusplus/cpp-if.html)    |  一个 **if 语句** 由一个布尔表达式后跟一个或多个语句组成。   |
| [if...else 语句](https://www.runoob.com/cplusplus/cpp-if-else.html) | 一个 **if 语句** 后可跟一个可选的 **else 语句**，else 语句在布尔表达式为假时执行。 |
| [嵌套 if 语句](https://www.runoob.com/cplusplus/cpp-nested-if.html) | 您可以在一个 **if** 或 **else if** 语句内使用另一个 **if** 或 **else if** 语句。 |
| [switch 语句](https://www.runoob.com/cplusplus/cpp-switch.html) |   一个 **switch** 语句允许测试一个变量等于多个值时的情况。   |
| [嵌套 switch 语句](https://www.runoob.com/cplusplus/cpp-nested-switch.html) |  您可以在一个 **switch** 语句内使用另一个 **switch** 语句。  |

## ? : 运算符

可以用来替代 **if...else** 语句。它的一般形式如下：

```cpp
Exp1 ? Exp2 : Exp3;
```

如果 Exp1 为真，则计算 Exp2 的值，如果 Exp1 为假，则计算 Exp3 的值，计算后的值即为整式(?:)的值。

# c++ 日期 & 时间

为了使用日期和时间相关的函数和结构，需要在c++程序中引用[**`<ctime>`**](./cpp/ctime.md)头文件。

下面是 C/C++ 中关于日期和时间的重要函数。所有这些函数都是 C/C++ 标准库的组成部分。

| <a id="top">序号</a> |                         函数 | 描述                         |
| :--: | :--------------------------: | :-------------------------------: |
|  1   | [**`time()`**](#time)<br>`time_t time(time_t *time);` | 该函数返回系统的当前日历时间，自 1970 年 1 月 1 日以来经过的秒数。如果系统没有时间，则返回 -1。 |
|  2   |     [**`ctime()`**](#ctime)<br>`char *ctime(const time_t *time);`     |该返回一个表示当地时间的字符串指针，字符串形式 *day month year hours:minutes:seconds year\n\0*。 |
|  3   | [**`localtime()`**](#localtime)<br>`struct tm *localtime(const time_t *time);` |该函数返回一个指向表示本地时间的 **tm** 结构的指针。 |
|  4   | [**`clock()`**](#clock)<br>`clock_t clock(void);` | 该函数返回程序执行起（一般为程序的开头），处理器时钟所使用的时间。如果时间不可用，则返回 -1。 |
|  5   | [**`asctime()`**](#asctime)<br>`char * asctime ( const struct tm * time );` |该函数返回一个指向字符串的指针，字符串包含了 time 所指向结构中存储的信息，返回形式为：day month date hours:minutes:seconds year\n\0。 |
|  6   | [**`gmtime()`**](#gmtime)<br>`struct tm *gmtime(const time_t *time);` |该函数返回一个指向 time 的指针，time 为 tm 结构，用协调世界时（UTC）也被称为格林尼治标准时间（GMT）表示。 |
|  7   | [**`mktime()`**](#mktime)<br>`time_t mktime(struct tm *time);` |该函数返回日历时间，相当于 time 所指向结构中存储的时间。 |
|  8   | [**`difftime()`**](#difftime)<br>`double difftime ( time_t time2, time_t time1 );` |该函数返回 time1 和 time2 之间相差的秒数。 |
|  9   | [**`strftime()`**](#strftime)<br>`size_t strftime();` |该函数可用于格式化日期和时间为指定的格式。 |

## <a id="time">**time() 函数示例：**</a>
```c++
#include <iostream>
#include <ctime>

int main() {
    std::time_t result = std::time(nullptr);
    std::cout << "当前时间戳: " << result << std::endl;
    return 0;
}
```

[[返回]](#top)

## <a id="ctime">**ctime() 函数示例：**</a>
``` c++
    #include <iostream>
    #include <ctime>

    int main() {
        std::time_t rawtime;
        std::time(&rawtime);
        char* date = std::ctime(&rawtime);
        std::cout << "格式化后的本地时间：" << date;
        return 0;
}
```

[[返回]](#top)

## <a id="localtime">**localtime() 函数示例：**</a>
``` c++
#include <iostream>
#include <iomanip>
#include <ctime>

int main() {
    std::time_t rawtime;
    std::tm* timeinfo;
    std::time(&rawtime);
    timeinfo = std::localtime(&rawtime);
    std::cout << "本地时间: " << std::put_time(timeinfo, "%c %Z") << "\n";
    return 0;
}
```

[[返回]](#top)

## <a id="clock">**clock() 函数示例：**</a>
``` c++
#include <iostream>
#include <ctime>
#include <ratio>
#include <chrono>

int main() {
    std::clock_t start;
    double duration;
    start = std::clock();
    // 假设这里有一些处理工作
    for(long i=0; i<10000000L; i++);
    duration = (std::clock() - start) / (double) CLOCKS_PER_SEC;
    std::cout << "CPU 时间: " << duration << " 秒" << std::endl;
    return 0;
}
```

[[返回]](#top)

## <a id="asctime">asctime()</a>
和 asctime() 相关的功能已经在 [localtime](#localtime)() 示例中演示过了。
[[返回]](#top)

## <a id="gmtime">**gmtime() 函数示例：**</a>
``` c++
#include <iostream>
#include <iomanip>
#include <ctime>

int main() {
    std::time_t rawtime;
    std::tm* ptm;
    std::time(&rawtime);
    ptm = std::gmtime(&rawtime);
    std::cout << "当前UTC时间 -> " << std::put_time(ptm, "%c %Z") << "\n";
    return 0;
}
```

[[返回]](#top)

## <a id="mktime">**mktime() 函数示例：**</a>
``` c++
#include <iostream>
#include <ctime>

int main() {
    std::tm timeinfo = {};
    timeinfo.tm_year = 2025 - 1900; // 年份从1900开始计算
    timeinfo.tm_mon = 3;            // 月份从0开始计数，即3表示4月
    timeinfo.tm_mday = 1;
    timeinfo.tm_hour = 9;
    timeinfo.tm_min = 13;
    timeinfo.tm_sec = 0;
    timeinfo.tm_isdst = -1;

    std::time_t seconds = std::mktime(&timeinfo);
    std::cout << "时间戳: " << seconds << std::endl;
    return 0;
}
```

[[返回]](#top)

## <a id="difftime">**difftime() 函数示例：**</a>
``` c++
#include <iostream>
#include <ctime>

int main() {
    std::time_t start, finish;
    double diff;

    std::time(&start);
    // 假设这里有一些处理工作
    for(long i=0; i<10000000L; i++);
    std::time(&finish);

    diff = std::difftime(finish, start);
    std::cout << "时间差: " << diff << " 秒" << std::endl;

    return 0;
}
```

[[返回]](#top)

## <a id="strftime">**strftime() 函数示例：**</a>
``` c++
#include <iostream>
#include <ctime>

int main() {
    std::time_t rawtime;
    std::tm* timeinfo;
    char buffer[80];

    std::time(&rawtime);
    timeinfo = std::localtime(&rawtime);

    std::strftime(buffer, 80, "今天的日期和时间是: %Y-%m-%d %H:%M:%S", timeinfo);
    std::cout << buffer << std::endl;

    return 0;
}
```
[[返回]](#top)

# C++ 基本的输入输出

## 头文件

`<iostream>`（标准I/O）、`<fstream>`（文件）、`<iomanip>`（格式）、`<sstream>`（字符串流）

## 基础操作

* **输入**：`cin >> x;`（跳过空格）
* **输出**：`cout << x << endl;`
* **读整行**：`getline(cin, str);`（含空格）

## 格式控制

* 保留小数：`cout << fixed << setprecision(2) << 3.1415;` → `3.14`
* 宽度对齐：`cout << setw(5) << left << 42;` → `"42 "`

## 文件操作

```cpp
ofstream fout("data.txt");  // 写  
fout << "Hello";  
ifstream fin("data.txt");   // 读  
string s;  
getline(fin, s);  
```

## 字符串流

```cpp
istringstream iss("10 3.14");  
iss >> a >> b;  // a=10, b=3.14  
ostringstream oss;  
oss << "X=" << 5;  // "X=5"  
```

## 注意
1. `cin >>`后接`getline()`前用`cin.ignore();`
2. **二进制文件**：`ios::binary` + `read()/write()`
3. **错误检查**：`if (!cin) { ... }`

**核心：`<<` 输出，`>>` 输入 + 灵活控制流！**

# 数据结构

## 序列容器（Sequence Containers）

1. **`std::vector`**
	* **特性**：动态数组，支持快速随机访问，尾部操作高效。
	* **头文件**：`#include <vector>`
	* **代码示例**：
        ```
        vector<int> vec = {1, 2, 3};
        vec.push_back(4);       // 尾部插入
        vec.pop_back();         // 尾部删除
        cout << vec[0];         // 随机访问 O(1)
        ```
2. **`std::deque`**（双端队列）
	* **特性**：支持头部和尾部的高效插入/删除，随机访问稍慢于 `vector`。
	* **头文件**：`#include <deque>`
        ```
        deque<int> dq = {1, 2};
        dq.push_front(0);       // 头部插入
        dq.push_back(3);        // 尾部插入
        ```
3. **`std::list`**（双向链表）
	* **特性**：任意位置插入/删除高效，不支持随机访问。
	* **头文件**：`#include <list>`
     
        ```
        list<int> lst = {1, 3};
        lst.insert(++lst.begin(), 2);  // 在第二个位置插入2
        lst.erase(lst.begin());        // 删除第一个元素
        ```
4. **`std::forward_list`**（单向链表，C++11）
	* **特性**：更轻量的单向链表，内存占用更小。
	* **头文件**：`#include <forward_list>`
     
        ```
        forward_list<int> flst = {1, 2};
        flst.push_front(0);     // 仅支持头部插入
        ```
5. **`std::array`**（静态数组，C++11）
	* **特性**：固定大小数组，内存连续，替代原生数组。
	* **头文件**：`#include <array>`
        ```
        array<int, 3> arr = {1, 2, 3};
        cout << arr.size();     // 输出3
        ```

## 关联容器（Associative Containers）

1. **`std::set` / `std::multiset`**
    * **特性**：基于红黑树的有序集合，`set` 元素唯一，`multiset` 允许重复。
    * **头文件**：`#include <set>`
      ```
      set<int> s = {3, 1, 2};
      s.insert(4);            // 插入后自动排序 {1, 2, 3, 4}
      auto it = s.find(2);    // 查找 O(log n)
      ```

2. **`std::map` / `std::multimap`**
    * **特性**：键值对的有序容器，`map` 键唯一，`multimap` 允许重复键。
    * **头文件**：`#include <map>`
      ```
      map<string, int> m;
      m["apple"] = 5;         // 插入键值对
      m.emplace("banana", 3); // 原地构造键值对
      ```

## 无序关联容器（Unordered Containers，C++11）

1. **`std::unordered_set` / `std::unordered_multiset`**
    * **特性**：基于哈希表的无序集合，查找平均 O(1)，最坏 O(n)。
    * **头文件**：`#include <unordered_set>`
      ```
      unordered_set<int> us = {3, 1, 2};
      us.insert(4);           // 插入后无序
      ```

2. **`std::unordered_map` / `std::unordered_multimap`**
    * **特性**：基于哈希表的键值对容器，键无序。
    * **头文件**：`#include <unordered_map>`
      ```
      unordered_map<string, int> umap;
      umap["apple"] = 5;      // 插入键值对
      ```

## 容器适配器（Container Adaptors）

1. **`std::stack`**
   * **底层容器**：默认 `deque`，可切换为 `vector` 或 `list`。
   * **头文件**：`#include <stack>`
     ```
     stack<int> stk;
     stk.push(1);
     stk.pop();
     ```
2. **`std::queue`**
   * **底层容器**：默认 `deque`，可切换为 `list`。
   * **头文件**：`#include <queue>`
     ```
     queue<int> q;
     q.push(1);
     q.pop();
     ```
3. **`std::priority_queue`**
   * **特性**：大顶堆（默认），可配置为小顶堆。
   * **头文件**：`#include <queue>`
     ```
     priority_queue<int> maxHeap; // 大顶堆
     priority_queue<int, vector<int>, greater<int>> minHeap; // 小顶堆
     ```


## 其他重要容器

1. **`std::string`**
   * **特性**：动态字符序列，支持字符串操作。
   * **头文件**：`#include <string>`
     ```
     string str = "hello";
     str += " world";
     ```
2. **`std::bitset`**
   * **特性**：固定大小的位序列，支持位操作。
   * **头文件**：`#include <bitset>`

     ```
     bitset<8> bits("1010"); // 8位二进制
     bits.set(3);            // 设置第3位为1
     ```


## 性能对比

| 容器            | 插入/删除            | 查找      | 随机访问 |
| :-------------- | :------------------- | :-------- | :------- |
| `vector`        | 尾部 O(1)，中间 O(n) | O(n)      | O(1)     |
| `list`          | 任意位置 O(1)        | O(n)      | 不支持   |
| `map`/`set`     | O(log n)             | O(log n)  | 不支持   |
| `unordered_map` | 平均 O(1)，最坏 O(n) | 平均 O(1) | 不支持   |

## 使用建议

1. **快速随机访问** → `vector` 或 `array`
2. **高频头部/尾部操作** → `deque`
3. **频繁任意位置插入/删除** → `list` 或 `forward_list`
4. **有序数据管理** → `map`/`set`
5. **快速查找（无序）** → `unordered_map`/`unordered_set`

# 类 & 对象

## 类定义

定义一个类需要使用关键字 **class**，然后指定类的名称，并类的主体是包含在一对花括号中，主体包含类的成员变量和成员函数。<br>定义一个类，本质上是定义一个数据类型的蓝图，它定义了类的对象包括了什么，以及可以在这个对象上执行哪些操作。

![img](https://www.runoob.com/wp-content/uploads/2015/05/cpp-classes-objects-2020-12-10-11.png)

```c++
class Box
{
   public:
      double length;   // 盒子的长度
      double breadth;  // 盒子的宽度
      double height;   // 盒子的高度
};
```

## 定义对象

```c++
Box Box1;          // 声明 Box1，类型为 Box
Box Box2;          // 声明 Box2，类型为 Box
```

## 类访问修饰符

数据封装是面向对象编程的一个重要特点，它防止函数直接访问类类型的内部成员。类成员的访问限制是通过在类主体内部对各个区域标记 **public、private、protected** 来指定的。关键字 **public、private、protected** 称为访问修饰符。

一个类可以有多个 public、protected 或 private 标记区域。每个标记区域在下一个标记区域开始之前或者在遇到类主体结束右括号之前都是有效的。成员和类的默认访问修饰符是 private。

```c++
class Base {
public:   	// 公有成员    
protected:  // 受保护成员    
private:    // 私有成员
};
```

公有（==public==）成员:**公有**成员在程序中类的外部是可访问的。您可以不使用任何成员函数来设置和获取公有变量的值

私有（==private==）成员:**私有**成员变量或函数在类的外部是不可访问的，甚至是不可查看的。只有类和友元函数可以访问私有成员。默认情况下，类的所有成员都是私有的。

受保护（==protected==）成员:**受保护**成员变量或函数与私有成员十分相似，但有一点不同，（受保护）成员在派生类（即子类）中是可访问的。

