# 类模板与模板类

## 类模板

**类模板**：允许用户为类定义一种模式，使得类中的某些数据成员、成员函数的擦书、成员函数的返回值，能够取任意类型。

如果一个类中数据成员的数据类型不能确定，或者某个成员函数的参数或返回值的类型不能确定，就必须将此类声明为模板，其存在不是代表一个具体的、实际的类，而是代表任意类型的类。

- 定义类模板：

            template <class Type>
            class foo
            {
            }
            
- 通用数据类型的成员或成员函数类型    

            Type ml;
            Type test( Type a);
            
- 在类定义外定义成员函数时，若成员函数中有模板参数存在，则需要在前面进行模板声明

            template<class Type>
            void foo<Type>::test( Type a) {...};
      
- 可从类模板派生出新的类，既可派生类模板，也可派生非模板类（已经具体化类型）。

    - 从类模板派生新类模板
    
             template <class Type>
             class base
             {
             };
             
             template <class Type>
             class derive:public base<T>
             {
             };
             
        与一般类派生定义相似，只是在指出其基类时要加上模板参数，即base<T>
        
      - 从类模板派生非类模板，作为非模板类的基类，其必须是类模板实例化后的模板类，且不需要在派生类前声明template<class>
      
                template <class Type>
                class base
                {
                };
                
                class derive: public base<int>
                {
                };
               
         在定义derive类时，base已实例化成int型的模板类。          
      
### 模板类

**模板类**是类模板实例化后的具体对象。例如Stack<type>为类模板；而Stack<int>指定了具体类型，则表示实例化
            
      