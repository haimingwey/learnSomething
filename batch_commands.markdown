###`@echo off`

批处理命令一般都会有一个前缀，表示当前目录，然后是执行了什么命令。
我们可以用`@echo off`把多余的前缀去掉。

	C:\Users\Administrator\Desktop>echo haimingwey
	haimingwey

	C:\Users\Administrator\Desktop>@echo off
	echo haimingwey
	haimingwey
	java -version
	java version "1.8.0_60"
	Java(TM) SE Runtime Environment (build 1.8.0_60-b27)
	Java HotSpot(TM) Client VM (build 25.60-b23, mixed mode, sharing)
	@echo on

	C:\Users\Administrator\Desktop>

###`cd %~dp0`

用test.bat文件写入一行数据`cd %~dp0`,然后点击文件运行

	C:\Users\Administrator\Desktop>cd C:\Users\Administrator\Desktop\
	
解析：
1，`cd`用于指定目录，毋庸多讲。
2，`%~`是命令扩展符，后面加不同的参数可以扩展成不同的命令。
3，d表示drive，即盘符。
4，p表示path路径。
5，0表示批处理文件的第一个参数。第一个参数默认为命令行的文件名。

	C:\Users\Administrator\Desktop>echo C:\Users\Administrator\Desktop\test.bat
	C:\Users\Administrator\Desktop\test.bat

更加详细的解释可以看：http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/percent.mspx?mfr=true
