## 指针与函数

---

#### 0x1 数据交换函数

编写程序互换两个整形数据类型对象的值，要求使用函数实现数据对象值的互换

```cpp
#include <iostream>
//#define NDEBUG 这是一个宏调用如果没有头程序中的 ifndef NDEBUG endif 就会输出，便于我们调试
using namespace std;

void Swap(int *x , int * y);

int main()
{

 int m = 10, n=20;
 #ifndef NDEBUG
  cout << "main (before swapped): m = " << m << " n= " << n << endl;
 #endif 
 Swap(&m , &n);
 #ifndef NDEBUG
  cout << "main (after swapped): m = " << m << " n= " << n << endl;
 #endif
 return 0;
}


void Swap(int *x , int *y)
{
  int t;
  if( !x || !y )
  {
   cout << "Swap: Parameter(s) illegal." << endl;
  // exit(1);
  }

  #ifndef NDEBUG
   cout << "Swap (before swapped): *x = " << *x << "; *y = " << *y << endl;
  #endif
   t = *x;
   *x = *y;
   *y = t;
  #ifndef NDEBUG
   cout << "Swap (after swapped): *x = " << *x << "; *y = " << *y << endl;
  #endif

}
```

只实现功能版本

```cpp
#include <iostream>
#define NDEBUG
using namespace std;

void Swap(int *x , int * y);

int main()
{

 int m = 10, n=20;
 Swap(&m , &n);
 return 0;
}


void Swap(int *x , int *y)
{
  int t;
  if( !x || !y )
  {
   cout << "Swap: Parameter(s) illegal." << endl;
  // exit(1);
  }

   t = *x;
   *x = *y;
   *y = t;
}
```



