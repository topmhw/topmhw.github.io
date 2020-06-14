---
layout: post
title: 浅谈匿名内部类
category: java-basic
tags: [java-basic]
excerpt: 匿名内部类的作用、注意事项、应用场景
---
## 引入
   假如有个People抽象类，Boy实例类
   ``` java
    // 父类
    public abstract class People{
           public abstarct void say();
    }
   ```
   ``` java
    // 子类
    public class Boy extends People{
        public void say(){
           System.out.println("Hello World!");
        }
    }
   ```
   ``` java
   public class MyTest{
       // 测试类
       @Test
       public void Test(){
           People p = new Boy();
           p.say();
       }
   }
   ```
   假如我们用到People类的性质，就必须要单独写一个子类，像上述那样将父类引用指向子类对象。如果Boy类在程序仅会实例化一次且在其他地方不会使用到，那么额外编写一个Boy子类就显得没必要了。使用匿名内部类实现上面功能会是怎么样的呢？
   ``` java
    // 父类
    public abstract class People{
        public abstarct void say();
    }
   ```
   ``` java
   public class MyTest{
       // 测试类
       @Test
       public void Test(){
           People p = new People(){
                public void say(){
                   System.out.println("Hello World!");
                }
           };
           p.say();
       }
   }
   ```
   这样子我们就不用额外编写一个子类了，也不需要为子类的命名烦恼，同时也可以实现相应的功能。

## 匿名内部类的作用
   实例化抽象类，减少重新创建一个类的代码编写，同时不会因为类命名而烦恼。当然，匿名内部类也可以用在接口上的。
   ``` java
  // 父类
   public interface class People{
       void say();
   }
   ```
   ``` java
   public class MyTest{
       // 测试类
       @Test
       public void Test(){
           Integer i = 10;
           People p = new People(){
                public void say(){
                   System.out.println("Hello World!");
                   System.out.println(i); // 10
                }
           };
           p.say();
       }
   }
   ```

## 注意事项
- 匿名内部类同内部类一样要依赖外部类的存在而存在，因此匿名内部类不允许出现静态的变量、方法块及方法。
- 匿名内部类可以访问外部类局部方法里面的局部变量，但是不能修改局部变量。（具体请查看内部类的相关知识）

## 应用场景
当子类的实现简单且只实例化一次的话，不妨可以考虑匿名内部类。平时我们在多线程用得比较多内部类，我们看下匿名内部类如何创建线程的？当然你也可以用在其他场景。

   ``` java
   // 继承Thread创建线程
   public Solution{
       
       @Test
       public void Test(){
           Thread t = new Thread(){
               @Override
               public void run(){
                   for(int i = 0; i < 100; i++){
                       System.out.println(i);
                   }
               }
           };
           t.start();
       }
   }
   ```
   ``` java
   // 实现Runnable接口创建线程
   public Solution{
       
       @Test
       public void Test(){
           Thread t = new Thread(new Runnable(){
               @Override
               public void run(){
                   for(int i = 0; i < 100; i++){
                       System.out.println(i);
                   }
               }
           });
           t.start();
       }
   }
   ```
