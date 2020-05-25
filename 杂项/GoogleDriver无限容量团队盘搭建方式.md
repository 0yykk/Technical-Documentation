# 准备阶段
* 谷歌账号，为了使用 [Google Drive](https://www.google.com/intl/zh-CN/drive/)
* 免费域名，可以使用 [freenom](https://www.freenom.com) 白嫖一年的免费域名
* [CloudFlare](https://dash.cloudflare.com/login)账号
* 谷歌浏览器插件 [gooreplacer](https://pan.baidu.com/s/1u1JilxWO7Qm79C6TE0cFkw) (提取码:svd8) 重定向freenom的检测网址到国内帮助实现注册域名
* 一个科学上网的工具

# 开始
 * ### 创建谷歌团队盘
 从以下3个链接中随意访问一个，输入谷歌账号以及团队盘名称创建即可

 * https://gd.404edu.workers.dev/ 
 * https://gd.zxd.workers.dev/ 
 * http://leon.educationhost.cloud/ 
 新增加几个申请地址，一个不行换另一个，目前都可用。

 * https://td.fastio.me/
 * https://gd.zxd.workers.dev/
 * https://gd.404edu.workers.dev/
 * http://leon.educationhost.cloud/

 ![](/asset/img/1590390639(1).png)
 * ### 申请freenom 免费域名
 谷歌浏览器安装[gooreplacer](https://pan.baidu.com/s/1u1JilxWO7Qm79C6TE0cFkw) (提取码:svd8)插件来解锁此网站的反代理机制并导入配置文件如图所示，不然查域名都是不可用的

![](/asset/img/1590391267(1).png)

导入配置后不需要动其他的了，确保蓝色的√是开启的就行了。
之后访问freenom官网，注意此处访问freenom在注册登录后不要翻墙上网,切记！！！！！！！！！！！！！！！进去默认中文，翻墙反而会出现订单提交页面按钮无法点击的情况

![](/asset/img/1590391409(1).png)

点击合作伙伴>开发人员，下拉到最底部，准备进行注册。

![](/asset/img/1590391471(1).png)

进入后左边填入您的邮箱，点击验证我的电子邮箱。
谷歌账号和Facebook注册会出错，务必选择左边的邮箱注册(我建议大家可以先翻墙且不勾选插件来注册，应该是能注册成功的，登录后再去掉tz并勾选插件进行下一步操作。这个需要您多尝试几次，大概率可以成功)

信息注意最好填你家的模糊地址，除了姓名，联系方式，性别是瞎编的，其余最好和你所在地差不多，会有ip检测机制的，不然你申请域名到最后一步会被自动取消。

注册后登录，点击register new domain,输入你想要的域名前缀

然后输入想要的域名，检查可用性，如果显示被占用多更换几个关键字进行检测
选好之后购买

![](/asset/img/1590391670(1).png)

选择12个月白嫖套餐

![](/asset/img/1590391825(1).png)

接下来要先进行域名解析，才能添加到cloudfare

![](/asset/img/1590391890(1).png)

点域名服务器->点击管理freenom dns

![](/asset/img/1590391963(1).png)
目标随便填个ip并保存

* ### 基于cloudflare反向代理的分发网络来管理域名
此网站也无需翻墙，注册并登录
 
注意如果显示你的域名未注册的话请多等一会，第一次估计要个几分钟，但也别一直等，很可能是上一步操作问题。实在不行回去重新操作把ttl临时改为900，之后进cloudfare 后ttl最好自动，设置好后选择免费计划

![](/asset/img/1590392171(1).png)

选好之后在这个页面上会显示你在freenom上填写的DNS纪录(忽略图片上的，正常情况下你这里还是www)

![](/asset/img/1590401984(1).jpg)

继续

将下面图片中的两个CloudFlare名称服务器的名称填写到freenom域名服务器中

![](/asset/img/1590402123(1).png)

填写到这里

![](/asset/img/1590402255(1).png)

保存后返回cloudfare 标签页点击完成，检查域名会自动刷新。

![](/asset/img/1590402318(1).png)

点完成，点下dns，可以改www为任意你想要的，

![](/asset/img/1590401984(1).jpg)

然后切换到ssl\tls切换到始终使用 https

![](/asset/img/1590402476(1).png)

* ### 通过goindex和gdindex一键生成网站网盘目录页并把代码部署到Cloudflare worker
 * #### 搭建goindex并绑定路由
  访问goindex一键生成[网站](https://install.kenci.workers.dev )
  获取验证码（注意要翻墙，一个验证码只能用一次，但可以重复获取）
  ![](/asset/img/1590402753(1).png)

  * 路径id即为你共享盘的那串代码，找到之前保存的并粘贴即可，或者重新访问谷歌网盘获取
  * 设置密码，你不改的话默认是index。选择主色和边框颜色.一键点生成，点复制就行。

  ![](/asset/img/1590402871(1).png)
  
  回到Cloudflare 点击worker->管理worker->创建worker
  然后删除自带的JS代码并粘贴你刚复制的，点击保存并部署，新生成的网盘目录就搞好了，右边可以点发送来测试，返回200代表已经部署好了，也可以点预览来访问。
  
  * 想在主页显示文字可以自己写Readme.md通过谷歌网盘页面上传至根目录。

  * 想对单个文件夹设置密码可以在此文件夹下放置名为".password"的文件，注意文件名就是.password，不是后缀。文件内容填你想对那个文件夹设置的密码就行。程序文件中 root_pass 为根目录的密码，优先于 .password 文件

  <font color=red size=4>注意：目前仅goindex支持设置文件夹密码，gdindex不支持，换句话说就是你设置文件夹密码在goindex是有效的，但在gdindex中却无视你设置的文件夹密码，所以一般建议不要公开开放gdindex网盘目录，最好设置用户名和密码，否则无法确保你文件夹的安全</font>
* #### 搭建gdindex实现上传功能
  同理我们可以访问[gdindex生成](https://gdindex-code-builder.glitch.me/ )网站然后使用和搭建goindex的方式即可搭建成功

  <font color=red>另外为了安全，您也可以在cloudfare防火墙中开启5秒盾可有效防止洪水攻击。</font>
  
* ### 本地部署python环境及依赖包
  * 下载[python](https://www.python.org/downloads/)
  * 下载[rclone]()
  * 安装[autoclone]()

 * 配置rclone的环境变量
  Windows 10 中 
   * 在“搜索”中，搜索以下内容并进行选择：控制面板 
   * 单击高级系统设置链接。 
   * 单击环境变量。在系统变量部分中，找到并选择 PATH 环境变量。单击编辑。如果 PATH 环境变量不存在，请单击新建。比如你的Rclone.exe在目录D:\Rclone\Rclone.exe， 则你的 PATH 环境量的值即为D:\Rclone 在编辑系统变量（或新建系统变量）窗口中，指定 PATH 环境变量的值。
   * 单击确定。通过单击确定关闭所有剩余窗口

* <font color=red>开启全局代理</font>
  * 使用谷歌浏览器查看代理工具的端口，一定要全局代理

* ### 本地利用ac 在cmd 命令行代理的设定及创建项目并下载sa
  1. 设置cmd代理，使得cmd正常访问网络
  首先打开cmd，分两次输入
  <br>
  set http_proxy=http://127.0.0.1:10809 
  set https_proxy=http://127.0.0.1:10809
  <br>
  <font color=red>10809是你的代理工具的端口号，之后不要关闭cmd，否侧每次打开都需要重新设置cmd代理</font>
  2. 切换目录至解压的autoRclone目录
  输入 pip install -r requirements.txt 安装依赖文件
  执行后如下图
  ![](/asset/img/1590407669(1).png)
  如果提示更新，输入 python -m pip install --upgrade pip

* ### 下载你的云盘服务器凭证
   * 首先[开启Drive 的API](https://developers.google.com/drive/api/v3/quickstart/python)
   ![](/asset/img/1590407850(1).png)
   * 点击开启，选择类型桌面 desktop就行,下载得到 credential.Json文件(你的云盘的通行证)
   * 把下载的credential.json放在autorclone的目录下。

* ### 接下来准备生成sa（服务账号，也是个邮箱）
   * 在cmd中输入 python gen_sa_accounts.py --quick-setup -1
    这将会重置化已有的项目并在该项目下生成sa
    如果这样显示
    ![](/asset/img/1590408033(1).png)
    则将此时cmd上的Please visit this URL to....后面的URL复制到浏览器访问获得authorization code 并且填写到cmd中，按回车后又会得到一串链接，请自行手动复制到浏览器并访问后会让您开启service usage api
* ### 下载json文件并提取sa账号
  如果您是一开始就成功了或者最后才正常运行，都会如下图所示创建并下载sa
  ![](/asset/img/1590408337(1).png)
  sa下载完成后会在autorclone目录下的accounts目录。正常的数量是100个
  * 提取下载的json文件中的sa(邮箱服务账号)
  看到这，无论怎样，您都应该实现了sa的下载
  接下来您需要用软件[gesturesbyfeifan.exe](https://pan.baidu.com/s/1OxKtbexgm-WrezSDP-v-dA)(提取码：gil1)，放到autoclone的accounts目录下，双击运行，会生成一个user.txt，这就是您的sa邮箱集合.
* ### google 邮件群组的创建，添加sa和本地上传sa 至td
  * 创建谷歌群组并添加sa
   <br>
   访问[google group](https://groups.google.com/)来创建群组
   <font color=red>访问此网站务必关闭第三步中申请freenom的免费域名所用的插件，不然添加成员时过不了人机验证。</font>
   <br>
  * 选择创建群组，由于免费用户限制一次加10个邮箱，一天（24小时）限制添加100个，所以请10个10个的复制user.txt的邮箱添加.(这也是一天75t上限的来源)
  <br>
  * 添加群组邮箱到自己的td（团队盘，共享盘）
    100个sa 添加完成后找到您群组的邮箱号，如下图。
    ![](/asset/img/1590408750(1).png)
    接下来访问谷歌云盘，添加您群组的邮箱号至共享盘成员，权限设置为内容管理员和管理员都是可以的。
    ![](/asset/img/1590408825(1).png)
    ![](/asset/img/1590408854(1).png)
    <br>
  * 同步群组成员到td
  让我们回到刚才的cmd窗口(如果是重新打开的别忘了cmd代理和切换目录),运行以下命令将accounts目录下的sa添加到td群组
  <br>
  <font color=blue>python3 add_to_team_drive.py -d SharedTeamDriveSrcID</font>
  <br>
  <font color=red>注意此处的SharedTeamDriveSrcID需要修改成你团队盘的路径ID，url中folder后面的字段</font>
  然后回车，会显示出的你盘名，在回车会出现进度条，将account目录下的100个sa账号添加到团队盘群组，此时回到您的谷歌网盘共享盘页面，您会看到盘名下变成了101个成员，1个群组。
* ### gclone的下载和配置及转存命令
   * 安装[gclone](https://github.com/donwa/gclone/releases)
   * 注意转存时cmd也是要代理http和https的，总之就是只要打开cmd就先要设置代理。
   * 代理设置好后，直接cmd 运行 gclone config，进入gclone的配置界面。
   ![](/asset/img/1590409307.png)

   * 选择n
   * 输入一个名字(运行转存时需要用到的代号)
   * 输入13并回车
   * 空格 回车
   * 空格回车
   * 输入1 回车
   * 空格 回车
   * 随便输入一个accounts目录下的json文件的路径，注意是确切的随意的一个json文件的路径。
   * 输入n (取消进入高级设置) 回车
   * 输入Y 回车
   * 再输入Y，回车
   * 再输入q回车（退出gclone 设置）
* ### gclone 转存命令
   恭喜你，完成了所有的步骤，你已经拥有了一个自己的无限空间和几乎无限速的网盘。
   <font color=red>以下命令在cmd设置完代理后即可运行，不需要cd 到对应目录</font>
   <br>
   gclone copy gc:{网上别人分享的文件的地址的路径id} gc:{你自己的团队盘目录下的文件夹的id} --drive-server-side-across-configs -v  
   <br>
   <font color=red>此处的 gc 是你之前给网盘取得代号</font>
   查重命令
   gclone dedupe newest gc:{你自己的团队盘目录下的文件夹的id}
   分享个分享链接给大家作为测试
   <br>
   <https://drive.google.com/drive/folders/1MMD97TyOU-wMOusruGoXIhQebz1VTmH2>


















 