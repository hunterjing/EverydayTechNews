# EverydayTechNews(每日科技新闻)

每天早晨自动发送科技新闻到你的邮箱。

点击[这里](https://mailist.nowscott.top/)订阅每日科技早报

[![technews][action-image]][action-url]
[![forks][forks-image]][forks-url]

## 创建初衷

小时候，家中的长辈常订阅报纸。然而，随着时代的变迁，报纸逐渐退出我们的视野，被无处不在的互联网新闻取而代之。

在这个广袤的信息海洋中，琳琅满目且杂乱无章，包含了大量的信息。但实际上，我对于关注的内容并不多。

因此，我创建了这个工具，每天自动将科技新闻发送到我的邮箱。

这样，我就不再淹没在大量信息中，而是像过去阅读报纸时一样，只专注阅读我最感兴趣的部分。

## 工具介绍

因为不想暴露我的个人邮箱，所以真正每天在运行的工具在另外一个私有库中，本项目的目的在于帮助同样有这个需求的朋友们搭建这样一个小工具。

这个自动发送新闻到邮箱的小工具是基于python开发的，主函数是根目录下的main.py文件，然后配置文件是根目录下的config.json。

## 工具部署

在2023年7月19日的更新后，部署将变的更加简单！

由于我将私密性的信息全部放到了仓库的秘密变量中，所以现在可以通过Fork的形式来进行部署。

首先Fork本仓库：https://github.com/NowScott/EverydayTechNews

接下来在设置（Settings）中找到Secrets and variables，点击下方的Actions，在右侧你可以看到一个蓝色的按钮写着New repositorys secret，点击这个按钮，新建4个secret，分别是：
```
SENDING_ACCOUNT: send_email@example.com
SENDING_PASSWORD: smtp_password
SERVER: smtp.163.com
RECEIVER_LIST: receiver1_email@example.com,receiver2_email@example.com
```

1. 前两个分别是要使用的邮箱和SMTP的密钥

2. 关于服务器（server），它取决于您使用的电子邮件地址。这里我提供了使用网易163邮箱地址的示例。其他常用电子邮件提供商的服务器地址列在最后。

3. 接收者（receivers）用“,”间隔开，不仅可以添加自己的邮箱地址，也可以添加朋友的邮箱地址。这样可以共享和讨论相互感兴趣的内容。

更改完配置信息之后找到.github/workflows/technews.yml这个文件

这部分代码的含义是在格林尼治时间（UTC）的每天22:30执行，换算成北京时间需要加8个小时，即早上6:30左右开始执行，然而并非完全准确。你可以根据自己的需求对这部分时间进行更改，有关 cron 的详细规则，请参考这个网站：https://tool.lu/crontab/

接着在上方找到Action，左侧点击technews，右侧找到run workflow尝试运行，如果在下方的运行中没有报错而且邮件能正常发送，那么就成功了。

但是如果你需要其他版块的新闻，可能要麻烦一些。

由于其他版块的排版和科技的不尽相同，所以更换版块意味着要重新写页面解析部分的代码，去找到符合你口味的新闻，我这里就不过多赘述了。


[action-url]:https://github.com/NowScott/EverydayTechNews/actions/workflows/technews.yml "Action State"
[action-image]:https://img.shields.io/github/actions/workflow/status/NowScott/EverydayTechNews/technews.yml?label=Action
[forks-url]:https://github.com/NowScott/EverydayTechNews/forks
[forks-image]:https://img.shields.io/github/forks/NowScott/EverydayTechNews?label=Forks