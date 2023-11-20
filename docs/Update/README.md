﻿﻿
## 更新日志


### 2023-11-15

重大更新：项目升级到 `.net8.0` 版本；

### 2023-10-28

系统更新说明书：[《Blog.Core 23年第三季度更新说明书！》](https://mp.weixin.qq.com/s/INaIckCNkLclkxbHZ49bCw)；  
因为更新内容较多，故统一写到一篇文章中。 

### 2023-06-10

系统更新说明书：[《Blog.Core 23年第二季度更新说明书！》](https://mp.weixin.qq.com/s/2raJtLyPTOouwND-2Ihoww)；  
因为更新内容较多，故统一写到一篇文章中。  

### 2023-02-18

系统更新说明书：[《Blog.Core 23年第一季度更新说明书！》](https://mp.weixin.qq.com/s/dPJix2oqPYOf-wgOiwJ3GQ)；  
因为更新内容较多，故统一写到一篇文章中。  

### 2023-01-20

重大更新：项目升级到 `.net7.0` 版本；

### 2022-11-27

系统更新说明书：[《Blog.Core 第四季度开源更新说明书》](https://mp.weixin.qq.com/s/32u37iei9frIhVszium8VA)；  
因为更新内容较多，故统一写到一篇文章中。  

### 2022-04-10

重要功能增加：框架集成部门权限；

### 2022-01-29

功能增加：项目增加 `Admin` 界面快速预览；

### 2021-12-04

更新：项目开发插件，给 `swagger` 加权；

### 2021-10-09

重大更新：项目升级到 `.net6.0` 版本；

### 2021-08-21

重要功能增加：项目增加 `Apollo` 配置中心；

### 2021-08-03

重要功能增加：项目增加 `ES` 搜索，增加 `Serilog` 使用 `tcp` 的方式自定义格式化,写入 `elk` 的实现；

### 2021-06-28

功能增加：项目增加 `nacos` 配置，支持将项目注册到 `nacos` 服务中心，搭建微服务之子服务；

### 2021-06-04

小功能更新：执行的时候，将 `Sql` 日志输出到控制台，方便查看，支持配置文件关闭；

### 2021-05-01

组件更新：多项日志中间件，由自写组件，转为使用`serilog`组件记录日志；  

### 2021-03-03

项目目录调整：新增测试文件夹和模板文件夹；   

### 2021-02-09

重大项目更新：新增建行聚合支付；    

### 2021-01-11

更新：优化任务调度功能，新增暂停和停止；

### 2020-12-02

更新：新增调用`MongoDB`功能，功能可用待完善中；


### 2020-11-19
> 重大内容更新：更新项目模板 `Update Blog.Core.Webapi.Template.2.5.2.nupkg`  
> 主要内容：1、泛型主键；2、通过测试中间件；3、`RabbitMQ`消息队列


### 2020-11-18

项目更新：新增`RabbitMQ`消息队列和`EventBus`事件总线，功能可用待完善。  


### 2020-11-11

项目重大更新：更新至`.NET 5.0`。    


### 2020-11-05

项目更新：增加`测试用户`中间件，通过一键操作可以跳过权限限制，方便调试，文章[使用测试用户中间件](http://apk.neters.club/api/Blog/GoUrl?id=156)。    



### 2020-10-11

项目更新：设计泛型主键功能，可以在项目初始化的时候设计主键类型。    



### 2020-09-18

项目更新：更新项目模板 `Update Blog.Core.Webapi.Template.2.2.3.nupkg`  。    
> 1、增加 `Redis` 消息队列功能；   



### 2020-09-04

项目更新：增加 `Redis` 消息队列功能；  


### 2020-08-06

项目更新：更新项目模板 `Update Blog.Core.Webapi.Template.2.2.0.nupkg`  。    
> 1、根据解决方案名，来自动导入model；  
> 2、单独封装服务扩展层 `Blog.Core.Extensions` ；  
> 3、代码生成器，支持控制器文件的生成；  
> 4、弱化仓储层，用泛型仓储基类注入服务；  




### 2020-08-01

> 重大结构更新：弱化仓储层，通过泛型仓储基类，来实现仓储服务注入，并去掉`Blog.Core.IRepository` 接口层；  

### 2020-07-03

> 更新：`DbFirstController` 生成四层文件，目前新增支持 `控制器Controller` 文件的输出；


### 2020-06-22

> 项目更新：将服务扩展和自定义中间件，单独封装一层 `Blog.Core.Extensions` ，更解耦。



### 2020-06-08

> 简单项目更新：生成数据库表结构的时候，利用反射机制，自动生成固定命名空间 `Blog.Core.Model.Models` 下的全部实体.  
> 同时判断表是否存在，如果存在下次不再重复生成。


### 2020-06-06

项目更新：更新项目模板 `Update Blog.Core.Webapi.Template.2.1.0.nupkg` [1a726f8](https://github.com/anjoy8/Blog.Core/commit/1a726f890e527c978982071462e82db4478632f0)，更新项目即可 。    
> 1、配置内容展示到控制台；  
> 2、简化封装 `Startup.cs` 类文件；  
> 3、`DbFirst` 模式支持多库模式；  
> 4、`Log4net` 讲异常和 `Info` 分开；  
> 5、修复 `BlogLogAop` 偶尔卡顿问题；  
> 6、将生成种子数据和任务调度功能，封装到中间件；  
> 7、获取当前项目在服务器中的运行信息；  
> 8、删除所有的不需要的 `using` 指令；  




### 2020-05-29
项目启动开启 `QuzrtzNet` 调度任务，并且在 `Admin` 后台管理中配置操作界面；  
> 内容更新：封装生成种子数据的入口方法；   



### 2020-05-12
修复：支持多库模式下，生成项目模板代码 `DbFirstController`  [102c6d6](https://github.com/anjoy8/Blog.Core/commit/102c6d6bfcafd06bf5241844759dea5e7a6815da) 
> 注意：`T4` 模板不能此功能，一次只能一个数据库，且只能 `SqlServer`


### 2020-05-07
> 重大内容更新：更新项目模板 `Update Blog.Core.Webapi.Template.2.1.0.nupkg`  [7f64fde](https://github.com/anjoy8/Blog.Core/commit/7f64fde5507f7a8572372dcadb6af5110bd37d68) 


###  2020-05-06  
> 重大内容更新：优化Log4Net使用方案,完美配合 `NetCore` 官方的 `ILogger<T>`， [ecaffb6](https://github.com/anjoy8/Blog.Core/commit/ecaffb66bdf10a90c087d01e6e817e54f23a97d4)  


### 2020-05-01

> 重要内容更新：配合Admin全部完成按钮级别权限，更新初始化种子数据

### 2020-04-27

增加功能：配合前端Admin，增加页面 `KeepAlive` 功能；  
增加功能：增加 `Sql` 语句查询Demo，支持返回 `DataTable`；


### 2020-04-25

增加功能：`Http api` 接口调用，满足微服务需求
> 重要内容更新：优化 `Appsettings.app()` 方法，通过官方 `IConfiguration` 接口来获取DBS连接字符串；  
> 优化 `BlogLogAOP.cs`


### 2020-04-15

> 重大内容更新：更新项目模板 `Update Blog.Core.Webapi.Template.1.11.30.nupkg`

  
###  2020-04-14  
> 重大内容更新：主分支，可以通过配置，一键切换JWT和Ids4认证授权模式    


###  2020-03-30  
> 重大内容更新：统一所有接口返回格式  
  

###  2020-03-25  
增加功能：支持读写分离（目前是三种模式：单库、多库、读写分离）   
> 重大BUG更新：系统登录接口，未对用户软删除进行判断，现已修复  
> API:  /api/login/GetJwtToken3  
> Code: await _sysUserInfoServices.Query(d => d.uLoginName == name && d.uLoginPWD == pass && d.tdIsDelete == false);  

  

###  2020-03-18  
增加功能：创建 Quartz.net 任务调度服务  
  

###  2020-01-09  
增加功能：项目迁移到IdentityServer4，统一授权认证中心   


###  2020-01-05  
增加功能：设计一个简单的中间件，可以查看所有已经注入的服务  
  

###  2020-01-04  
增加功能：Ip限流，防止过多刷数据  
