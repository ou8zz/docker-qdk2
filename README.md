通过Docker打包威联通QNAP NAS的qpkg文件
============================================
官方的打包工具
https://github.com/qnap-dev/docker-qdk2

Steps
=========================
```
$ git clone https://github.com/qnap-dev/docker-qdk2.git
$ cd docker-qdk2
$ docker run -it --rm -v ${PWD}/example/redmine:/src dorowu/qdk2-build
Creating archive with data files...
      tar:   10kB 0:00:00 [18.8MB/s] [=========================================================] 158%            
Creating archive with control files...
Creating QPKG package...
-rw-r--r-- 1 1000 1000 24337 Mar 17 02:35 redmine_3.3.0_x86_64.qpkg
$ ls -l example/redmine/redmine_3.3.0.qpkg 
-rw-r--r-- 1 u u 24337 Mar 17 10:35 example/redmine/redmine_3.3.0_x86_64.qpkg
```

A QPKG was created in `example/redmine/build/redmine_3.3.0_x86_64.qpkg`. Make sure there is Container Station installed on QNAP NAS, then manually install it in App Center.

### Frpc打包

将对应平台的frpc执行文件cp到`example/frpc/x86_64`目录
创建`frpc.ini`到`Public/frpc/`目录，和自己对应的配置

```bash
git clone https://github.com/ou8zz/docker-qdk2
cd docker-qdk2
docker run -it --rm -v ${PWD}/example/frpc:/src dorowu/qdk2-build

```

入口文件在example/frpc/shared/frpc.sh
安装之后启动会在`Public`目录下创建`frpc`文件夹，读取里面的`frpc.ini` （第一次安装要手动创建该文件），运行日志则为同目录下的`frpc.log`。
这样就不需要自定义开机脚本或者通过`Container Station`启动frpc容器了。