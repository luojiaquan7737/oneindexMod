# oneindex
Onedrive Directory Index

## Attention
 - 注意不管是之前的魔改还是非魔改版本，请拉取本程序重新安装下，因为token缓存换到redis里了！
 - ~~注意安装页面的redirecturl写自己的地址，必须使用https协议，例如https://pan.shax.vip/，类似请照着这个写就好了，同时在graph页面增加一个这个回调地址就行！~~ **已经修正可用的跳转网址**

## 预览地址
https://pan.2bmi.com/

## 更新信息
- 2019-11-02
  - 补充说明文档
- 2019-09-09
  - 修正跳转网址
  - 补充 cache文件夹
- 2019-01-08
  - 修复部分用户出现安装成功后无内容的bug
  - 优雅token缓存周期，无需定时任务，智能获取，优化数据缓存
  - 修改默认主题，修复图床上传问题，前提是你要打开图床
  - base.php里只涉及用户侧数据，去除refresh_token等，添加redis密码配置信息
  - 修改issue里bug

## 魔改说明：
- 感谢大佬donwa提供原版的oneindex源码

- 本代码大部分基于donwa的oneindex添加内容自用

## 魔改内容
- 缓存和token获取使用redis ,无需使用命令设置定时任务，增加默认有效期  

- 如果onedrive有上传或者删除文件，请后台手动清除缓存

- 图床使用ajax获取，可以直接展现链接和引用代码

## 功能：
不用服务器空间，不走服务器流量，  

直接列onedrive目录，文件直链下载。  

## change log:  
18-03-29: 更新直链获取机制、缓存机制，避免频繁访问的token失效  
18-03-29: 解决非英文编码问题  
18-03-29: 添加onedrive共享的起始目录 功能  
18-03-29: 添加rewrite的配置文件  
18-03-29: 增加sqlite模式cache支持  
18-03-29: 添加缩略图功能  
18-03-29: 添加404判断  
18-03-31: 添加console  
18-04-13: 修复特殊文件名无法下载问题  
18-04-13: 添加命令行上传功能  
18-04-16: 更新 2.0 beta  
18-04-16: 更新展示界面  
18-04-16: 响应式，支持小屏设备  
18-04-16: 图片在线预览  
18-04-16: 视频在线播放  
18-04-16: 代码在线查看（js、css、html、sh、php、java、md等）  
18-04-16: README.md 支持，解析各目录下(onedirive目录下) README.md 文件，在页面尾部展示。  
18-04-18: 音频在线播放  
18-04-18: HEAD.md 支持，在页面头部展示   
18-04-18: .password 文件夹加密  
18-05-06: 在线视频播放器替换成 Dplayer  
18-05-06: 在线视频播放支持'mp4','webm','avi','mpg', 'mpeg', 'rm', 'rmvb', 'mov', 'wmv', 'mkv', 'asf'  
18-06-01: 支持个人账号  
18-06-01: cli文件夹上传（单线程）  
18-06-01: 管理后台(后台地址:?/admin 默认密码:oneindex)  
18-06-01: 不同后缀展示设置  
18-06-01: 文件直接输出  
18-06-01: 文件上传管理（后台） 
18-06-01: 增加index.html特性   
18-06-01: 图床功能   

## 需求：
1. PHP空间，PHP 5.6+ 打开curl支持  
2. Redis5.0.5+以上
3. onedrive 账号 (个人、企业版或教育版/工作或学校帐户)  
4. oneindex 程序

## 安装：
1. **我这里以宝塔安装好Nginx、PHP7.0以及域名one.2bmi.com作为演示**
2. **安装Redis**
![194154f0a8f66f86f.png](https://www.z4a.net/images/2019/11/02/194154f0a8f66f86f.png)
3. **在安装期间，来新建一个网站，注意php版本是7.0，将域名解析到服务器这边**
![29e0464082c4524f8.png](https://www.z4a.net/images/2019/11/02/29e0464082c4524f8.png)
4. **在本项目复制zip的下载链接**
[![3f8d0cdaf744cd8f6.png](https://www.z4a.net/images/2019/11/02/3f8d0cdaf744cd8f6.png)](https://www.z4a.net/image/UpoCcw)
5. **打开网站的根目录并删除默认的文件，因域名不同，目录也不同**
![466b44c2178294893.png](https://www.z4a.net/images/2019/11/02/466b44c2178294893.png)
6. **下载好的压缩包解压并将所有文件剪切到根目录，删除压缩包以及解压目录**
![5bfcd759645b063d2.png](https://www.z4a.net/images/2019/11/02/5bfcd759645b063d2.png)
7. **确认Redis安装好，之后打开PHP7.0管理安装Redis扩展**
![6.png](https://www.z4a.net/images/2019/11/02/6.png)
8. **在安装Redis扩展期间，去开启curl 可能是878行如果找不到，查找关键字“php_curl.dll”**
![7.png](https://www.z4a.net/images/2019/11/02/7.png)
9. **修改完成之后点击保存，确认Redis扩展安装完成，在PHP7.0管理的“服务”点击重载服务
10. **至此就可以浏览器打开绑定的域名访问了！**
![8.png](https://www.z4a.net/images/2019/11/02/8.png)
11. **点击进去获取ID以及机密，如果以前有操作过可以前往 https://apps.dev.microsoft.com 删除ID**
![9.png](https://www.z4a.net/images/2019/11/02/9.png)
12. **复制机密到网站填写，点击返回下拉页面就可以看到ID，当然你可以直接快捷键查找**
![11.png](https://www.z4a.net/images/2019/11/02/11.png)
![12.png](https://www.z4a.net/images/2019/11/02/12.png)
13. **填写完成之后，点击下一步**
![13.png](https://www.z4a.net/images/2019/11/02/13.png)
14. **点击“绑定账号”便会跳转到微软登录账号。按提示操作！**
![14.png](https://www.z4a.net/images/2019/11/02/14.png)
![15.png](https://www.z4a.net/images/2019/11/02/15.png)
15. **最后就是绑定完成，点击访问网站**
![16.png](https://www.z4a.net/images/2019/11/02/16.png)
![17.png](https://www.z4a.net/images/2019/11/02/17.png)

**后台管理地址默认是：域名/?/admin**
**后台的文件管理地址默认是：https://onedrive.live.com/ 但是这个域名不能正常访问，所以需要自行修改自己onedrive地址
文件在网站根目录“/view/admin”下的layout.php  已注释的
这里举例：https://域名前缀-my.sharepoint.cn 这是世纪互联运营的，https://域名前缀-my.sharepoint.com 这是微软运营的。
当然你不知道的话，可以去前往 https://www.office.com 登录后点击“OneDrive”，看地址栏显示即可！**

## docker 安装运行：

从docker仓库获取镜像：
```sh
none
```

或者从源码构建镜像：

```shell
git clone https://github.com/david7207/oneindexMod.git
cd oneindex/
docker build -t your-image-name .
```

运行：

```shell
docker run -d -p {open port}:80 --name {container name} --restart=always {image name}
```

停止删除容器：

```shell
docker stop {container name}
docker rm -v {container name}
```

## 特殊文件实现功能  
` README.md `、`HEAD.md` 、 `.password`特殊文件使用  

可以参考[https://github.com/donwa/oneindex/tree/files](https://github.com/donwa/oneindex/tree/files)  

**在文件夹底部添加说明:**  
>在onedrive的文件夹中添加` README.md `文件，使用markdown语法。  

**在文件夹头部添加说明:**  
>在onedrive的文件夹中添加`HEAD.md` 文件，使用markdown语法。  

**加密文件夹:**  
>在onedrive的文件夹中添加`.password`文件，填入密码，密码不能为空。  

**直接输出网页:**  
>在onedrive的文件夹中添加`index.html` 文件，程序会直接输出网页而不列目录。  
>配合 文件展示设置-直接输出 效果更佳  

## 命令行功能  
仅能在php cli模式下运行  
**上传文件:**  
```
php one.php upload:file 本地文件 [onedrive文件]
```


**上传文件夹:**  
```
php one.php upload:folder 本地文件夹 [onedrive文件夹]
```

例如：  
```
//上传demo.zip 到onedrive 根目录  
php one.php upload:file demo.zip  

//上传demo.zip 到onedrive /test/目录  
php one.php upload:file demo.zip /test/  

//上传demo.zip 到onedrive /test/目录并命名为 d.zip  
php one.php upload:file demo.zip /test/d.zip  

//上传up/ 到onedrive /test/  
php one.php upload:file up/ /test/
```
