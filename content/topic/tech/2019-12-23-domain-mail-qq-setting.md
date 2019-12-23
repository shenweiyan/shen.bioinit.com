---
title: QQ 邮箱设置自定义域名邮箱
type: post
topic/tags: ["others", "运维"]
date: 2019-12-23T05:35:37.000Z
category: 运维
published: true
---

**首先理解一下，qq 邮箱设置域名邮箱，其实就是给你的 qq 邮箱起个别名而已，可以用自定义邮箱去收发邮件，但是邮件还是在 qq 邮箱里。**

**

## 1. 创建域名邮箱

域名邮箱的主页是：[http://domain.mail.qq.com/](http://domain.mail.qq.com/)，这也是 QQ 域名邮箱直接登录的地址。我们直接在浏览器打开，在页面的左边栏就可以看到域名邮箱的创建入口。我们需要先通过 QQ 邮箱登陆。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577080482207-4a6823f7-5974-4da5-8e49-219d9662bce7.png#align=left&display=inline&height=623&name=image.png&originHeight=623&originWidth=818&size=83336&status=done&style=none&width=818)

登录后，选择创建域名邮箱。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577080618503-c44d8f5c-80e3-445f-9205-7e2092e6e865.png#align=left&display=inline&height=458&name=image.png&originHeight=458&originWidth=851&size=60493&status=done&style=none&width=851)


## 2. 填写自己的域名


![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577080710339-a93739ba-ae51-46f6-9949-344ab67970cb.png#align=left&display=inline&height=302&name=image.png&originHeight=302&originWidth=872&size=46228&status=done&style=none&width=872)

点击下一步，出现下面的页面，选择我们域名的提供商。小编的邮箱如果是在阿里云注册，所以选择其他提供商。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577080800210-21a9926c-b022-4029-80ea-f6d5bf7b6499.png#align=left&display=inline&height=463&name=image.png&originHeight=463&originWidth=785&size=74346&status=done&style=none&width=785)


## 3. 添加 CNAME 和 Mx 记录


点击下一步，会出现下面的页面，根据提示添加 CNAME 和 Mx 记录。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577081245774-bf5bd0a9-b21e-41a5-9f44-6818f9f6132d.png#align=left&display=inline&height=552&name=image.png&originHeight=552&originWidth=790&size=73999&status=done&style=none&width=790)


### 3.1 域名解析

这里以阿里云为例，登陆阿里云账号，选择对应域名的解析，点击"**添加记录**"。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577081811908-b8fc34de-3c4a-4d78-9802-ef495dbfc1e5.png#align=left&display=inline&height=236&name=image.png&originHeight=236&originWidth=645&size=22161&status=done&style=none&width=645)




### 3.2 添加记录

添加两条记录，将前面的内容直接复制过来，其余的默认就好。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577082738823-96d1ea8c-e12f-4bbf-b5f8-e37bbaf03385.png#align=left&display=inline&height=424&name=image.png&originHeight=424&originWidth=592&size=18674&status=done&style=none&width=592)

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577082913294-55807943-f3f0-41f9-b11e-aa679da49900.png#align=left&display=inline&height=478&name=image.png&originHeight=478&originWidth=587&size=20508&status=done&style=none&width=587)




## 4. 提交验证

返回 qq 邮箱刚才界面，点击提交验证。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577083032992-2157d612-3ded-42ab-a8b1-29346e20b820.png#align=left&display=inline&height=280&name=image.png&originHeight=280&originWidth=787&size=35490&status=done&style=none&width=787)

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577083122693-9071945e-9d0e-4342-be3d-c218c6005257.png#align=left&display=inline&height=275&name=image.png&originHeight=275&originWidth=706&size=18898&status=done&style=none&width=706)


## 5. 添加成员

添加一个成员（注意，在添加新成员之前，需要首先设置域名邮箱的管理员），名字随便起，就跟你在别的平台注册邮箱一样。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577083898733-2253da04-beda-461f-97ab-3fabf6542a92.png#align=left&display=inline&height=429&name=image.png&originHeight=429&originWidth=673&size=29675&status=done&style=none&width=673)

新建成员，点击"确定" 完成后。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577084479055-0435dae2-bc32-4651-b67f-a098e0ca9977.png#align=left&display=inline&height=220&name=image.png&originHeight=220&originWidth=827&size=24479&status=done&style=none&width=827)

进入新创建用户的 QQ 邮箱，在收到的域名邮箱确认邮件中，点击 "**接受这个邮箱账号**"，即可完成最后的创建。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577084826009-fc42b95e-ffd3-4d33-afc1-d8d3a5a006ee.png#align=left&display=inline&height=403&name=image.png&originHeight=403&originWidth=976&size=115382&status=done&style=none&width=976)


最后，我们再次回到新创建用户 qq 邮箱**设置 **–>**账户**–>**账号管理**，此时就会出现刚刚设置的域名邮箱。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577085255696-9c855e06-26c8-4a65-a679-809c9656e2d2.png#align=left&display=inline&height=242&name=image.png&originHeight=242&originWidth=888&size=27837&status=done&style=none&width=888)



## 6. 主显账号

QQ 邮箱默认是以 xxx.qq.com 作为你的发信账号和主显账号，如果我们想在打开 QQ 邮箱的时候第一眼看到的就是自己的域名邮箱，我们可以这样设置。

通过 QQ 邮箱的"**设置 → 账户 → 账号管理 → 默认发信账号**"，选择你想要的邮箱。

**![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577085995742-5adbbfed-49ea-4c60-b1d8-57ac82628638.png#align=left&display=inline&height=345&name=image.png&originHeight=345&originWidth=481&size=22174&status=done&style=none&width=481)**

**

**"保存更改"** 后，你就可以看到自己的默认 QQ 邮箱已经变成了你所设置的域名邮箱。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1577086191939-db81aef0-93d1-404b-900f-688535c21469.png#align=left&display=inline&height=337&name=image.png&originHeight=337&originWidth=833&size=66617&status=done&style=none&width=833)

到这里，QQ 邮箱的自定义域名邮箱就全部设置完成了。接下来，你就可以使用 163 或者其他邮箱，对新创建的域名邮箱收发邮件进行测试验证一下。

最后想说的是，在阿里云，一个 `.cn` 域名一年才 29 块钱，而 `.top`  、 `.site` 之类域名一年更是 10 块钱不到，更不要说价格更加便宜的腾讯云域名，所以如果你想拥有一个自己专属的域名，除了备案可能过程稍微繁琐点，其他门槛都是极低的。

