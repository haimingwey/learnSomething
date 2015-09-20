# ThreadLocal
ThreadLocal instances are typically private static fields in classes that wish to associate state with a  thread(e.g.a user ID or Transaction ID).

## ThreadLocal fields and methods

### Genericity

	public class ThreadLocal<T> {
		...
	}

### Static class ThreadLocalMap

	/**
    * ThreadLocalMap is a customized hash map suitable only for
    * maintaining thread local values. To help deal with
    * very large and long-lived usages, the hash table entries use
    * WeakReferences for keys.
    */
	static class ThreadLocalMap {
	    ...
	}
	
### The ThreadLocal object act as keys, searched via threadLocalHashCode.
	private final int threadLocalHashCode = nextHashCode();
	
### AtomicInteger: An value that may be updated atomically.

AtomicInteger类有什么功能？

	基本上就是简单的赋值与++、--操作

AtomicInteger类是怎么实现的？

	使用unsafe类控制


	private static AtomicInteger nextHashCode = new AtomicInteger();

### Why is 0x61c88647?
	private static final int HASH_INCREMENT = 0x61c88647;
	
### Return next hash code.
	private static int nextHashCode() {
		return nextHashCode.getAndAdd(HASH_INCREMENT);
    }

### ThreadLocalMap有一个Entry数组，Entry保存键值对。
	public T get() {
        Thread t = Thread.currentThread();
        ThreadLocalMap map = getMap(t);
        if (map != null) {
            ThreadLocalMap.Entry e = map.getEntry(this);
            if (e != null)
                return (T)e.value;
        }
        return setInitialValue();
    }
	
	private T setInitialValue() {
        T value = initialValue();
        Thread t = Thread.currentThread();
        ThreadLocalMap map = getMap(t);
        if (map != null)
            map.set(this, value);
        else
            createMap(t, value);
        return value;
    }
	
	protected T initialValue() {
        return null;
    }
	
	public void set(T value) {
        Thread t = Thread.currentThread();
        ThreadLocalMap map = getMap(t);
        if (map != null)
            map.set(this, value);
        else
            createMap(t, value);
    }
	
	public void remove() {
         ThreadLocalMap m = getMap(Thread.currentThread());
         if (m != null)
             m.remove(this);
    }

### Get the map associated with a ThreadLocal.
	ThreadLocalMap getMap(Thread t) {
        return t.threadLocals;
    }
	
	void createMap(Thread t, T firstValue) {
        t.threadLocals = new ThreadLocalMap(this, firstValue);
    }
	
	static ThreadLocalMap createInheritedMap(ThreadLocalMap parentMap) {
        return new ThreadLocalMap(parentMap);
    }
	
	T childValue(T parentValue) {
        throw new UnsupportedOperationException();
    }
