## 指针

#### 0x1:数据对象的地址与值

地址：数据对象的存储位置在计算机中的编号

值： 在该位置处存储的内容

地址与值是辨证统一的关系，不能分割淡出来看

---

#### 0x2 指针的定义与使用

##### 格式：**目标数据对象类型 \* 指针变量名称**

例一：定义p为指向整数的指针：

```cpp
 int * p ；
```

例二：定义p为指向结构体类型的指针：

```cpp
struct POINT（int x ，y ；）；
POINT * p ；
```

##### 多个指针变量的定义

例三：

```cpp
int *p ，* q ；
```

两个都要 \*  不要忘记 ，为了避免麻烦我们也可以使用 typedef

例四：

```cpp
typedef int * PINT  ;
PINT p ,q ;
```

这样就等价于上边的 例三

---

#### 0X3 指针变量的存储布局

仅定义指针变量，未初始化

```
int * p;
```

定义指针变了，并使其指向某个目标变量

```cpp
int n = 10 ;
int * p = &n; //&获取地址
```

##### 指针指向数组的0号元 即首元素

```cpp
 int a[8] = {1,2,3,4,5,6,7,8};
 int * p = a //这里a 本身就是个地址 0x 1111111
```

| p | a\[0\] | a\[1\] ........\[a7\] |
| :--- | :---: | :---: |
| 0x 00130000000 | 0x 00130000000 | 0x 0013 111111...xxx |

---

#### 0x4 指针变量的赋值与操作

指针变量可以像普通变量一样赋值

示例一：

```cpp
int n= 10 ; 
int * p = &n ;
int * q ;
q = p //q 和 p 最终都指向n 的地址
```

##### 取址操作符  &   引领操作符

取址操作符：获取数据对象的地址，可讲结果赋值给指针变量 **  ‘&’  **

引领操作符 : 获取指针所指向的目标数据对象

示例一：

```cpp
#include <iostream>

using namespace std;

int main()
{
 int m ,n = 10;
 cout << "n is " <<  n << endl;
 cout << "m is " <<  m << endl;
 int * p = &n;
 m = * p;
 cout << "m is " <<  m << endl;
 *p = 1;
 cout << "n is " <<  n << endl;
 cout << "m is " <<  m << endl;
}
```

输出如下：

```cpp
n is 10
m is 0
m is 10
n is 1
m is 10
//不明白可以自己加cout 把 m n  的地址都打印出来逐一观察
```

#### ![](/assets/zhizhen.PNG)0x5整数互换程序：

编写程序，使用指针互换两个整数的值

```cpp
#include <iostream>

using namespace std;

int main()
{
 int m = 10 , n =20 ,t;
 cout << "m is " << m <<endl;
 cout << "n is " << n <<endl;
 int * p = &m ; 
 int * q = &n ;
 cout << "*q is number " << * q << endl;
 cout << "q is addr " << q << endl;
 t = * p ;//t = 10 (m)
 *p = * q ; //p = q.values 20
 *q = t;
 cout << "m is " << m <<endl;
 cout << "n is " << n <<endl;
}
```

输出如下：

```cpp
m is 10
n is 20
*q is number 20
q is addr 0x7fff39a1cdd0
m is 20
n is 10
```

#### 指针的意义与应用：

* 作为函数通信的一种手段

  ```markdown
      使用指针作为函数参数，不仅可以提高参数传递效率，还可以将该参数作为函数输出集的一员，带回结果
  ```

* 作为构造复杂数据结构的手段

  ```markdown
       使用指针构造数据对象之间的关联，形成复杂数据结构
  ```

* 作为动态内存分配和管理的手段

  ```markdown
       在程序执行期间动态构造数据对象之间的关联
  ```

* 作为执行特定程序代码的手段

  ```markdown
       使用指针指向特定代码段，执行未来才能实现的函数
  ```



