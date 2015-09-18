# ThreadLocal
ThreadLocal instances are typically private static fields in classes that wish to associate state with a  thread(e.g.a user ID or Transaction ID).
ThreadLocal实例一般作为类的私有静态成员，用来关联一个线程。

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
	
