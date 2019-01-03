* 本项目使用Python语言来实现旅游景点的收集和分析，前往Python官网，选择对应的系统进行下载，安装完成后，按Ctrl+R ,输入cmd,打开命令提示符窗口，输入python，验证是否安装成功。同时，我们要修改环境变量，右键点击"我的电脑"->属性->高级系统设置->环境变量，在系统变量栏目中，找到PATH，双击编辑后，添加刚才安装python的路径即可。
然后去官网进行BeautifulSoup4源码下载，下载源码，编译运行，然后将下载后的压缩包剪切到本机的python安装目录中，解压后，打开命令提示符窗口，输入python d:\python3.6\beautifulsoup4-4.5.1\setup.py build 即可完成安装。
接着，我们安装网页文件解析器htm5lib，只需直接运行pip install html5lib即可。接着去官网下载对应的.whl文件，根据自己的系统版本和python版本选择适合的文件。然后进行安装，首先在cmd中输入pip install wheel安装wheel工具，做好准备工作。接着运行pip install *.whl文件，即可成功安装lxml解析器。最后打开cmd，直接pip install requests即可安装。
