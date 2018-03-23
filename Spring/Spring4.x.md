### 五. 在IOC容器中配置Bean
1. Spring容器启动成功的三个条件:
    - Spring框架的类包已经加载到应用程序的类路径下.
    - 应用程序为Spring提供了完整的Bean配置信息
    - Bean的类都已经放到应用程序的类路径下.

    Spring启动时,读取应用程序提供的Bean配置信息,并在Spring容器中生成一份相应的Bean配置注册表,然后根据这张注册表实例化Bean,装配好Bean之间的依赖关系,为上层应用程序提供就绪的运行环境.

2. Bean的元数据信息(4方面)
    - Bean的实现类
    - Bean的属性信息,如数据源的连接数,用户名,密码等.
    - Bean的依赖关系,Spring根据依赖关系配置完成Bean之间的配置.
    - Bean的行为配置,如生命周期范围以及生命周期各过程的回调函数等.
3. Spring实现了Bean元数据信息内部表示与外部定义的解耦.  
![Spring容器内部解析](https://raw.githubusercontent.com/HubyLiang/MarkdownPhotos/master/Spring/Spring%E5%AE%B9%E5%99%A8%E5%86%85%E9%83%A8%E5%8D%8F%E4%BD%9C%E8%A7%A3%E6%9E%90.PNG)  
4. Bean的基本装配   
一般而言,在配置一个Bean的同时,需要为其指定 id 和 name ,且id必须唯一.此外,id和name都可以指定多个名字,名字之间可以用 ',' 隔开,即意味一次指定多个bean.   
id不允许重复,但name可以重复,如果使用getBean(beanName)获取Bean时,获取的为后一个声明的Bean,因为后一个将前一个覆盖掉.  
如果id和name两个属性都未指定,则默认将全限定类名作为Bean的名称.  
但注意: **通过id指定Bean的唯一名称才是康庄大道**
5. 依赖注入  
Spring支持两种依赖注入方式:属性注入和构造函数注入.   
属性注入指的是通过setXxx()方法注入Bean的属性值或依赖对象.这种更为广泛的使用.
6. 工厂方法注入  
7. 简化配置方式
   - 字面值属性
   ![](https://github.com/HubyLiang/MarkdownPhotos/raw/master/Spring/%E5%AD%97%E9%9D%A2%E5%80%BC%E5%B1%9E%E6%80%A7%E7%AE%80%E5%8C%96%E9%85%8D%E7%BD%AE.PNG)
   注意,如果使用简化版配置,将无法使用<![CDATA[]]>处理XML特殊字符,只能使用XML转义序列.
   - 引用对象属性
   ![](https://github.com/HubyLiang/MarkdownPhotos/raw/master/Spring/%E5%BC%95%E7%94%A8%E5%AF%B9%E8%B1%A1%E5%B1%9E%E6%80%A7%E7%AE%80%E5%8C%96%E9%85%8D%E7%BD%AE.PNG)
   <ref>的简化形式对应于<ref bean="xxx">,而<ref local="xxx">和<ref parent="xxx">则没有对应的简化形式.

   - 使用P命名空间
   ![](https://github.com/HubyLiang/MarkdownPhotos/raw/master/Spring/%E4%BD%BF%E7%94%A8P%E5%91%BD%E5%90%8D%E7%A9%BA%E9%97%B4.PNG)
   注意:  
   -- 对于字面值属性,格式为: &nbsp; p:<属性名> = "xxx"  
   -- 对于引用对象的属性,其格式为:  &nbsp; p:<属性名>-ref = "xxx"
8. 自动装配  
Spring IoC知道所有Bean的配置信息,此外,通过Java反射机制还可以知道实现类的结构信息,如构造函数,属性等信息.掌握这些Bean的信息后,Spring Ioc容器就可以进行Bean的自动装配.  
\<bean\>元素提供了属性autowire="<自动装配类型>" 属性来设置自动装配.  
![](https://github.com/HubyLiang/MarkdownPhotos/raw/master/Spring/Ioc%E8%87%AA%E5%8A%A8%E8%A3%85%E9%85%8D.PNG)
在实际开发中,XML配置方式很少使用自动装配功能,基于注解的方式默认采用byType自动装配策略.  
9. 方法注入  
无状态的Bean的作用域一般可以为singleton(单例模式),获取Bean的对象为最开始注入的Bean对象.  
10. lookup方法注入
CGLib可以在运行期动态操作Class字节码,为Bean的**动态**创建子类或实现类,因此让Spring Ioc容器拥有了复写Bean方法的能力.
