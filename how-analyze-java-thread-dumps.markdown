# How to Analyze Java Thread Dumps

	原博客地址：https://dzone.com/articles/how-analyze-java-thread-dumps

当多个线程同时应用相同的资源时，容易发生线程锁竞。线程锁竞线程锁竞争的一种典型情况就是死锁，下面是两者的关系。

	--Thread contention
		--Deadlock

我们可以用java自带的一些工具来分析线程锁。java自带的都有哪些工具呢？我们可以在jdk的bin目录下找到。
[root@localhost bin]# ls
appletviewer  idlj       javac           javap         jconsole  jinfo    `jps`         jstat      native2ascii  rmic         serialver   wsgen
apt           jar        javadoc         java-rmi.cgi  jcontrol  jmap     jrunscript  jstatd     orbd          rmid         servertool  wsimport
ControlPanel  jarsigner  javafxpackager  javaws        jdb       jmc      jsadebugd   jvisualvm  pack200       rmiregistry  tnameserv   xjc
extcheck      java       javah           jcmd          jhat      jmc.ini  `jstack`      keytool    policytool    schemagen    unpack200
		
## 线程状态

	    public enum State {
	        NEW,
	        RUNNABLE,
	        BLOCKED,
	        WAITING,
	        TIMED_WAITING,
	        TERMINATED;
	    }
	    
-NEW: The thread is created but has not been processed yet.
-RUNNABLE: The thread is occupying the CPU and processing a task. (It may be in WAITING status due to the OS's resource distribution.)
-BLOCKED: The thread is waiting for a different thread to release its lock in order to get the monitor lock.
-WAITING: The thread is waiting by using a wait, join or park method.
-TIMED_WAITING: The thread is waiting by using a sleep, wait, join or park method. (The difference from WAITING is that the maximum waiting time is specified by the method parameter, and WAITING can be relieved by time as well as external changes.) 

##　线程类型

	守护线程
	非守护线程

线程运行main`static void main(String[] args)` 方法会产生一个线程，且是非守护线程。

## 用jVisualVM

## 用jstack，这里不说了，有一篇已经说过了。






	
