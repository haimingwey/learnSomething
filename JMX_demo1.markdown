### JMX实例1

今天看了一下JMX的资料，写了些非常简单代码。在此做写记录，废话少说，直接上代码。

	// 接口类，定义被管理资源的方法。
	public interface HelloMBean {
	    void setName(String name);
	
	    String getName();
	
	    void sayHello(String whoName);
	
	    void printHello();
	}

	// 需要被管理的资源Hello类
	public class Hello implements HelloMBean {
	
	    private String name;
	
	    public String getName() {
	        return name;
	    }
	
	    public void setName(String name) {
	        this.name = name;
	    }
	
	    public void printHello() {
	        System.out.println("Hello World "+name);
	    }
	
	    public void sayHello(String whoName) {
	        System.out.println("Hello "+ whoName);
	    }
	}
	
	// 适配器
	public class HelloAgent {
	
	    public static void main(String[] args) throws Exception {
	        MBeanServer server = MBeanServerFactory.createMBeanServer();
	        ObjectName name = new ObjectName("com.company.Hello:name=haimingwey");
	        server.registerMBean(new Hello(), name);
	        HtmlAdaptorServer adaptor = new HtmlAdaptorServer();
	        ObjectName adapterName = new ObjectName("com.company.HelloAgent:name=htmladaptor,port=8082");
	        server.registerMBean(adaptor, adapterName);
	        adaptor.start();
	        System.out.println("start...");
	    }
	    
	}
	

- 运行代码HelloAgent.main()
- 在浏览器输入http://localhost:8082/

	![在浏览器输入http://localhost:8082/](./Figure/jmx/demo1-Agent-View.jpg)

- 点击链接`name=haimingwey`

	![MBean view Hello](./Figure/jmx/demo1-MBean-View-Hello.jpg)

	- 位置1输入`name`的属性值
	- 位置2点击应用，等于调用bean中的setName()方法
	- 位置3输入`sayHello`方法的参数
	- 位置4点击方法，将会使用输入的参数调用此方法
	- 位置5点击调用`printHello`方法
