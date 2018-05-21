# homework4（group homework）

## 1. group member  
| Name | github Nick Name | Student ID | Scope |   
| - | :-: | :-: | :-:|  
| 胡雨奇 | ReimuYk | 516030910257 |  Build APP |  
| 丁丁 | derFischer | 515015910005 | PPT |   
| 罗宇辰 | 592McAvoy | 516030910101 | PPT |   
| 陈诺 | 199ChenNuo | 516030910199 | README |  

注：所有同学都完成了CI/CD环境的搭建，分工仅体现在本次作业中  

----

## 2. CI（*Continuous Integration*）  
### 2.1 What's CI  
CI的中文名是**持续集成**，意为，新的代码一经提交就进行对新代码的构建与测试。根据测试结果可以立即确定新代码与原代码是否正确的集成在一起。  
     
![CI image](https://github.com/ReimuYk/hw-CI-CD/blob/master/images/CI.jpg)  

### 2.2 Why CI  
*持续集成是一种软件开发实践，即团队开发成员经常集成他们的工作，通常每个成员每天至少集成一次，也就意味着每天可能会发生多次集成。每次集成都通过自动化的构建（包括编译，发布，自动化测试)来验证，从而尽快地发现集成错误。* 
  
持续集成带来的好处  
- 减少风险，减少重复过程  
- 任何时间、任何地点生成可部署的软件  
- 增强项目的可见性  
- 建立团队对开发产品的信心  

### 2.3 How CI  
#### 2.3.1 Tool: *Jenkins*  
Jenkins 是一个开源项目，提供了一种易于使用的持续集成系统，使开发者从繁杂的集成中解脱出来，专注于更为重要的业务逻辑实现上。同时 Jenkins 能实施监控集成中存在的错误，提供详细的日志文件和提醒功能，还能用图表的形式形象地展示项目构建的趋势和稳定性  
#### 2.3.2 CI环境搭建   
1. 新建任务  
在Jenkins左侧菜单中选择*新建任务*来新建一个任务  
2. 配置项目  
在任务的顶部导航菜单中*General*中配置项目  
3. 源码管理  
在任务的顶部导航菜单中的*源码管理*中使用git、SVN等工具进行源码管理  
4. 配置触发器  
    - 定时构建  
    在指定时间进行项目构建（不关心源码是否发生变化）  
    - 轮询SCM  
    定时检查源码变更，如果存在更新那么执行构建动作  
5. 配置构建命令  
在构建下的输入框内输入需要的构建命令  
6. 构建  
在Jenkins左侧导航菜单中选择*立即构建*来构建项目  
#### 2.3.3 每一次部署的操作流程  
1. 向版本控制库提交新代码  
2. 自动化构建  
    - 编译  
    - 分发  
    - 部署  
    - 测试  
3. 修改代码  
4. 构建成功  

### 2.4 其他CI工具  
- Travis CI
- ...

----
## 3 CD (*Continuous Delivery* & *Continuous Deployment*)  
### 3.1 What's CD
CD包含了**持续交付**和**持续部署**。  
持续交付(*Continuous Delivery*)在持续集成的基础上，将集成后的代码部署到更贴近真实运行环境的「类生产环境」(*production-like environments*)中。  
![CDelivery-image](https://github.com/ReimuYk/hw-CI-CD/blob/master/images/C-Delivery.jpg)  
持续部署(*Contiuous Deployment*)则是在持续交付的基础上，把部署到生产环境的过程自动化。  
![CDeployment-image](https://github.com/ReimuYk/hw-CI-CD/blob/master/images/C-Deployment.jpg)  
持续交付与持续部署的区别： 
持续部署的模式下，所有的变更都会被自动部署到生产环境中，而持续交付中，所有的变更都**可以**被部署到生产环境中，但出于业务考虑也可以选择**不部署**。因此要实施持续部署时，要先实施持续交付。  
本次作业选用的是持续部署。
### 3.2 Why CD  
*持续部署是通过自动化的构建、测试和部署循环来快速交付高质量的产品。某种程度上代表了一个开发团队工程化的程度，毕竟快速运转的互联网公司人力成本会高于机器，投资机器优化开发流程化相对也提高了人的效率，让生产效率最大化。* 
  
持续部署带来的好处
- 快速发布  
- 缩短 编码->测试->上线->交付 的迭代周期  
### 3.3 How CD  
#### 3.3.1 Tool: *heroku*  
heroku是一个免费的，支持多种语言的开源平台。开源借助heroku完成代码的构建、运行与持续部署。  
#### 3.3.2 准备工作  
1. 注册heroku  
    进入官网注册即可。注册时需要开启代理。  
2. 安装heroku-cli、nodejs git  
    在官网选择合适本地系统的heroku-cli，通过命令
    - <code>node --version</code>  
    - <code>npm --version</code>  
    - <code>git --version</code>  
    可以检查本地是否安装了需要的一些软件  
3. 登录  
    <code>heroku login</code>
4. 创建仓库  
    <code>heroku create</code>  
5. 上传 & 部署  
    <code>git push heroku master</code>  
6. 查看部署完成的项目  
    <code>heroku open</code>  
7. 修改后，暂存 & 提交  
    <code>git add .  
    git commit</code>  
8. 推送  
    <code>git push</code>  
### 3.4 Other CD Options  
- GCE  
- AWS  
- ...  

----

## 4. 参考资料  
1. [ Jenkins工具 ]之一：持续集成和jenkins入门介绍  
https://www.2cto.com/kf/201609/544550.html  
  
2. Jenkins+Node.js持续集成  
https://www.jianshu.com/p/64b498304d07  
  
3. Jenkins+Github持续集成  
https://www.jianshu.com/p/b2ed4d23a3a9  
  
4. Jenkins基础入门-7-创建一个Project的基本过程  
https://blog.csdn.net/u011541946/article/details/78014179  
  
5. docker与CI/CD  
https://blog.csdn.net/eugenelee2096/article/details/73332615  
  
6. CI/CD持续集成/持续部署 敏捷开发  
https://blog.csdn.net/qq_32261399/article/details/76651376  
  
7. Heroku官方文档  
https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction  

