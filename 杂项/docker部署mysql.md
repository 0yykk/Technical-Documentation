### 准备阶段

以 Windows 10 为例，首先找到控制面板的启动或关闭Windows功能，如下图
![](/asset/img/1590500107(1).png)
<br>
然后勾选Hyper-V管理工具下所有的组件
![](/asset/img/1590500211(1).png)
点击确定保存，然后等待重启电脑。

重启后到[docker官方网站](https://hub.docker.com/editions/community/docker-ce-desktop-windows)下载 Windows 10 专用的安装包
![](/asset/img/1590500445(1).png)

安装docker desktop for windows
设置[阿里云镜像加速](https://www.aliyun.com/),登录后点击控制台找到容器镜像加速，进去可以获得一个镜像加速器链接，如下图
![](/asset/img/1590500808(1).png)
切换到自己当前操作系统，选择对应的操作方式进行操作，或者右键运行后任务栏下面的docker图标选择settings，然后在Docker Engine的registry-mirrors中填写你获得的镜像加速器地址链接，点击Apply应用并等待docker重启

### Pull MySQL镜像
* 打开cmd或者powershell，输入以下命令

   <font color=red>docker pull mysql:latest</font>

   拉取mysql镜像
### 运行MySQL容器
* 使用命令 <font color=red>docker images</font> 查看本地是否已经存在mysql镜像
  ![](/asset/img/1590501288(1).png)
  <br>
* 使用命令<font color=red>docker run -d --name mysql001 -p 2220:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql</font>
来运行当前镜像生成容器，并且设置root密码为123456，容器命名为mysql001，端口将宿主机2230端口映射到mysql的3306端口

* 使用docker ps命令查看当前运行的容器
  ![](/asset/img/1590501554(1).png)
### 通过root密码访问MySQL服务
* 使用命令 <font color=red>docker exec -it mysql001 bash</font> 输入对应的密码，访问MySQL服务
  ![](/asset/img/1590501627(1).png)
  现在就能够访问mysql服务了
  ![](/asset/img/1590501936(1).png)

### 结束
