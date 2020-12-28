<div align="center">
   <img width="160" src="http://img.mamoe.net/2020/02/16/a759783b42f72.png" alt="logo"></br>


   <img width="95" src="http://img.mamoe.net/2020/02/16/c4aece361224d.png" alt="title">

----
Mirai 是一个在全平台下运行，提供 QQ 协议支持的高效率机器人库

这个项目的名字来源于
<p><a href = "http://www.kyotoanimation.co.jp/">京都动画</a>作品<a href = "https://zh.moegirl.org/zh-hans/%E5%A2%83%E7%95%8C%E7%9A%84%E5%BD%BC%E6%96%B9">《境界的彼方》</a>的<a href = "https://zh.moegirl.org/zh-hans/%E6%A0%97%E5%B1%B1%E6%9C%AA%E6%9D%A5">栗山未来(Kuriyama <b>Mirai</b>)</a></p>
<p><a href = "https://www.crypton.co.jp/">CRYPTON</a>以<a href = "https://www.crypton.co.jp/miku_eng">初音未来</a>为代表的创作与活动<a href = "https://magicalmirai.com/2019/index_en.html">(Magical <b>Mirai</b>)</a></p>
图标以及形象由画师<a href = "">DazeCake</a>绘制
</div>

# mirai-login-solver-selenium

[ ![Download](https://api.bintray.com/packages/karlatemp/mirai/mirai-login-solver-selenium/images/download.svg) ](https://bintray.com/karlatemp/mirai/mirai-login-solver-selenium/_latestVersion)
![Gradle CI](https://github.com/project-mirai/mirai-login-solver-selenium/workflows/Gradle%20CI/badge.svg?branch=master)

该模块负责处理滑动验证码, `mirai-core` 并不强制要求使用 `mirai-login-solver-selenium`

使用时添加该模块至运行时 classpath 即可

## 运行平台支持

| OS      | Browser | 是否支持 |
| ------- | -----   | -----  |
| Windows | Chrome  | Yes    |
| Windows | Firefox | Yes    |
| CentOS  | Firefox | Yes    |
| Linux   | Firefox | 未测试  |
| Linux   | ------- | No     |
| MacOS   | ------- | No     |

```text
Windows - Chrome  - test ok
Windows - Firefox - test ok
CentOS  - Firefox - test ok
Linux   - Not tested
MacOS   - Not in support - No device
```

## 在 MiraiConsole 中使用

### 使用 [Mirai Console Loader](https://github.com/iTXTech/mirai-console-loader) 安装 `Mirai login solver selenium`

* `MCL` 支持自动更新插件，支持设置插件更新频道等功能

`./mcl --update-package net.mamoe:mirai-login-solver-selenium --set-channel nightly --set-type plugins`

### Download

```shell script
# 注: 自行更换对应版本号

# Download mirai-login-solver-selenium

curl -L https://maven.aliyun.com/repository/public/net/mamoe/mirai-login-solver-selenium/1.0-dev-4/mirai-login-solver-selenium-1.0-dev-4-all.jar -o mirai-login-solver-selenium-1.0-dev-4.jar

```

## 手动完成滑动验证

### 环境准备

在 `mirai` 运行时中添加 JVM 属性 `mirai.slider.captcha.supported` (添加参数 `-Dmirai.slider.captcha.supported`)
以确认手动完成滑动验证

准备一台拥有桌面系统的电脑, 并且需要安装支持 DevTools 的任意浏览器 (Eg `Chrome`, `Firefox`)

开启一个新的隐私窗口, 打开 `DevTools`, 并将运行模式切换为 `Android`

![](images/img1.png)

在该窗口打开滑动验证码页面, 并将 `DevTools` 的选项卡切换到 `Console`,

另外打开 [captcha.inject.js](src/main/resources/mirai-selenium/captcha.inject.js), 点击 `Raw` 按钮
将该文件内容完整复制进入 `DevTools > Console`, 然后按下 回车(`Enter`)

![](images/img2.png)

完成滑动验证码, 将会显示需要传回的 ticket

![](images/img3.png)

### 其他资料

- [go-cqhttp/docs/slider.md](https://github.com/Mrs4s/go-cqhttp/blob/master/docs/slider.md)
