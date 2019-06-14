在设计上把spring划为核心、组件和应用三个基本层次。

spring的价值：

​	spring是一个非侵入性框架，其目标是使应用程序代码对框架的依赖最小化，应用代码可以在没有spring或者其他容器的情况下运行。

​	spring提供了一个一致的编程模型，使应用直接使用POJO开发，从而可以与运行环境隔离开来。

​	Spring推动应用的设计风格向面向对象及面向接口的转变，提高了代码的重用。

IoC容器和依赖反转模式：

​	依赖对象的获得就被反转了

​	控制反转是关于一个对象如何获取它所依赖的对象的引用

所谓IoC，对于spring框架来说，就是由spring来负责控制对象的生命周期和对象间的关系

##### 工厂模式也可以管理实例的初始化呀，为什么一定要使用Spring呢？

​	*其实本质上还是因为IOC是通过反射机制来实现的。当我们的需求出现变动时，工厂模式会需要进行相应的变化。但是IOC的反射机制允许我们不重新编译代码，因为它的对象都是动态生成的。*

#### spring是什么：

​	开源框架，为了解决企业应用开开发的复杂性而创建的，使用基本的JavaBean来完成以前只能由EJB完成的事情。容器框架，

##### spring核心：

​	控制反转（Ioc）和面向切面编程。

##### spring能干什么：

​	方便解耦，简化开发。方便对程序进行拦截、监控等。可以对事务声明。

#### mvc模式

​	Model（模型）、View（视图）、Control（控制器）

​	MVC设计模式的任务是将包含业务数据的模块与显示模块的视图解耦。在模型和视图之间引入重定向层可以解决问题。此重定向层是控制器，控制器将接收请求，执行更新模型的操作，然后通知视图关于模型更改的消息。

​	三层架构：展现层+应用层+数据访问层

##### MVC和三层架构的联系：

​	但是实际上MVC只存在三层架构的展现层，M实际上是数
据模型，是包含数据的对象。在Spring  MVC里，有一个专门
的类叫Model，用来和V之间的数据交互、传值；V指的是视图
页面，包含JSP、freeMarker、Velocity、Thymeleaf、Tile等；C
当然就是控制器（Spring MVC的注解@Controller的类）。

​	而三层架构是整个应用的架构，是由Spring框架负责管理
的。一般项目结构中都有Service层、DAO层，这两个反馈在
应用层和数据访问层	

​	

​	

#### spring mvc是什么:

​	是spring下的子项目，是一种基于java的实现了Web Mvc设计模式框架，是Web层的框架，spring是业务层的框架，Hibernate&Mybatis是持久层的框架。

##### spring mvc能干什么：

​	将Web层进行指责解耦，简便开发

![springmvc的核心](images\springmvc.jpg)

​	



##### Spring MVC的请求流程：

​	第一步：发起请求到前端控制器(DispatcherServlet)

​	第二步：前端控制器请求HandlerMapping查找Handler可以根据xml配置、注解进行查找

​	第三步：处理器映射器HandlerMapping向前端控制器返回Handler

​	第四步：前端控制器调用处理器适配器去执行Handler

​	第五步：处理器适配器去执行Handler

​	第六步：Handler执行完成给适配器返回ModelAndView

​	第七步：处理器适配器向前端控制器返回ModelAndView。ModelAndView是springmvc框架的一个底层对			    象，包括 Model和view

​	第八步：前端控制器请求视图解析器去进行视图解析，根据逻辑视图名解析成真正的视图(jsp)

​	第九步：视图解析器向前端控制器返回View

​	第十步：前端控制器进行视图渲染。视图渲染将模型数据(在ModelAndView对象中)填充到request域

​	第十一步：前端控制器向用户响应结果

##### 什么是Spring的事务管理？

​	原子性(A)：事务是最小单位，不可再分
​	一致性(C)：事务要求所有的DML语句操作的时候，必须保证同时成功或者同时失败
​	隔离性(I)：事务A和事务B之间具有隔离性
​	持久性(D)：是事务的保证，事务终结的标志(内存的数据持久到硬盘文件中)	

​	PROPAGATION_REQUIRED：支持前事务，如果当前没有事务，就新建一个事务。这是最常见的选择。（默认）

​	spring中一共定义了七种传播机制。

​	mysql默认的事务隔离级别为repeatable-read（可重复读）

​	ISOLATION_DEFAULT: 默认,这是一个PlatfromTransactionManager默认的隔离级别，使用数据库默认的事务隔离级别。

​	声明式事务（基于AOP）有助于用户将操作与事务规则进行解耦

​	spring提供一致的事务。

​	



##### 什么是AOP，为什么使用AOP ?

​	AOP把软件系统分为两个部分：**核心关注点**和**横切关注点**。

​	业务处理的主要流程是核心关注点，与之关系不大的部分是横切关注点

​	AOP全称：Aspect-Oriented Programming，面向切面编程。就是把可重用的功能提取出来，然后将这些通用功能在合适的时候织入到应用程序中，比如事务管理、权限控制、日志记录、性能统计等。  A<u>OP并没有帮助我们解决任何新的问题，它只是提供了一种更好的办法，能够用更少的工作量来解决现有的一些问题，使得系统更加健壮，可维护性更好。</u>

​	spring创建代理的规则:

​		1.默认使用Java动态代理来创建Aop代理

​		2.当需要代理的类不是代理接口的时候，spring会切换使用CGLIB，也可强制使用CGLIB.

​	AOP核心概念：

​	1、横切关注点

对哪些方法进行拦截，拦截后怎么处理，这些关注点称之为横切关注点

2、切面（aspect）

类是对物体特征的抽象，切面就是对横切关注点的抽象

3、连接点（joinpoint）

被拦截到的点，因为Spring只支持方法类型的连接点，所以在Spring中连接点指的就是被拦截到的方法，实际上连接点还可以是字段或者构造器

4、切入点（pointcut）

对连接点进行拦截的定义

5、通知（advice）

所谓通知指的就是指拦截到连接点之后要执行的代码，通知分为前置、后置、异常、最终、环绕通知五类

6、目标对象

代理的目标对象

7、织入（weave）

将切面应用到目标对象并导致代理对象创建的过程

8、引入（introduction）

在不修改代码的前提下，引入可以在**运行期**为类动态地添加一些方法或字段



#### Spring的加载方式：







​	



​	



































#### spring中设计模式

1.简单工厂：

​	简单工厂模式的实质是由一个工厂类根据传入的参数，动态决定应该创建哪一个产品类。 
spring中的BeanFactory就是简单工厂模式的体现，根据传入一个唯一的标识来获得bean对象，但是否是在传入参数后创建还是传入参数前创建这个要根据具体情况来定。

2. 工厂方法：

   定义一个用于创建对象的接口，让子类决定实例化哪一个类。Factory Method使一个类的实例化延迟到其子类。 spring中的FactoryBean就是典型的工厂方法模式。如下图：

3. 单例：

   ​	保证一个类仅有一个实例，并提供一个访问它的全局访问点。 
   spring中的单例模式完成了后半句话，即提供了全局的访问点BeanFactory。但没有从构造器级别去控制单例，这是因为spring管理的是是任意的java对象。

4. 适配器（Adapter）

   ​	将一个类的接口转换成客户希望的另外一个接口。Adapter模式使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。 

   ​	由于Advisor链需要的是MethodInterceptor对象，所以每一个Advisor中的Advice都要适配成对应的MethodInterceptor对象。 

5. 包装器：（Decorator）

   动态地给一个对象添加一些额外的职责。就增加功能来说，Decorator模式相比生成子类更为灵活。 

   spring中用到的包装器模式在类名上有两种表现：一种是类名中含有Wrapper，另一种是类名中含有Decorator。基本上都是动态地给一个对象添加一些额外的职责。 

6. 代理：（Proxy）

   为其他对象提供一种代理以控制对这个对象的访问。 
   从结构上来看和Decorator模式类似，但Proxy是控制，更像是一种对功能的限制，而Decorator是增加职责。 

7. 观察者:（Observer）

   定义对象间的一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新。 

   spring中Observer模式常用的地方是listener的实现。如ApplicationListener。

8. 策略：（Strategy）

   定义一系列的算法，把它们一个个封装起来，并且使它们可相互替换。本模式使得算法可独立于使用它的客户而变化。 
   spring中在实例化对象的时候用到Strategy模式，

9. 模板：（Template）













UTC:世界协调时间



GMT:格林威治标准时间



CST:  

​	CST却同时可以代表如下 4 个不同的时区： 

​	Central Standard Time (USA) UT-6:00 

​	Central Standard Time (Australia) UT+9:30 

​	China Standard Time UT+8:00 

​	Cuba Standard Time UT-4:00 


​	可见，CST可以同时表示美国，澳大利亚，中国，古巴四个国家的标准时间。  

#### BeanFactory和FactoryBean的区别：

​	BeanFactory工厂类接口，用户管理bean的一个工厂，BeanFactory是IOC容器的核心接口，它的职责包括：实例化、定位、配置应用程序中的对象及建立这些对象间的依赖。

​	FactoryBean表示它是一个Bean，不同于普通Bean的是，它实现了FactoryBean接口的Bean，根据该Bean的ID从BeanFactory中获取的实际上是FactoryBean的getObject()返回的对象，而不是FactoryBean本身，如果要获取FactoryBean对象，请在id前加上一个‘&’符号来获取。



#### Ioc容器中Bean生命周期:

​	1.Bean实例的创建

​	2.为Bean实列设置属性

​	3.条用Bean的初始化方法

​	4.应用可以通过Ioc使用Bean

​	5.当容器关闭时，条用Bean的销毁方法

​	

![](images\IOC接口图.jpg)

​	容器的初始化，refresh相当于容器的初始化函数，在初始化过程中，比较重要的部分是对BeanDefinition信息的载入和注入工作。由BeanDefinitionReader来完成Bean定义信息的读取、解析和Ioc容器内部BeanDefinition的建立。在客户第一次向Ioc容器请求Bean时，Ioc容器对相关Bean依赖关系进行注入。这时通过getBean来取得Bean，这些Bean不是简单的Java对象，而是已经包含了对象之间依赖关系的Bean。



### 								

WebApplicationContext     ApplicationContext

![](images\DispatcherServlet.jpg)





















