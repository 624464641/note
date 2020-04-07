#### 饿汉模式

``` java
private static Student student = new Student() ;
    public  static  Student getInstance(){
        return student;
    }
```

 每次应用返回的是同一个对象 ， 好处线程安全，坏处：浪费内存空间

#### 懒汉模式

``` java
   private static Student student1 ;
    public  static  Student getInstance2(){
        if(student1 == null){
            return new Student();
        }
        return student1;
    }
```

会返回一个新的对象

#### 双重校验

```java
    private static Student student2;
    public static Student getInstance3() {
        if (student2 == null) {
            synchronized (Test01.class) {
                if(student2 == null){
                    student2 = new Student();
                }
            }
        }
        return student2;
    }
```

+ 为了在多线程环境下，不影响程序的性能，不让线程每次调用方法时都加锁，而只是在实例未被创建时再加锁，在加锁处理里面还需要判断一次实例是否已存在

  

  

