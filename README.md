# edk2

### Windows下开发环境配置
 直接在win10下安装  

### 安装开发工具
1. 安装VS2010  链接：https://pan.baidu.com/s/1jwUJVKW7IXo-yF5UJa5ANg  提取码：1111 

2. 安装Python2.7 https://www.python.org/downloads/release/python-2716/. 新建环境变量PYTHON_HOME，值为C:\Python27  （勾选添加到PATH，然后默认安装，Python27一定要放C盘根目录）

3. 下载IASL编译器.  https://acpica.org/downloads/binary-tools  ，解压到C:\asl，并添加到环境变量PATH中

4. 下载NASM. https://www.nasm.us/. 往环境变量PATH中添加C:\nasm,  (NASM_PREFIX不设置也可以, 但是会报warning. 如果设置必须设置正确, 一旦填错, 必须把udk2文件夹删除干净重来)

5. 下载Openssl. http://wiki.overbyte.eu/arch/openssl-1.1.0g-win32.zip. 往环境变量PATH中添加C:\openssl

6.下载edk2开发包, 解压: https://codeload.github.com/tianocore/edk2/zip/vUDK2018

7.生成OPENSSL加密库。 从 https://github.com/openssl/openssl/archive/OpenSSL_1_1_0g.zip 下载，下载后解压到edk2\CryptoPkg\Library\OpensslLib中，重命名为openssl.

8. 预搭建base tools。从https://github.com/tianocore/edk2-BaseTools-win32 并解压到edk2\BaseTools\Bin，重命名为Win32,注意忽略此步会在接下来的搭建中遇到报错环境变量PYTHON_HOME的问题。

### 配置edk2编译环境

1. 在edk2目录下使用cmd，运行edksetup.bat,生成Conf目录下的target.txt和tools_def.txt

2. 打开target.txt，修改值  TOOL_CHAIN_TAG        = VS2010x86

3. 修改值  DEFINE VS2010x86_BIN    = D:\VS2010\VC\bin
          DEFINE VS2010x86_DLL    = D:\VS2010\Common7\IDE;DEF(VS2010x86_BIN)
          DEFINE VS2010x86_BINX64 = DEF(VS2010x86_BIN)\x86_amd64
          DEFINE VS2010x86_BIN64  = DEF(VS2010x86_BIN)\x86_ia64
4. 重启cmd，运行：

  -> edksetup.bat Rebuild    
  -> edksetup.bat --nt32    
  -> build    
  -> build run    

参考（https://github.com/tianocore/tianocore.github.io/wiki/UDK2018-How-to-Build#how-to-build-windows-system）
转自 (https://cloud.tencent.com/developer/article/1670600)
