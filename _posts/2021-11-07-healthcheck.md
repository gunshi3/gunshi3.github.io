---
title: 'HealthCheck'
date: 2021-11-07
permalink: /posts/2021/11/healthcheck
tags:
  - python
  - repo
  - healthCheck
---

# <img src="https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=69948112,3892466283&fm=26&gp=0.jpg" alt="hnu" width = "80" height = "77" /> HNU 自动打卡 HealthCheck

#### 更新日志 Log :bulb:

- :100: :新建`auto`分支，增加`GitHub Action`自动部署功能，录制Bilibili教程，请访问：——`2021/10/30`

- :1st_place_medal: 增加了用户信息加密功能，新建`dev`默认分支（该分支包含加密功能，如不在意用户信息，请用master分支部署） ——`2021/10/29`

- :2nd_place_medal: 完善了`master`分支管理，优化了程序环境部署，增加了ascii艺术字。 					——`2021/03/03`

- :3rd_place_medal:新建`version1-outdate`分支，完成核心功能，`version1-outdate`分支现已过时 ——`2021/01/01`

- 项目地址：[HealthCheck](https://github.com/DelinQu/HealthCheck/)

## 简介 :bulb:

> HealthCheck基于**python**搭建，它每天尝试三次打卡，成功后会**邮箱提醒**你打卡成功; 如果3次尝试仍未成功，HealthCheck会邮件提醒您手动打卡，并将**错误日志**发送给开发者（yourself）.
>
> HealthCheck分离代码和配置文件，你可以很方便地通过修改配置文件来达到**切换运行**环境的目的。同时你也可以通过向用户列表文件中添加新的打卡用户信息来进行**批量打卡**。mapper文件夹下的接口与主程序分离，可以随时**测试接口**。
>
> HealthCheck通过ASP定时框架来实现定点打卡，一旦你将HealthCheck部署到服务器，即可解放双手，高效生活。
>
> 现已添加`auto`分支，无需手动部署，使用`GitHub Action`即可完成自动打卡。

- **声明** :triangular_flag_on_post:
> **使用此项目完成打卡的同学有义务保证信息的准确性！如若出现身体异常，请务必配合疫情防控工作，完成异常信息上报！**


## 分支介绍

- :100: `auto`分支：`GitHub Action`自动部署分支+默认分支，Bilibili教程。（自动部署推荐）.
- :1st_place_medal: `dev`分支：包含用户信息`加密功能`的`手动部署`分支，如不在意用户信息，请用master分支部署.
- :2nd_place_medal: `master`分支：手动部署主分支，相较`dev` 手动部署更加简便。（手动部署推荐）.
- :3rd_place_medal:`version1-outdate`：已过时的分支。（不推荐）.

**目录结构 :trident:**

>  目录结构
```zsh
.
├── config						
│   └── appConfig.py            	# 配置文件
├── data
│   ├── .img                    	# 验证码图片缓存
├── main.py                      	# 程序入口
├── mapper                       	# 方法接口
│   ├── commit.py               	# 提交打卡信息表单
│   ├── getImage.py             	# 下载保存验证码图片
│   ├── ksdemo.py               	# 验证码图像识别
│   ├── login.py                	# 登陆
│   └── sendEmail.py            	# 邮件发送
├── README.md                    	# README
└── requirements.txt             	# 安装依赖		
```



## Quick Start For `auto` branch

>  本README文件对应`auto`分支（手动部署请参考相应分支的README），使用此程序需要简单3步, 您也可以参考此视频：

<video src="https://delinqu.github.io/files/HealthCheckVideos.mp4" width="960" controls="controls">
your browser does not support the video tag
</video>

### 1. 注册帐号 (Please skip it if you have one)

- [Github](https://github.com)

![image-20211030224537969](https://i.loli.net/2021/10/30/BaYtk3RJwVP2DGT.png)

### 2. Fork 到自己的仓库

![image-20211031084432461](https://i.loli.net/2021/10/31/li5nkzh2xY89X7b.png)

### 3. 填写Secrets信息并开放Github Action

创建Secrets字段信息，包括`Ge ren men hu`帐号：`YOUR_USERNAME`，密码`YOUR_PASSWD` 以及接收打卡日志的邮件`YOUR_EMAIL`，依次点击 Settings >  Secrets > New repository secret > `填写Secrets` > `创键完成` .

- 创建Secrets

![image-20211031085356309](https://i.loli.net/2021/10/31/kWAUnS6fYwEc5qJ.png)

- 填写Secrets（三个）

![image-20211031084925621](https://i.loli.net/2021/10/31/Ic8i9we4ubEsOrv.png)

- 创建完成

![image-20211031085436836](https://i.loli.net/2021/10/31/Qh3fnYzRkSi4aqw.png)

创建完成后，依次点击 `Actions` > `Workflows` > `Enable workflow` 即可开始定时打卡。

![image-20211031085916426](https://i.loli.net/2021/10/31/QgDtFwcypI6oHBl.png)


## 运行`HealthCheck`

通过`Quick Start`后您已经完成了所有部署，静候每天凌晨`00:30`自动打卡邮件即可。如果您想要手动运行workflow，可以点击 Health Check Action > Run workflow > `Run workflow` 手动测试一次。

![image-20211031090153765](https://i.loli.net/2021/10/31/aDAgJOkIUWpMGeX.png)

进入 Health Check Action > Deploy > Check  查看打卡日志。

![image-20211031090510314](https://i.loli.net/2021/10/31/HGSTnQ1384iwdWK.png)

今日已提交过打卡信息，否则将会在打卡成功后发送邮件提醒。

![image-20211031090633598](https://i.loli.net/2021/10/31/hcqb469tTynVSOD.png)



## :ice_cream:More info [非必须]

`config/appConfig`配置文件信息也是可以按照个人需要修改的。在该文件中您可以重新配置发件人信息，开发者邮件信息，fast图片识别账户密码，打卡地点等信息。

```python
# 邮箱配置
senderEmail = 'qdl.no-reply@foxmail.com'
sender = "qdl-dev"
devEmail = 'qdl.no-reply@foxmail.com'
AuthCode = 'nprgjutnqcdedhdc'
sucessMsg = '   今日打卡成功，打卡时间：'
failMsg = '     我们对您的账户进行了3次打卡尝试，由于某些原因导致打卡失败，请于今日手动完成打卡。\
您可以尝试联系此邮箱以解决打卡失败的问题。祝您生活愉快！\n发件人： '+senderEmail                    # 格式无需调整

# http://fast.95man.com/注册使用
k95Username = 'qdl-dev'
k95Passwd = 'qdl-dev'

# 用户信息
RealAddress,RealCity,RealCounty,RealProvince,BackState,MorningTemp,NightTemp = \
	"湖南大学","长沙市","岳麓区","湖南省",1,36.3,36.3
```

`.github/workflows/python-publish-auto.yml`工作流配置文件中您可以根据需要修改自动打卡时间：

```yaml
on:
  push:
    branches: [auto]
  pull_request:
    branches: [auto]
  schedule:
    - cron:  '30 16 * * *'	# UTC世界时，修改请参考Github Action Doc
  workflow_dispatch:
```

> :warning: 注意
>
> fast图片识别默认使用的是我注册的一个私人帐户qdl-dev，而fast图片识别只能提供单日100次识别接口，如果使用该仓库的人数达到上限可能打卡失败。
>
> 更详细的:ice_cream:More info 信息请参考 [Master分支](https://github.com/DelinQu/HealthCheck/tree/master)
