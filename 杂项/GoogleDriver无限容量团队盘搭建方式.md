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







 