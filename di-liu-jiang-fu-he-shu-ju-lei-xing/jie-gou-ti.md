结构体与数组最大的差别： 不同类型数据对象构成的集合

#### 结构体类型示例：

示例一：日期结构体

```cpp
      struct DATE
      {
        int year;
        int month;
        int day;
      };
```

示例二：复数结构体

```cpp
     struct COMPLEX
     {
      double real;
      double imag;
     };
```

#### 结构体类型的声明：

仅仅引入结构体类型的名称，而没有给出具体定义，其具体定义在其他头文件或者本文件后续位置

```cpp
   struct   COMPLEX；
```

#### 实例--表示学生信息

成员：整数类型学生学号id，字符串类型的姓名name  ， 性别 （单独定义的枚举类型）gender ， 年龄 age ， 字符串类型的地址 addr

```cpp
enum GENDER {FEMALE , MALE};
struct STUDENT
 {
  int id;
  STRING name;
  GENDER  gender;
  int age;
  STRING addr;
 };
```

#### 结构体的存储：

各成员的存储空间一般连续，不像数组一定连续

##### 特殊情况

因为不同硬件和编译器的原因，不同类型的成员可能会按照字（两个  
字节）或双字（四个字节）对齐后存放

使用 sizeof 获得结构体类型量占用空间大小（以字节为单位），下  
述两种使用方式均可

```cpp
sizeof date;     sizeof (date);
```

#### 操作结构体：

* ##### 初始化

        示例一：

```cpp
  DATE  date = {2008，8，8}；
```

* ##### 赋值

         与数组不用，结构体可以直接赋值（数组必须逐一赋值通过for循环），拷贝过程为逐成员一一复制

        示例一：

```cpp
   DATE new_date ； new_date = date;
```

* ##### 访问

     使用点 ‘.’   号 操作符解析结构体量的某个特定成员
     示例一：

```cpp
   DATE date ； date.year = 2008 ; date.month = 8 ; date.day = 8;
```

             嵌套结构体成员的访问 ： 可以使用连续点号逐层解析

             示例二：

```cpp
    struct FRIEND (int id ； STRING name ； DATE birthday；);
    FRIEND friend；
    friend.birthday.year;
```

             复杂结构体成员的访问：严格按照语法规范进行

              示例三：

```cpp
    FREIND friends[4];
    friends[0].birthday.year = 1988;
```

#### 结构体与函数：

     编写函数，使用结构体类型存储日期，并返回该日在该年的第几天信息，具体天数从 1 开始计数，例如 2016 年 1 月 20 日返回 20，2 月 1 日返回 32

```cpp
  unsigned int GetDateCount (DATE date)
  {
    static unsigned int days_of_months[13] = 
    { 0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
    unsigned int i, date_id = 0;
     for( i = 1; i < date.month; i++ )
      date_id += days_of_months[i];
    date_id += date.day;
    if( date.month > 2 && IsLeap(date.year) )//ISleap函数自己，谓词函数判断是否是闰年
       date_id++;
    return date_id;
  }
```







