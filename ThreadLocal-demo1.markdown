每一个线程都挂载了一个ThreadLocalMap。ThreadLocal类中get方法没有key传入，原因就在于这个key就是当前你使用的这个ThreadLocal它自己。ThreadLocal的对象生命周期可以伴随整个线程的生命周期。

	public class User {

	    private static final ThreadLocal<Object> enclosure = new ThreadLocal<Object>();

	    public void set(Object object) {
	        enclosure.set(object);
	    }

	    public Object get() {
	    	return enclosure.get();
	    }
	}


	public class ThreadLocalUsage extends Thread{
	
		public User user= new User();
	
		@Override
		public void run() {
			this.user.set("var1");
	
			while (true) {
				try {
					sleep(1000);
				} catch (InterruptedException e) {
	
				}
				System.out.println(this.user.get());
			}
		}
	
		public static void main(String[] args) {
			ThreadLocalUsage thread = new ThreadLocalUsage();
			thread.start();
	
			try {
				sleep(4000);
			} catch (InterruptedException e) {
	
			}
			thread.user.set("var2");
			System.out.println(thread.user.get());
		}
	}

