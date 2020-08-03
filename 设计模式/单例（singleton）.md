单例模式：

0. 准备阶段

  ~~~ java
/**
     * 1. 类在初始化时加载静态块 ，
     */
     private static final  SingletonA singletonA = new SingletonA();

     private static volatile  SingletonA singletonB = null ;

    /**
     * 设置私有的构造函数 外部无法访问
     */
    private SingletonA(){};
  ~~~

1.懒汉模式

~~~ java
 public static synchronized SingletonA getInstanceB(){

        if(singletonB == null ){

            singletonB =  new SingletonA();
            
        }
        return singletonB;
    }
~~~

特点： 类在初始化时没有加载，只有当外部第一次调用 getInstanceB时才会加载

2.饿汉模式

~~~ java
public static SingletonA getInstance(){
    return singletonA;
}
~~~

​      特点： 类在初始化时已经加载，全局任何地方调用都是使用同一个对象

3. 使用场景描述：

- 在应用场景中，某类只要求生成一个对象的时候，如一个班中的班长、每个人的身份证号等。
- 当对象需要被共享的场合。由于单例模式只允许创建一个对象，共享该对象可以节省内存，并加快对象访问速度。如 Web 中的配置对象、数据库的连接池等。
- 当某类需要频繁实例化，而创建的对象又频繁被销毁的时候，如多线程的线程池、网络连接池等。