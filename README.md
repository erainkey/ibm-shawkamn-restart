# ibm_cf_restart-actions
使用Github Actions定时重启IBM Cloud Foundry应用程序

## 使用之前，有几项准备工作
1. IBMCloud的账号密码
2. Cloud Foundry应用程序的区域
3. Cloud Foundry应用程序的名称

## 使用方法

### 1 Fork此仓库

### 2 设置此仓库的变量

![](http://tu.yaohuo.me/imgs/2020/06/750d9a9a867979ce.png)

依次添加名为**MAIL**、**PWD**、**RGN**、**CFNAME**的变量  
值分别为邮箱(账号)、密码、区域、Cloud Foundry应用程序的名称(同时是链接前缀)  

### 3 确定Github Action正常工作

~~点击修改任意文件后提交~~对自己的仓库点击**Star**使Actions激活  

此前，可能需要点击**Pull requests**与**Projects**之间的**Action**进去点一下允许之类的

### 变量示例
MAIL====>12345@qq.com  
PWD====>123456QWER  
RGN====>us-south  
CFNAME====>cxkjntm  

## 其他

配置完毕，将会在每天的04:15重启Cloud Foundry应用程序  

如果你不需要重启太频繁，请到**你自己仓库**的.github/workflows/run.yml文件  
修改**- cron:**这一行  

示例：
#### 1 UTC+0时区，每天20:15(即默认)  
```
schedule:
    - cron: 15 20 * * *
```
#### 2 UTC+0时区，每月1、4、7、10、13、16、19、22、25、28、31号的20:15(+3)  
```
schedule:
    - cron: 15 20 1/3 * *
```
#### 3 UTC+0时区，每月1、8、15、22、29号的20:15(+7)  
```
schedule:
    - cron: 15 20 1/7 * *
```
#### 4 UTC+0时区，每周一的20:15  
```
schedule:
    - cron: 15 20 * * 1
```
#### 5 UTC+0时区，每周一、周四的20:15(+3)  
```
schedule:
    - cron: 15 20 * * 1/3
```
UTC+0的20:15就是UTC+8的04:15

## 修改
IBMCloud Cli新版本有问题，受启发替换成CF Cli了，用法和原来一样(2020-08-28)  
