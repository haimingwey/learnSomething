###看到有batch文件开头写着@echo off，到底这个是什么意思呢？

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
