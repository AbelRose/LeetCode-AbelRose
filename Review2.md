### Review2

一:

@Controller和@Service

@Controller

Controller 主要负责请求转发，接受页面过来的参数，传给Service处理，service接到返回值，再传给页面。

Controller，从字面上理解是***控制器***，所以它是负责***业务调度*** 的，所以在这一层应写一些业务的调度代码。而具体的业务处理应放在service中去写，而且service不单纯是对于dao的增删改查的调用，

@Service

service是***业务层***，所以应该更切近于***具体业务功能***要求，所以在这一层，一个方法所体现的是一个可以***对外***提供的功能。

就是对一个或多个DAO进行的***再次封装***，封装成一个服务，所以这里也就不会是一个原子操作了，需要***事物控制***。(在需要事务支持的地方加入***@Transactional注解***)

> 比如购物商城中的生成订单方法，这里面就不简单是增加个订单记录那么简单，
>
> 我们需要查询库存，核对商品等一系列实际业务逻辑的处理

DAO层(Data Access Object)

DAO层叫数据访问层，属于一种比较底层，比较基础的操作，具体到对于某个表的增删改查，也就是说某个DAO一定是和数据库的某一张表一一对应的，其中封装了增删改查基本操作，建议DAO只做***原子操作，增删改查。***



二:

Java 中sleep()和wait()的区别

- 这两个方法来自不同的类 sleep() 来自***Thread类***. 而wait()  来自***Object类***

  sleep是Thread的***静态类方法***，谁调用的谁去睡觉，即使在a线程里调用了b的sleep方法，实际上还是a去睡觉，要让b线程睡觉要在b的代码中调用sleep。

- 最主要是***sleep***方法***没有释放锁***，而***wait***方法***释放了锁***，使得***其他线程***可以使用同步控制块或者方法。

  sleep不出让系统资源；wait是进入线程等待池等待，出让系统资源，其他线程可以占用CPU。一般wait不会加时间限制，因为如果wait线程的运行资源不够，再出来也没用，要等待其他线程调用notify/notifyAll唤醒等待池中的所有线程，才会进入就绪队列等待OS分配系统资源。sleep(milliseconds)可以用时间指定使它自动唤醒过来，如果时间不到只能调用interrupt()强行打断。
  Thread.Sleep(0)的作用是“触发操作系统立刻重新进行一次CPU竞争”

- 使用范围：wait，notify和notifyAll只能在***同步控制方法*** 或者***同步控制块*** 里面使用，而sleep可以在***任何地方***使用

  ```java
  synchronized(x){ 
        x.notify() 
       //或者wait() 
  }
  ```

- sleep必须捕获异常，而wait，notify和notifyAll不需要捕获异常

总结:

- 两者都可以***暂停***线程的执行。

- 对于sleep()方法，我们首先要知道该方法是属于Thread类中的。而wait()方法，则是属于Object类中的。

- Wait 通常被用于***线程间交互/通信***，sleep 通常被用于***暂停执行***。

- sleep()方法导致了程序暂停执行指定的时间，让出cpu该其他线程，但是他的监控状态依然保持者，当指定的时间到了又会自动恢复运行状态。在调用sleep()方法的过程中，线程不会释放对象锁。

- 而当调用wait()方法的时候，线程会放弃对象锁，进入等待此对象的等待锁定池，只有针对此对象调用notify()方法后本线程才进入对象锁定池准备，获取对象锁进入运行状态。线程不会自动苏醒。



三:

死锁问题



四:

Java 用户用户密码加密

https://blog.csdn.net/u013068377/article/details/78921720

```XML
<!--    权限控制的两种方法  只能使用一种-->
<security:global-method-security jsr250-annotations="enabled"></security:global-method-security>
<!--    <sercurity:global-method-security secured-annotations="enabled"></sercurity:global-method-security>-->
<!--    <security:global-method-security pre-post-annotations="enabled"></security:global-method-security>-->
```

jsr250 不是加密方式



五:

AOP底层实现

























