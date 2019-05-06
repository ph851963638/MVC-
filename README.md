# MVC-

ModelAndView  视图及数据
创建  

ModelAndView mav=new ModelAndView()   无参构造方法 对象
if（resut）{
mav.setviewname("名称");  //跳转页面//web-inf/jsp
}else{
//session.setAttribute("msg","登录信息有误")；
 mav.addObject("msg",登陆信息有误);
//return "redirect:/index.jsp;// web-inf/index;
 mav.setViewName("redirect:/index.jsp");
}



AOP底层业务实现：
  aspect  object programming  面向切面的编程
  功能： 让关注点代码与业务代码分离
  关注点   重复代码的方法就叫关注点
  切面     关注点形成的类，就叫切面类
           重复代码进行抽象，运行时向业务方法中动态的植入  切面类代码
  切入点    
        通过切入点表达式，指定拦截哪些类的哪些代码，给指定的类在运行时的代码




IOC
1.1    基本原理--- 容器和bean 
    容器   means   beanFactory 是springIOC容器的实体；IOC容器对bean进行管理
   beanfactory 是IOC容器的核心接口，职责包括： 实例化、定位、配置应用程序中的对象以及建立这些对象间的依赖； xml就是最常用的一个。
   spring  ioc容器至少包含一个bean定义；   
   bean的定义包括： 服务层对象、数据访问层对象（DAO）、类似 Struts Action的表示层对象、Hibernate sessionFactory对象、JMS Queue 对象 等等。 通常bean的定义并不与容器中的领域对象相同，因为领域对象的创建和加载必须依赖具体的dao和业务逻辑。
   基本结构如下：
   <?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
           http://www.springframework.org/schema/beans/spring-beans-2.5.xsd">

  <bean id="..." class="...">
    <!-- collaborators and configuration for this bean go here -->
  </bean>

  <bean id="..." class="...">
    <!-- collaborators and configuration for this bean go here -->
  </bean>

  <!-- more bean definitions go here -->

</beans>
  
  
  3.2.2  实例化容器
 ApplicationContext context = new ClassPathXmlApplicationContext(new String[] {"services.xml", "daos.xml"});
   BeanFactory factory = context;
3.2.2.1. XML配置元数据的结构
将XML配置文件分拆成多个部分是非常有用的。为了加载多个XML文件生成一个 ApplicationContext实例，可以将文件路径作为字符串数组传给ApplicationContext构造器 。而bean factory将通过调用bean defintion reader从多个文件中读取bean定义。

通常情况下，Spring团队倾向于上述做法，因为这样各个配置并不会查觉到它们 与其他配置文件的组合。另外一种方法是使用一个或多个的<import/>
 Spring IoC容器将管理一个或多个bean，这些bean 将通过配置文件中的bean定义被创建(在XML格式中为<bean/> 元素)。

在容器内部，这些bean定义由BeanDefinition 对象来表示，该定义将包含以下信息：

全限定类名：这通常就是已定义bean的实际实现类。

bean行为的定义，这些定义将决定bean在容器中的行为（作用域、生命周期回调等等）

对其他bean的引用，这些引用bean也可以称之为协作bean（collaborators） 或依赖bean（dependencies）.

创建bean实例时的其他配置设置。比如使用bean来定义连接池，可以通过属性或者构 造参数指定连接数，以及连接池大小限制等
 
 
 3.2.3 多种bean
 Spring IoC容器将管理一个或多个bean，这些bean 将通过配置文件中的bean定义被创建(在XML格式中为<bean/> 元素)。

在容器内部，这些bean定义由BeanDefinition 对象来表示，该定义将包含以下信息：

全限定类名：这通常就是已定义bean的实际实现类。

bean行为的定义，这些定义将决定bean在容器中的行为（作用域、生命周期回调等等）

对其他bean的引用，这些引用bean也可以称之为协作bean（collaborators） 或依赖bean（dependencies）.

创建bean实例时的其他配置设置。比如使用bean来定义连接池，可以通过属性或者构 造参数指定连接数，以及连接池大小限制等
 
3.2.3.1. bean的命名
每个bean都有一个或多个id(或称之为标识符或名称，在术语 上可以理解成一回事)。这些id在当前IoC容器中必须唯一。如果 一个bean有多个id，那么其他的id在本质上将被认为是别名。
要实现这一点可以在name属性中使用逗号、 冒号或者空格将多个id分隔。
  
  
3.2.3.1.1. bean的别名
<alias name="fromName" alias="toName"/>
内部类名

如果需要你希望将一个静态的内部类配置为 一个bean的话，那么内部类的名字需要采用二进制的写法。

比如说，在com.example包下有一个叫 Foo的类，而Foo类有一个静态 的内部类叫Bar，那么在bean定义的时候， class属性必须这样写：

com.example.Foo$Bar

注意这里我们使用了$字符将内部类和外部类进行分隔

当采用XML描述配置元数据时，将通过<bean/>元素的 class属性来指定实例化对象的类型。class 属性 (对应BeanDefinition实例的 Class属性)通常是必须的(不过也有两种例外的情形，见 Section 3.2.3.2.3, “使用实例工厂方法实例化”和 Section 3.6, “bean定义的继承”)。class属性主要有两种用途 ：在大多数情况下，容器将直接通过反射调用指定类的构造器来创建bean(这有点类似于 在Java代码中使用new操作符)；在极少数情况下，容器将调用 类的静态工厂方法来创建bean实例，class 属性将用来指定实际具有静态工厂方法的类(至于调用静态工厂 方法创建的对象类型是当前class还是其他的class则无关紧要)。


















