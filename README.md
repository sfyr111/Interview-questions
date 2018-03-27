# Interview-questions（每日一题）

#### 那些操作会造成内存泄漏?
- 内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。垃圾回收器定期扫描对象,并计算引用了每个对象的其他对象的数量。如果一个对象的引用数量为0(没有其他对象引引用过该对象),或对该对象的惟一引用是循环的,那么该对象的内存即可回收。

- settimeout的第一个参数使用字符串而非函数的话,会引发内存泄漏。
闭包、控制台日志、循环(在两个对象彼此引用且彼此保留时,就会产生一个循环)
</br></br></br>

#### Js垃圾回收方法？

- 标记清除（mark and sweep）
  这是js最常见的垃圾回收方式，当变量进入执行环境的时候，比如函数中声明一个变量，垃圾回收器将其标记为“进入环境”，当变量离开环境的时候（函数执行结束）将其标记为“离开环境”。
  垃圾回收器会在运行的时候给存储在内存中的所有变量加上标记，然后去掉环境中的变量以及被环境中变量所引用的变量（闭包），在这些完成之后仍然存在标记的就是要删除的变量。
  
 - 引用计数（reference counting）
   在低版本IE中经常出现内存泄漏，很多时候就是因为采用引用技术的方式进行垃圾回收。
   引用计数的策略是跟踪记录每个值被引用的次数，当声明一个变量并将一个引用类型赋值给该变量的时候这个值的引用次数+1，如果该变量的值变成了另一个，则这个值的引用次数-1，当引用次数为0的时候就回收。
</br></br></br>

#### 堆(heap)、栈(stack)的区别？
- 堆栈存在意义
  为了使程序运行时占用的内存最小。
  
- 堆（  引用数据类型（对象、数组、函数）保存在堆 ）
  动态分配内存，大小不定也不会自动释放。
- 栈（  基本数据类型保存在栈。 ）
  由编译器自动分配内存空间、有系统自动释放，存放函数的参数值，局部变量的值等。
</br></br></br>
  
#### js继承方式及优缺点
- 原型链实现继承
优点：
  非常简便的实现了多重继承的关系；
  能够确定原型和实例之间的关系；
缺点：
  创建子类型实例时，无法向父类型传递参数，尤其是多重继承时，弊端非常明显；
  所有的实例会共享通过原型链继承的属性，在一个实例中改变了，会在另一个实例中反映出来；
  不能使用字面量添加新方法，会使继承关系中断（会重写constructor属性）。

- 构造函数实现继承
 优点：
   通过使用call可以在调用的时候向父类型传递参数。
 缺点：
   仅仅借用构造函数，方法都在构造函数中定义，就无法实现函数复用；
   通过借用构造函数，在父类型原型中定义的方法也无法通过原型链暴露给子类型；

- 组合继承
  组合继承就是将前面两种方法组合到一起。
  原理是通过原型链实现对原型属性和方法的继承，而通过构造函数实现对实例属性的继承。这样，既保证原型上定义的属性和方法可以共享，又保证每个实例都有自己的属性。
  优点：
  组合继承避免了原型继承和借用构造函数继承的缺点，融合了他们的优点，是目前最常用的继承方式。
 
- 原型式继承
  （省略，自己去了解）
    
- 寄生式继承
  （省略，自己去了解）

- 寄生组合式继承
  （省略，自己去了解）
  
ps：主要记住原型链继承、构造函数继承和他们相结合的组合式继承。

  
