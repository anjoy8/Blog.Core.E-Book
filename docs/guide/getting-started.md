# K  快速上手
注意

请确保你的 `Visual Studio 2022` 版本 >= `17.8.0`。    
并安装 `.NET 8.0 SDK`  


## 下载
Github（国际） 下载 [https://github.com/anjoy8/Blog.Core](https://github.com/anjoy8/Blog.Core)  
    
Gitee（国内） 下载 [https://gitee.com/laozhangIsPhi/Blog.Core](https://gitee.com/laozhangIsPhi/Blog.Core)  


## 编译与运行
1、拿到项目后，双击 `Blog.Core.sln` 解决方案；  
2、首先 `F6` 编译，看是否有错误；  
3、然后 `F5` 运行，调起 `9291` 端口，浏览器查看效果；  
4、因为系统默认的是 `sqlite` 数据库，如果你想换其他数据库，请看下边；    
5、注意：本系统是直接自动生成数据库和数据的，不用手动创建数据库；  




## CodeFirst 与 DbFirst
1、项目同时支持两个常见开发模式：`CodeFirst` 和 `DbFirst`；  
2、首先 如果你是第一次下载我的项目，肯定是想要浏览效果和直接使用对应的权限相关的内容，这个时候肯定需要用到数据库表结构，那就肯定需要 `CodeFirst` ，只需要在`appsettings.json` 里配置好数据库连接字符串（下文会说到如何配置），就能正确运行；  
3、浏览器查看效果，或者配合 `Admin` 项目查看效果后，如果感觉项目可行，并打算在此基础上二次开发，那肯定会在你刚刚创建的数据库种去创建新的表结构，这个时候就需要使用 `DbFirst` 模式，来生成四层项目问题：Model+Service+Repository等；  
4、你可以使用T4模板，但是我更建议使用 `/api/DbFirst/GetFrameFiles` 接口来生成，不仅支持多种类型的数据库，还支持同时多库模式的输出；    
5、如果你不想用我的表结构和实体类，在项目启动的时候，把配置文件的 `SeedDBEnabled`节点设置成False即可，然后配置对应的你自己的数据库连接字符串，比如是商城的，然后使用 `/api/DbFirst/GetFrameFiles` 接口来生成你的数据库四层类文件；  



## 如何配置数据库连接字符串

1、打开 `Blog.Core` 项目下的 `appsettings.json` 文件；  
2、修改 `DBS` 字节内容，配置对应的连接字符串，注意`DBType`对应不同的数据库类型；  
3、把你想要运行的数据库 `Enabled` 为 `true` 即可，其他都要设置 `false`；  
4、然后 `MainDB` 设置为下边你使用的指定 `ConnId`:  

```
//优化DB配置、不会再区分单库多库
//MainDb：标识当前项目的主库，所对应的连接字符串的Enabled必须为true
//Log:标识日志库，所对应的连接字符串的Enabled必须为true
//从库只需配置Slaves数组,要求数据库类型一致!，比如都是SqlServer
//
//新增,故障转移方案
//如果主库挂了,会自动切换到备用连接(比如说主库+备用库)
//备用连接的ConnId配置为主库的ConnId+数字即可,比如主库的ConnId为Main,那么备用连接的ConnId为Mian1
//主库、备用库无需数据库类型一致!
//备用库不会有程序维护,需要手动维护
"MainDB": "Main", //当前项目的主库，所对应的连接字符串的Enabled必须为true
"DBS": [
  /*
    对应下边的 DBType
    MySql = 0,
    SqlServer = 1,
    Sqlite = 2,
    Oracle = 3,
    PostgreSQL = 4,
    Dm = 5,//达梦
    Kdbndp = 6,//人大金仓
  */
  {
    "ConnId": "Main",
    "DBType": 2,
    "Enabled": true,
    "Connection": "WMBlog.db", //sqlite只写数据库名就行
    "Slaves": [
      {
        "HitRate": 0,// 值越大，优先级越高 0不使用
        "Connection": "WMBlog2.db"
      }
    ]
  },
  {
    "ConnId": "Main2",
    "DBType": 2,
    "Enabled": true,
    "Connection": "WMBlog3.db", //sqlite只写数据库名就行
    "Slaves": [
      {
        "HitRate": 0,// 值越大，优先级越高 0不使用
        "Connection": "WMBlog4.db"
      }
    ]
  },
  {
    "ConnId": "Log", //日志库连接固定名称，不要改,其他的可以改
    "DBType": 2,
    "Enabled": true,
    "HitRate": 50,
    "Connection": "WMBlogLog.db" //sqlite只写数据库名就行
  },
  {
    "ConnId": "WMBLOG_MSSQL_1",
    "DBType": 1,
    "Enabled": false,
    "Connection": "Data Source=(localdb)\\MSSQLLocalDB;Initial Catalog=WMBLOG_MSSQL_1;Integrated Security=True;Connect Timeout=30;Encrypt=False;TrustServerCertificate=False;ApplicationIntent=ReadWrite;MultiSubnetFailover=False",
    "ProviderName": "System.Data.SqlClient"
  },
  {
    "ConnId": "WMBLOG_MSSQL_2",
    "DBType": 1,
    "Enabled": false,
    "Connection": "Data Source=(localdb)\\MSSQLLocalDB;Initial Catalog=WMBLOG_MSSQL_2;Integrated Security=True;Connect Timeout=30;Encrypt=False;TrustServerCertificate=False;ApplicationIntent=ReadWrite;MultiSubnetFailover=False",
    "ProviderName": "System.Data.SqlClient"
  },
  {
    "ConnId": "WMBLOG_MYSQL",
    "DBType": 0,
    "Enabled": false,
    "Connection": "server=localhost;Database=blog;Uid=root;Pwd=root;Port=3306;Allow User Variables=True;"
  },
  {
    "ConnId": "WMBLOG_MYSQL_2",
    "DBType": 0,
    "Enabled": false,
    "Connection": "server=localhost;Database=blogcore001;Uid=root;Pwd=root;Port=3306;Allow User Variables=True;"
  },
  {
    "ConnId": "WMBLOG_ORACLE",
    "DBType": 3,
    "Enabled": false,
    "Connection": "Data Source=127.0.0.1/ops;User ID=OPS;Password=123456;Persist Security Info=True;Connection Timeout=60;"
  },
  {
    "ConnId": "WMBLOG_DM",
    "DBType": 5,
    "Enabled": false,
    "Connection": "Server=xxxxx:5236;User Id=xxxxx;PWD=xxxxx;SCHEMA=TESTDBA;"
  },
  {
    "ConnId": "WMBLOG_KDBNDP",
    "DBType": 6,
    "Enabled": false,
    "Connection": "Server=127.0.0.1;Port=54321;UID=SYSTEM;PWD=system;database=SQLSUGAR4XTEST1;"
  }
]
```
  

5、如果你想多库操作，需要配置
```
  a：MainDB 设置为主库的 ConnId；
  b：MutiDBEnabled设置为true，
  c：把下边想要连接的多个连接字符串都设置为true
```

## 如何配置项目端口号
1、在 `Blog.Core` 层下的 `appsettings.json` 文件中，将 `9291`端口，修改为自己想要的端口号；    
2、或者在 `launchSettings.json` 中设置(`注意，如果仅仅修改这里，publish后，端口访问无效`)；

## 如何项目重命名
1、双击项目根目录下的 `CreateYourProject.bat` 批处理文件；  
2、根据提示，`在Dos窗口内`输入自己想要的项目名称即可；  
3、在根目录会有一个 `.1YourProject` 文件夹，里边即你的项目；  


## 新增实体模块后如何迁移到数据库
1、在 `Blog.Core.Model` 项目目录下的 `Seed` 文件夹下，找到 `DBSeed` 类；  
2、根据提示，找到生成table的地方 `myContext.CreateTableByEntity`；  
3、添加进去你新增的实体类，当然也可以用下边的单独写法；  
4、编译项目，没错后，运行，则数据库更新完毕；  


## 新增实体，如何进行增删改查CURD操作
1、随便找一个含有业务逻辑的 `controller` 参考一下即可；  
2、主要 `api` 是通过 `Service` 服务层提供业务逻辑；  
3、然后服务层通过 `Repository` 仓储层封装持久化操作；  
4、每一个表基本上对应一个仓储类，基本的操作都封装到了 `BaseRepository.cs` 基类仓储中；  
5、添加完业务逻辑，记得要 `F6` 重新编译一下，因为项目间引用解耦了；  
6、项目已经自动注入了，直接在控制器使用对应的服务层接口就行： `IxxxxService` ;  


## 新增数据库表，如何反向生成四层文件
1、可以通过 `T4` 模板来生成，在 `Blog.Core.FrameWork` 层，使用方法: [9757999.html](https://www.cnblogs.com/laozhang-is-phi/p/9757999.html#autoid-4-3-0) ；  
> 注意：这种方案，目前默认的只能是 `SqlServer` ，其他类型的数据库，可以看上边文章中的代码，或者群文件里对应的代码。 

> 1、修改`DbHelper.ttinclude`文件中的连接字符串，注意是`SqlServer`的： public static readonly string ConnectionString;  
> 2、然后去各个层模板文件，点击`Ctrl+S`;  
> 3、就会在对应的层内，看到新文件，比如：Blog.Core.Model/Model_NEW   



2、也可以通过 `Sqlsugar` 所带的方法来实现 `DbFirst`，具体查看 `Controller` 层下的 `DbFirstController.cs`；   

3、总体操作过程，可以参考我的视频：[av77612407](https://www.bilibili.com/video/av77612407?p=2) ；   


## 发布与部署
1、双击项目根目录下的 `Blog.Core.Publish.bat`批处理文件；  
2、执行完成后，根目录会有一个`.PublishFiles` 文件夹，就是发布后的项目；


## 如何更新项目模板
1、着急的话自己打包，不着急就提 `issue`，等我更新；  
2、我的开源项目中，有个模板项目 `BlogCoreTempl` [地址](https://github.com/anjoy8/BlogCoreTempl)，下载下来；   
3、下载最新的 `Blog.Core` 源代码；  
4、将源代码拷贝到模板项目的 `content` 文件夹下；   
5、双击 `Package.bat` 文件，就生成了最新的模板了； 

