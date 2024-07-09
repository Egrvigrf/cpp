# 面向对象

## 对象
包含属性和行为，多个对象之间存在联系。

## 特性
1. 抽象
- 归纳共性
2. 封装
- 对象之间相互独立，互不干扰
- 隐蔽内部细节，只留下接口进行交互
3. 继承
- 提高代码重用性
4. 多态
- 不同对象对相同消息的响应不同

## 类的声明

类似于结构体的声明
```c++
struct Student {
    string name;
    int num;
};
```

```c++
class Student {
private:
    
public:
    void display();
};
```

定义对象(C++方式)
`Student stu1,stu2;`

## 成员函数

在类外定义成员函数要在名称前加上**作用域限符**(避免二义性)
`void Student::display() {...}`

类成员函数的存储
代码部分公用，数据部分单独存储（节省空间）
输出类对象占用的字节数
`cout<<sizeof(Student)<<endl;`

对象成员的引用

```c++
class Time {
public:
int hour,minite;
};
Time t1,*p;
p = &t1;
```
三种形式等价
`p->name` `(*p).name` `t1.name`  

引用访问(t2是t1的别名)
`Time &t2 = t1;`
`cout<<t2.hour<<endl`

### 构造函数
- 特殊的成员函数
- 名字与类名相同
- 在对象被创建时调用

可使用参数列表初始化
`Box::Box(int l, int w, int h) : length(l), width(w), hight(h) {...}`

### 析构函数
- 特殊的成员函数
- 名字为类名前加上~
- 在对象生命周期结束时执行
- 不能被重载，没有参数，不能定义类型，没有返回值

函数体推荐使用delete删除对象用new开辟的空间，因为销毁对象啊时系统会回收对象占用的空间而不会回收使用new开辟的空间

## this指针
- 指向当前对象的地址
- 隐式调用

## 静态成员
- 该类的所有对象共享同一个静态成员

在类外初始化,不能使用参数列表初始化
`int Box::height = 10;`

## 静态成员函数
- 和非静态成员函数的区别在于没有this指针
- 只能用于访问静态成员数据，不能访问非静态成员数据

## 友元函数
- 必须在类的定义中说明
- 可以访问类的所有成员