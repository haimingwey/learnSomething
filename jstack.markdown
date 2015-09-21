# jstack - Stack Trace
jstack主要用来查看某个Java进程内的线程堆栈信息

	用法：
	jstack [ option ] pid
	jstack [ option ] executable core
	jstack [ option ] [server-id@]remote-hostname-or-IP

1.用jps 找出线程id

	[root@localhost ~]# jps 
	3339 Main
	3799 Jps
	3774 ThreadLocalUsage

2.jstack带`-l`参数可以查看相关锁的信息

	[root@localhost ~]# jstack -l 3774
	2015-09-21 16:49:29
	Full thread dump Java HotSpot(TM) Client VM (24.79-b02 mixed mode):
	
	"Attach Listener" daemon prio=10 tid=0xb767e000 nid=0xef7 waiting on condition [0x00000000]
	   java.lang.Thread.State: RUNNABLE
	
	   Locked ownable synchronizers:
		- None
	
	"DestroyJavaVM" prio=10 tid=0xb7606800 nid=0xebf waiting on condition [0x00000000]
	   java.lang.Thread.State: RUNNABLE
	
	   Locked ownable synchronizers:
		- None
	
	"Thread-0" prio=10 tid=0xb767d000 nid=0xec7 waiting on condition [0xa10b8000]
	   java.lang.Thread.State: TIMED_WAITING (sleeping)
		at java.lang.Thread.sleep(Native Method)
		at ThreadLocalUsage.run(ThreadLocalUsage.java:12)
	
	   Locked ownable synchronizers:
		- None
	
	"Service Thread" daemon prio=10 tid=0xb766f000 nid=0xec5 runnable [0x00000000]
	   java.lang.Thread.State: RUNNABLE
	
	   Locked ownable synchronizers:
		- None
	
	"C1 CompilerThread0" daemon prio=10 tid=0xb766d000 nid=0xec4 waiting on condition [0x00000000]
	   java.lang.Thread.State: RUNNABLE
	
	   Locked ownable synchronizers:
		- None
	
	"Signal Dispatcher" daemon prio=10 tid=0xb766b400 nid=0xec3 runnable [0x00000000]
	   java.lang.Thread.State: RUNNABLE
	
	   Locked ownable synchronizers:
		- None
	
	"Finalizer" daemon prio=10 tid=0xb765ac00 nid=0xec2 in Object.wait() [0xa14ad000]
	   java.lang.Thread.State: WAITING (on object monitor)
		at java.lang.Object.wait(Native Method)
		- waiting on <0xa1a04298> (a java.lang.ref.ReferenceQueue$Lock)
		at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:135)
		- locked <0xa1a04298> (a java.lang.ref.ReferenceQueue$Lock)
		at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:151)
		at java.lang.ref.Finalizer$FinalizerThread.run(Finalizer.java:209)
	
	   Locked ownable synchronizers:
		- None
	
	"Reference Handler" daemon prio=10 tid=0xb7659400 nid=0xec1 in Object.wait() [0xa14fe000]
	   java.lang.Thread.State: WAITING (on object monitor)
		at java.lang.Object.wait(Native Method)
		- waiting on <0xa1a03f30> (a java.lang.ref.Reference$Lock)
		at java.lang.Object.wait(Object.java:503)
		at java.lang.ref.Reference$ReferenceHandler.run(Reference.java:133)
		- locked <0xa1a03f30> (a java.lang.ref.Reference$Lock)
	
	   Locked ownable synchronizers:
		- None
	
	"VM Thread" prio=10 tid=0xb7656800 nid=0xec0 runnable 
	
	"VM Periodic Task Thread" prio=10 tid=0xb7671400 nid=0xec6 waiting on condition 
	
	JNI global references: 116




