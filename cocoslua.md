安装路径：  

```
D:\Cocosstudio\Cocos2d-x\cocos2d-x-3.10\tools\cocos2d-console\bin
```


工程路径：

```
 D:\cocos2d-x-lua\project   
```


创建工程：

```
  cocos new  HelloWorld -p com.earlybd -l lua -d D:\cocos2d-x-lua\project  
```


删除 文件夹

```
app  packages  config.lua   
<ProjectHome>.</ProjectHome>   修改 <ProjectHome>./src</ProjectHome>  替换 src\     
下面"src\ ” 替换为空字符串。接着删除第一个为空的目录      
command line :  -workdir D:\cocos2d-x-lua\kxCocos-master\kxCocos -file src/main.lua                                                                            
```

​                               

lua 路径：

```
C:\Program Files (x86)\Lua\5.1\lua.exe   
```


运行：                                    

```
D:\cocos2d-x-lua\project\cocos2d-lua-pratics\LuaTemplate                                          
cocos run HelloLua -p win32     
```

​                                                                                                     

lua 调试:https://blog.csdn.net/han1558249222/article/details/53365289、                                                       

​                                                                                   



lua: 

```
D:\cocos2d-x-lua\project                                                                                                        
Lua script folder    ：lua 脚本目录                
Lua exe path         ：lua 主程序目录，也就是之前的 simulator                  
Working path       ：lua 运行环境目录                                
Lua project name ：在 VS 解决方案中显示的项目名称                            
Command line     ：执行命令，这个可以先不管                                                                                              
```



Vs2017 环境变量：  

```powershell
include                   
C:\Program Files (x86)\Microsoft Visual Studio\2017\Professional\VC\Tools\MSVC\14.14.26428\include;                 
C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\ucrt;                               
C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\shared;                     
C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt;                           
C:\Program Files (x86)\Windows Kits\8.1\Include\um;   
```

​                                  

path:                     

```powershell
C:\Program Files\Microsoft SQL Server\130\Tools\Binn\;                            
D:\Cocosstudio\Cocos2d-x\cocos2d-x-3.10\tools\cocos2d-console\bin\bin;                           
C:\Program Files (x86)\Lua\5.1;                    
C:\Program Files (x86)\Lua\5.1\clibs;                                    
D:\Cocosstudio\Cocos2d-x\cocos2d-x-3.10\tools\cocos2d-console\bin;                       
C:\Program Files\Microsoft SQL Server\110\Tools\Binn\;                                                                                                                                

C:\Program Files (x86)\Microsoft Visual                                   Studio\2017\Professional\VC\Tools\MSVC\14.14.26428\bin\Hostx86\x86;                           
C:\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE;
```

WIN_SDK                                                             

```
C:\Program Files\Microsoft SDKs        
```

​                                               



lib

```powershell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Professional\VC\Tools\MSVC\14.14.26428\lib;                 
C:\Program Files (x86)\Windows Kits\10\Lib\10.0.17134.0\ucrt\x86;                  
C:\Program Files (x86)\Windows Kits\8.1\Lib\winv6.3\um\x86;      
```

​                                                                                                                  



将解决方案 的$(SolutionDir)  替换成 $(CocosRoot)                      
mysql启动：  net start mysql                                                                    



使用devenv/MSBuild 在命令行编译sln或csproj                                                                                     
1>编译整个解决方案                                    

```
devenv.exe  D:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\kxCocos.sln  /build "Release|Win32" 
/Log  D:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\1.log                                              

MSBuild   D:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\kxCocos.sln   /t:Rebuild /p:Configuration=Release                                                                                                                                                    
```

1>编译解决方案中某个项目

```powershell
devenv DD:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\kxCocos.vcxproj  /build "Release|Win32"            
/Log  D:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\1.log                                                                          

devenv.exe D:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\kxCocos.sln /build "Release|Win32"           
/Project D:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\kxCocos  
/Log  D:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\1.log                                                           

MSBuild D:\cocos2d-x-lua\kxCocos-master\kxCocos\frameworks\runtime-src\proj.win32\kxCocos.vcxproj  /t:Clean                                                                           
/p:Configuration=Debug;/p:Platform=x86;TargetFrameworkVersion=v3.5          
```

​                                                                              



2>lua  控制台打印

```c
#ifdef USE_WIN32_CONSOLE                        
	AllocConsole();             
	freopen("CONIN$", "r", stdin);            
	freopen("CONOUT$", "w", stdout);                     
	freopen("CONOUT$", "w", stderr);                    
	// 初始化一下控制台的尺寸                   
	HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);              
	COORD size = { 160,9999 };                  
	SetConsoleScreenBufferSize(hOut, size);                 
	SMALL_RECT r;                        
	r.Left = 0;                     
	r.Top = 0;                    
	r.Right = 160;                          
	r.Bottom = 50;                                         
	SetConsoleWindowInfo(hOut, TRUE, &r);                   
#endif                           
```

或 

```c
#ifdef USE_WIN32_CONSOLE            
	AllocConsole();              
	freopen("CONIN$", "r", stdin);              
	freopen("CONOUT$", "w", stdout);                  
	freopen("CONOUT$", "w", stderr);                      
#endif                             
```



vs 中添加预处理器 

```
 USE_WIN32_CONSOLE        
```

​                             

3mZNVOirtKW                                                                                
Visual Studio 2017（VS2017） 企业版 Enterprise 注册码：NJVYC-BMHX2-G77MM-4XJMR-6Q8QF                   
Visual Studio 2017（VS2017） 专业版Professional 激活码key：KBJFW-NXHK6-W4WJM-CRMQB-G3CDH   


指南：
https://docs.cocos2d-x.org/cocos2d-x/zh/basic_concepts/      
https://fusijie.github.io/Cocos-Resource/index.html     


