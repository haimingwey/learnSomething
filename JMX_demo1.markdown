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
	- 
	![demo1-sayHello-Successful](./Figure/jmx/demo1-sayHello-Successful.jpg)

	- 位置5点击调用`printHello`方法

HelloAgent主程序输出如下：

	start...
	Hello Jone
	Hello World haimingwey

###　总结：
在一个系统中常常会有一些配置文件，如服务器IP地址，端口号等。一般我们有4中方法来实现配置项的加载。
- 直接写死在程序代码里面。
- 写在配置文件中，通常是properties文件。
- 把配置缓存起来，读取的时候检查一下配置文件是否有更新，如果有改动就重读一遍，否则从缓存中读取。
- JMX把配置属性集中在一个类，然后通过MBean修改属性值。JMX提供了一个WEB页面来改变bean属性，这一点非常方便。
