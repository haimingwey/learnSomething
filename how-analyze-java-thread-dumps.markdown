# How to Analyze Java Thread Dumps

	原博客地址：https://dzone.com/articles/how-analyze-java-thread-dumps

当多个线程同时应用相同的资源时，容易发生线程锁竞。线程锁竞线程锁竞争的一种典型情况就是死锁，我们可以用java自带的一些工具来分析线程锁。

	--Thread contention
		--Deadlock
		
在分析之前，我们有必要了解一下线程的基本状态有哪些？我们可以在Thread.State查看详细定义

	    public enum State {
	        NEW,
	        RUNNABLE,
	
	        /**
	         * Thread state for a thread blocked waiting for a monitor lock.
	         * A thread in the blocked state is waiting for a monitor lock
	         * to enter a synchronized block/method or
	         * reenter a synchronized block/method after calling
	         * {@link Object#wait() Object.wait}.
	         */
	        BLOCKED,
	        WAITING,
	
	        /**
	         * Thread state for a waiting thread with a specified waiting time.
	         * A thread is in the timed waiting state due to calling one of
	         * the following methods with a specified positive waiting time:
	         * <ul>
	         *   <li>{@link #sleep Thread.sleep}</li>
	         *   <li>{@link Object#wait(long) Object.wait} with timeout</li>
	         *   <li>{@link #join(long) Thread.join} with timeout</li>
	         *   <li>{@link LockSupport#parkNanos LockSupport.parkNanos}</li>
	         *   <li>{@link LockSupport#parkUntil LockSupport.parkUntil}</li>
	         * </ul>
	         */
	        TIMED_WAITING,
	
	        /**
	         * Thread state for a terminated thread.
	         * The thread has completed execution.
	         */
	        TERMINATED;
	    }
	    
