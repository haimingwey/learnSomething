# jstack - Stack Trace

http://docs.oracle.com/javase/7/docs/technotes/tools/share/jstack.html

	[root@localhost java]# jstack -F -l 2919
	Attaching to process ID 2919, please wait...
	Debugger attached successfully.
	Client compiler detected.
	JVM version is 24.79-b02
	Deadlock Detection:
	
	No deadlocks found.
	
	Thread 2920: (state = BLOCKED)
	
	Locked ownable synchronizers:
	    - None
	
	Thread 2928: (state = BLOCKED)
	 - java.lang.Thread.sleep(long) @bci=0 (Interpreted frame)
	 - ThreadLocalUsage.run() @bci=12, line=12 (Interpreted frame)
	
	Locked ownable synchronizers:
	    - None
	
	Thread 2924: (state = BLOCKED)
	
	Locked ownable synchronizers:
	    - None
	
	Thread 2923: (state = BLOCKED)
	 - java.lang.Object.wait(long) @bci=0 (Interpreted frame)
	 - java.lang.ref.ReferenceQueue.remove(long) @bci=44, line=135 (Interpreted frame)
	 - java.lang.ref.ReferenceQueue.remove() @bci=2, line=151 (Interpreted frame)
	 - java.lang.ref.Finalizer$FinalizerThread.run() @bci=36, line=209 (Interpreted frame)
	
	Locked ownable synchronizers:
	    - None
	
	Thread 2922: (state = BLOCKED)
	 - java.lang.Object.wait(long) @bci=0 (Interpreted frame)
	 - java.lang.Object.wait() @bci=2, line=503 (Interpreted frame)
	 - java.lang.ref.Reference$ReferenceHandler.run() @bci=46, line=133 (Interpreted frame)
	
	Locked ownable synchronizers:
	    - None



