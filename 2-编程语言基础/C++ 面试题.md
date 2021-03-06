# C++ 面试题

tags: c++

---



[TOC]



## 关键字

### 1. const

- 修饰变量：该变量不能被改变

- 修饰指针： 

  - 指针常量： 指针本身是常量

    ```
    TYPE* const pContent;
    ```

  - 指向常量的指针：指针所指向的内容是常量

    ```
    const TYPE *pContent;
    ```

- 修饰引用： 常量引用，常用于形参类型，即避免了拷贝，又避免了函数对值的修改；表示函数内引用所指的内容不能改

  ```
  void function4(const int& Var);
  ```

- 修饰成员函数：该成员函数内不能修改类的任何成员变量

  ```
  Type func_name() const;
  ```

### 2. static

- 修饰普通变量：修改变量的存储区域和生命周期，使变量存储在静态区，在 main 函数运行前就分配了空间，如果有初始值就用初始值初始化它，如果没有初始值系统用默认值初始化它。
- 修饰普通函数：表明函数的作用范围，仅在定义该函数的文件内才能使用。
- 修饰成员变量：所有的对象只保存一个该变量，而且不需要生成对象就可以访问该成员。
- 修饰成员函数：使得不需要生成对象就可以访问该函数，但是在 static 函数内不能访问非静态成员。

### 3. this 指针

 

### 4. inline 内联函数

- 函数调用过程： 函数调用执行时，首先要在栈中为形参和局部变量分配存储空间，然后还要将实参的值复制给形参，接下来还要将函数的返回地址(该地址指明了函数执行结束后，程序应该回到哪里继续执行) 放入栈中，最后才跳转到函数内部执行。 这个过程很耗费资源。

一般情况下函数调用的开销可以忽略，但如果一个函数内部只有少数几条语句，执行时间本来就非常短，那么这个函数调用产生的额外开销和函数执行时间比，就不能忽略了，如果该函数被执行了上万次，那么这部分函数调用应该被优化。

- 通过在函数前加上 inline 关键字，就能很好的解决函数调用开销的问题

**内联函数与普通函数的区别**： 当编译器处理调用内联函数的语句时，不会将该语句编译成函数调用的指令，而是直接将整个函数体的代码插入调用语句出。

**内联函数的特点：**

- 相当于把内联函数中的内容复制到了调用该函数的地方（编译时完成），加速了程序的运行，但是消耗了空间
- 不能包含循环、递归、switch 等复杂操作；内联只是对编译器的**建议**，是否内联取决于编译器
- 定义在类中的函数，除了虚函数，都会自动隐式地当成内联函数。但这不代表虚函数无法内联 
- 内联函数通常定义在头文件中
  - inline 函数对编译器而言必须是可见的，以便它能够在调用点展开该函数。
  - 如果定义在 cpp 文件中，那么在每个调用该内联函数的文件内都要再重新定义一次，且定义必须一致
  - inline 函数允许多次定义

### 5. volatile



### 6. struct， class

```
typedef struct Student { 
    int age; 
} Stu;
```

**struct 与 class 区别：**

- 本质的区别在于默认的访问控制权限
  - 默认的继承访问权限—— struct 是 public，class 是 private
  - 默认的成员访问权限—— struct 是 public，class 是 private

### 7. union



### 8. enum



