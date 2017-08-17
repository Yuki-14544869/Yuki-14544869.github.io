---
title: 使用hexo+github搭建我的个人博客
date: 2017-08-10 16:12:08
tags: 
  - Hexo
comments: true
---
## **闲聊**
在ACM的学习过程中碰见不会做的题目总是会上网搜索题解，在这过程中也是见识到了不同样式的博客。从而也萌生了自己写博客的念头，也想将自己的所学到的东西分享到博客上，不仅可以让别人学习，也是对自己的所学的一种巩固。于是一开始我用过一段时间的CSDN作为自己的博客，但是CSDN的样式对我来说仍然太丑，而且广告太多，在浏览之余，无意间发现了hexo，而且他的next主题性冷淡的色彩的搭配也直接戳中了我的内心。于是便乘着暑假给学弟们讲课之余建立了这么一个博客。

搭建环境步骤：

[一、 搭建环境准备](#1)  
[二、 安装Hexo](#2)  
[三、 Hexo的相关配置](#3)  
[四、 怎样将Hexo与github page 联系起来](#4)  
[五、 发布文章](#5)  
[六、 Next主题的简单配置](#6)

---------------------------------------------------------------------------------------------







## **一、 搭建环境准备**

大概可以分为以下三步 
- Node.js 的安装和准备 
- Git的安装和准备 
- gitHub账户的配置  
1. 配置Node.js环境
   下载node.js安装文件
    -[Windows Installer 32-bit](https://nodejs.org/dist/v4.2.3/node-v4.2.3-x86.msi)
    -[Windows Installer 64-bit](https://nodejs.org/dist/v4.2.3/node-v4.2.3-x64.msi)
   保持默认设置，一路next即可。最后在命令行界面(Win+R, 弹出运行之后输入cmd回车即可)确认版本以确定是否安装成功
   ```
    node -v
    npm -v
   ```
   ![](/Img/2017-08-10_17-34.png)  
2. 配置Git环境
   [Git官网下载地址](https://git-scm.com/downloads)
   与Node.js一样，一路默认配置直接下一步即可。最后打开命令行界面输入命令： 
   ```
    git --version
   ```
   如果结果如下图所示，则说明安装正确，可以进行下一步了，如果不正确，则需要回头检查自己的安装过程。
   ![](/Img/2017-08-10_17-36.png)  
3. github配置  
   1. 创建代码库
      登陆之后，点击页面右上角的加号，选择New repository：
      ![](/Img/2017-08-10_17-42.png)
      新建代码库  
      进入代码库创建页面：  
      在Repository name下填写yourname.github.io，Description (optional)下填写一些简单的描述（不写也没有关系），如图所示：
      ![](/Img/2017-08-10_19-54.jpg)
      **注意：比如我的github名称是Yuki-14544869 ,这里你就填 Yuki-14544869.github.io,如果你的名字是123456，那你就填 123456.github.io**
   2. 代码库设置  
      正确创建之后，你将会看到如下界面： 
      ![](/Img/2017-08-10_19-56.jpg)
      接下来开启gh-pages功能，点击界面右侧的Settings，你将会打开这个库的setting页面，向下拖动，直到看见GitHub Pages，如图：
      ![](/Img/2017-08-10_19-57.jpg)  
      **Github pages**
      ![](/Img/2017-08-10_19-58.jpg)  
      点击Automatic page generator，Github将会自动替你创建出一个gh-pages的页面。 如果你的配置没有问题，那么大约15分钟之后，yourname.github.io这个网址就可以正常访问了~ 如果yourname.github.io已经可以正常访问了，那么Github一侧的配置已经全部结束了。

到此搭建hexo博客的相关环境配置已经完成，下面开始讲解Hexo的相关配置

----------------------------------------------------------------------------------------------




## **二、 安装Hexo**
在自己认为合适的地方创建一个文件夹，这里我以E：/hexo 为例子讲解，首先在E盘目录下创建Hexo文件夹，进入文件夹后右击Git Bash Here进入git。
![](/Img/2017-08-10_20-04.png)
在命令行中输入：
```
    npm install hexo-cli -g
```
然后你会看到：
![](/Img/2017-08-10_20-05.jpg)
可能你会看到一个WARN，但是不用担心，这不会影响你的正常使用。 然后输入
```
    npm install hexo --save
```
然后你会看到命令行窗口刷了一大堆白字，下面我们来看一看Hexo是不是已经安装好了。 在命令行中输入：
```
    hexo -v
```
如果你看到了如图文字，则说明已经安装成功了。
![](/Img/2017-08-10_20-07.jpg)

---------------------------------------------------------------------------------------------



## **三、 Hexo的相关配置**
1. 初始化Hexo  
接着上面的操作，输入：
```
    hexo init
    npm install
```
  之后npm将会自动安装你需要的组件，只需要等待npm操作即可。  
*npm默认从国外下载东西，所以网速可能相对来说比较慢，如果实在忍受不了，可以使用以下操作更换npm的源地址*  
```
    npm config set registry https://registry.npm.taobao.org  
    // 配置后可通过下面方式来验证是否成功   
    npm config get registry   
    // 使用cnpm替代默认的npm：
    npm install -g cnpm --registry=https://registry.npm.taobao.org  
```
  *下面你就可以通过cnpm install moduleName来像使用npm一样安装你所需的包了*

2. 首次体验Hexo  
  继续操作，同样是在git中，输入：
```
    hexo g
    hexo s
```
  然后会提示：
```
    INFO Hexo is running at http://0.0.0.0:4000/. Press Ctrl+C to stop.
```
  在浏览器中打开http://localhost:4000/，你将会看到：
  ![](/Img/2017-08-10_20-17.jpg)  

  到目前为止，Hexo在本地的配置已经全都结束了。

  下面会讲解怎样将Hexo与github page 联系起来

---------------------------------------------------------------------------------------------




## **四、 怎样将Hexo与github page 联系起来**
大概分为以下几步 
- 配置git个人信息 
- 配置Deployment

### 配置Git个人信息
*如果你之前已经配置好Git个人信息，请跳过这一个步骤*
1. 设置Git的user name和email：(如果是第一次的话)
  ```
    git config --global user.name "123456"
    git config --global user.email "123456@163.com"
  ```
2. 创建一个 SSH key
  ```
    ssh-keygen -t rsa -C "123456@163.com"
  ```
  代码参数含义：

  * -t 指定密钥类型，默认是 rsa ，可以省略。
  * -C 设置注释文字，比如邮箱。
  * -f 指定密钥文件存储文件名。

  以上代码省略了 -f 参数，因此，运行上面那条命令后会让你输入一个文件名，用于保存刚才生成的 SSH key 代码，如：
  ```
    Generating public/private rsa key pair.
    # Enter file in which to save the key (/c/Users/you/.ssh/id_rsa): [Press enter]
  ```
  当然，你也可以不输入文件名，使用默认文件名（推荐），那么就会生成 id_rsa 和 id_rsa.pub 两个秘钥文件。

  接着又会提示你输入两次密码（该密码是你push文件的时候要输入的密码，而不是github管理者的密码），当然，你也可以不输入密码，直接按回车。那么push的时候就不需要输入密码，直接提交到github上了，如：
  ```
    Enter passphrase (empty for no passphrase): 
    # Enter same passphrase again:
  ```
  接下来，就会显示如下代码提示，如：
  ```
    Your identification has been saved in /c/Users/you/.ssh/id_rsa.
    # Your public key has been saved in /c/Users/you/.ssh/id_rsa.pub.
    # The key fingerprint is:
    # 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com
  ```
  当你看到上面这段代码的收，那就说明，你的 SSH key 已经创建成功，你只需要添加到github的SSH key上就可以了。
3. 添加你的 SSH key 到 github上面去
  1. 首先你需要拷贝 id_rsa.pub 文件的内容，你可以用编辑器打开文件复制，也可以用git命令复制该文件的内容，如：
    ```
        $ clip < ~/.ssh/id_rsa.pub
    ```
  2. 登录你的github账号，从又上角的设置（ Account Settings ）进入，然后点击菜单栏的 SSH key 进入页面添加 SSH key。
  3. 点击 Add SSH key 按钮添加一个 SSH key 。把你复制的 SSH key 代码粘贴到 key 所对应的输入框中，记得 SSH key 代码的前后不要留有空格或者回车。当然，上面的 Title 所对应的输入框你也可以输入一个该 SSH key 显示在 github 上的一个别名。默认的会使用你的邮件名称。  
4. 测试一下该SSH key
  ```
    $ ssh -T git@github.com
  ```
  当你输入以上代码时，会有一段警告代码，如：
  ```
    The authenticity of host 'github.com (207.97.227.239)' can't be established.
    # RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
    # Are you sure you want to continue connecting (yes/no)?
  ```
  这是正常的，你输入 yes 回车既可。如果你创建 SSH key 的时候设置了密码，接下来就会提示你输入密码，如：
  ```
    Enter passphrase for key '/c/Users/Administrator/.ssh/id_rsa':
  ```
  当然如果你密码输错了，会再要求你输入，知道对了为止。  
  注意：输入密码时如果输错一个字就会不正确，使用删除键是无法更正的。  
  密码正确后你会看到下面这段话，如：
  ```
    Hi username! You've successfully authenticated, but GitHub does not
    # provide shell access.
  ```
  如果用户名是正确的,你已经成功设置SSH密钥。如果你看到 “access denied” ，者表示拒绝访问，那么你就需要使用 https 去访问，而不是 SSH 。
### 配置Deployment
  同样在_config.yml文件中，找到Deployment，然后按照如下修改：
  ```
    deploy:
    type: git
    repo: git@github.com:yourname/yourname.github.io.git
    branch: master
  ```
  比如我的仓库的地址是git@github.com:Yuki-14544869/Yuki-14544869.github.io.git，所以配置如下:
  ```
    deploy:
    type: git
    repo: git@github.com:Yuki-14544869/Yuki-14544869.github.io.git
    branch: master
  ```

  ------------------------------------------------------------------------------------------------



  

## **五、 发布文章**
新建一篇博客，执行下面的命令：
![](/Img/2017-08-10_21-51.jpg)
这时候在我的 电脑的目录下 F:\hexo\source\ _posts 将会看到 article title.md 文件  
用MarDown编辑器打开就可以编辑文章了。文章编辑好之后，运行生成、部署命令：
```
    hexo g   // 生成
    hexo d   // 部署
```
当然你也可以执行下面的命令，相当于上面两条命令的效果
```
    hexo d -g #在部署前先生成
```
![](/Img/2017-08-10_21-53.jpg)
部署成功后访问 你的地址，https://yourName.github.io

（这里输入我的地址： https://Yuki-14544869.github.io ),将可以看到生成的文章。
### **踩坑提醒**
1. 注意需要提前安装一个扩展：
  ```
  npm install hexo-deployer-git --save
  ```
  **如果没有执行者行命令，将会提醒**
  ```
  deloyer not found:git
  ```
2. 如果出现下面这样的错误，
  ```
  Permission denied (publickey). 
  fatal: Could not read from remote repository. 
  Please make sure you have the correct access rights and the repository exists.
  ```
  则是因为没有设置好SSH key所致。请参考我上文第四步的SSH key重新设置。
------------------------------------------------------------------------------------------------




## **六、 Next主题的简单配置**
在 Hexo 中有两份主要的配置文件，其名称都是 _config.yml。 其中，一份位于站点根目录下，主要包含 Hexo 本身的配置；另一份位于主题目录下，这份配置由主题作者提供，主要用于配置主题相关的选项。

为了描述方便，在以下说明中，将前者称为 **站点配置文件**， 后者称为 **主题配置文件**。

比如我的电脑下的 F:\hexo 目录下的成为 站点配置文件，F:\hexo\themes\next 目录下的成为主题配置文件。
1. 安装 Next
  在终端窗口下，定位到 Hexo 站点目录下。使用 Git checkout 代码：
  ```
  cd your-hexo-site
  git clone https://github.com/iissnan/hexo-theme-next themes/next
  ```
2. 启用主题
  与所有 Hexo 主题启用的模式一样。 当 克隆/下载 完成后，打开 站点配置文件， 找到 theme 字段，并将其值更改为 next。
  ```
  theme: next
  ```
  到此，Next 主题安装完成。下一步我们将验证主题是否正确启用。在切换主题之后、验证之前， 我们最好使用 hexo clean 来清除 Hexo 的缓存。
  ```
  hexo clean
  ```
3. 验证主题
  首先启动 Hexo 本地站点，并开启调试模式（即加上 –debug），整个命令是 hexo s –debug。 在服务启动的过程，注意观察命令行输出是否有任何异常信息，如果你碰到问题，这些信息将帮助他人更好的定位错误。 当命令行输出中提示出：
  ```
  INFO Hexo is running at http://0.0.0.0:4000/. Press Ctrl+C to stop.
  ```
  此时即可使用浏览器访问 http://localhost:4000 ，检查站点是否正确运行。  
  当你看到站点的外观与下图所示类似时即说明你已成功安装 NexT 主题。这是 NexT 默认的 Scheme —— Muse
  ![](/Img/2017-08-10_22-21.jpg)
  现在，你已经成功安装并启用了 NexT 主题。下一步我们将要更改一些主题的设定，包括个性化以及集成第三方服务。
4. 主题设定
  选择 Scheme  
  Scheme 是 Next 提供的一种特性，借助于 Scheme，NexT 为你提供多种不同的外观。同时，几乎所有的配置都可以 在 Scheme 之间共用。目前 NexT 支持三种 Scheme，他们是：
  ```
  Muse - 默认 Scheme，这是 NexT 最初的版本，黑白主调，大量留白
  Mist - Muse 的紧凑版本，整洁有序的单栏外观
  Pisces - 双栏 Scheme，小家碧玉似的清新
  Scheme 的切换通过更改 主题配置文件，搜索 scheme 关键字。 你会看到有三行 scheme 的配置，将你需用启用的 scheme 前面
  ```
  注释 # 即可。  
  选择 Mist Scheme
  ```
  #scheme: Muse
  scheme: Mist
  #scheme: Pisces
  ```
5. 设置语言
  编辑 站点配置文件， 将 language 设置成你所需要的语言。建议明确设置你所需要的语言，例如选用简体中文，配置如下：
  ```
  language: zh-Hans
  ```
6. 设置 菜单
  菜单配置包括三个部分，第一是菜单项（名称和链接），第二是菜单项的显示文本，第三是菜单项对应的图标。 NexT 使用的是 Font Awesome 提供的图标， Font Awesome 提供了 600+ 的图标，可以满足绝大的多数的场景，同时无须担心在 Retina 屏幕下 图标模糊的问题。

  编辑 主题配置文件，修改以下内容：

  设定菜单内容，对应的字段是 menu。 菜单内容的设置格式是：item name: link。其中 item name 是一个名称，这个名称并不直接显示在页面上，她将用于匹配图标以及翻译。

  菜单示例配置:
  ```
  menu:
    home: /                     //主页
    archives: /archives         //归档页
    #about: /about              //分类页
    #categories: /categories    //标签页
    tags: /tags                 //关于页面
    #commonweal: /404.html      //公益404
  ```
  若你的站点运行在子目录中，请将链接前缀的 / 去掉

  设置菜单项的显示文本。在第一步中设置的菜单的名称并不直接用于界面上的展示。Hexo 在生成的时候将使用 这个名称查找对应的语言翻译，并提取显示文本。这些翻译文本放置在 NexT 主题目录下的 languages/{language}.yml （{language} 为你所使用的语言）。

  以简体中文为例，若你需要添加一个菜单项，比如 something。那么就需要修改简体中文对应的翻译文件 languages/zh-Hans.yml，在 menu 字段下添加一项：
  ```
  menu:
    home: 首页
    archives: 归档
    categories: 分类
    tags: 标签
    about: 关于
    search: 搜索
    commonweal: 公益404
    something: 有料
  ```
  设定菜单项的图标，对应的字段是 menu_icons。 此设定格式是 item name: icon name，其中 item name 与上一步所配置的菜单名字对应，icon name 是 Font Awesome 图标的 名字。而 enable 可用于控制是否显示图标，你可以设置成 false 来去掉图标。

  菜单图标配置示例:
  ```
  menu_icons:
    enable: true
    # Icon Mapping.
    home: home
    about: user
    categories: th
    tags: tags
    archives: archive
    commonweal: heartbeat
  ```
  在菜单图标开启的情况下，如果菜单项与菜单未匹配（没有设置或者无效的 Font Awesome 图标名字） 的情况下，NexT 将会使用 作为图标。

  请注意键值（如 home）的大小写要严格匹配
7. 侧栏
  默认情况下，侧栏仅在文章页面（拥有目录列表）时才显示，并放置于右侧位置。 可以通过修改 主题配置文件 中的 sidebar 字段来控制侧栏的行为。侧栏的设置包括两个部分，其一是侧栏的位置， 其二是侧栏显示的时机。

  设置侧栏的位置，修改 sidebar.position 的值，支持的选项有：
  ```
  left - 靠左放置
  right - 靠右放置
  ```
  目前仅 Pisces Scheme 支持 position 配置。影响版本5.0.0及更低版本。
  ```
  sidebar:
    position: left
  ```
  设置侧栏显示的时机，修改 sidebar.display 的值，支持的选项有：
  ```
post - 默认行为，在文章页面（拥有目录列表）时显示
always - 在所有页面中都显示
hide - 在所有页面中都隐藏（可以手动展开）
remove - 完全移除
sidebar:
  display: post
  ```
  已知侧栏在 use motion: false 的情况下不会展示。 影响版本5.0.0及更低版本。
8. 设置头像
  编辑 站点配置文件， 新增字段 avatar， 值设置成头像的链接地址。其中，头像的链接地址可以是：
  ```
http://example.com/avtar.png    //完整的互联网 URI
/images/avatar.png              //将头像放置主题目录下的 source/images/ 目录下 
  ```
9. 设置作者昵称
  编辑 站点配置文件， 设置 author 为你的昵称。
10. 站点描述
  编辑 站点配置文件， 设置  description
  字段为你的站点描述。站点描述可以是你喜欢的一句签名:)

---------------------------------------------------------


## **参考文献**
1. [手把手教你用Hexo+Github 搭建属于自己的博客](http://blog.csdn.net/gdutxiaoxu/article/details/53576018)
2. [从NPM到CNPM](http://blog.csdn.net/v2810769/article/details/52585662)
3. [ github设置添加SSH](http://blog.csdn.net/binyao02123202/article/details/20130891)