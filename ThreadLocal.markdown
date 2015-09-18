# ThreadLocal
ThreadLocal instances are typically private static fields in classes that wish to associate state with a  thread(e.g.a user ID or Transaction ID).

## ThreadLocal类属性和方法

### 泛型

	public class ThreadLocal<T> {
	...
	}

### 静态内部类ThreadLocalMap

	/**
      	* ThreadLocalMap is a customized hash map suitable only for
     	* maintaining thread local values. To help deal with
     	* very large and long-lived usages, the hash table entries use
     	* WeakReferences for keys.
     	*/
	static class ThreadLocalMap {
	...
	}
	
### 方法

	private static int nextHashCode() {
		return nextHashCode.getAndAdd(HASH_INCREMENT);
    }

	private static AtomicInteger nextHashCode = new AtomicInteger();
