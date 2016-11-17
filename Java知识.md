+ 声明ViewHolder内部类时，为什么建议使用static关键字

主要是理解静态内部类和非静态内部类的区别，非静态内部类会隐式地持有外部类的引用，就像在Activity中加入自定义的adapter,在adapter中可以随意访问外部Activity的方法。当你将内部类定义为static时，此内部类将无法访问外部类的实例方法，因为静态内部类不会持有外部类的引用。所以将ViewHolder声明为静态内部类，可以将ViewHolder和外部类解引用。当内部类无需使用外部类的资源时，最好把内部类定义成静态。

带...的可变参数可以


* volatile 与synchronized的区别

首先我们要先意识到有这样的现象,编译器为了加快程序运行的速度,对一些变量的写操作会先在寄存器或者是CPU缓存上进行,最后才写入内存.而在这个过程,变量的新值对其他线程是不可见的.而volatile的作用就是使它修饰的变量的读写操作都必须在内存中进行!

1. volatile本质是在告诉jvm当前变量在寄存器中的值是不确定的,需要从主存中读取,synchronized则是锁定当前变量,只有当前线程可以访问该变量,其他线程被阻塞住.
2. volatile仅能使用在变量级别,synchronized则可以使用在变量,方法.
3. volatile仅能实现变量的修改可见性,但不具备原子特性,而synchronized则可以保证变量的修改可见性和原子性.
4. volatile不会造成线程的阻塞,而synchronized可能会造成线程的阻塞.
5. volatile标记的变量不会被编译器优化,而synchronized标记的变量可以被编译器优化.


###Double.parseDouble("")的原理
1. 判断length是否为0，否则跑出异常
2. 判断是否为NaN或者Infinity，返回对应的值
3. 判断是否为16进制，返回对应的值
4. 判断是否为特殊值
5. 调用native的paseDbImpl,返回double值

###Android中ClassLoader和java中有什么关系和区别
Android中的ClassLoader与Java有些不同，Android中ClassLoader加载的是dex文件，而Java中加载的是jar文件.相同的是两者都采用了双亲委派模型.


