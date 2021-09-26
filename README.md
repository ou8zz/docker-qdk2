通过Docker打包威联通QNAP NAS的qpkg文件
============================================
+ 官方的Docker打包工具https://github.com/qnap-dev/docker-qdk2
+ 官方NAS QDK打包https://cheng-yuan-hong.gitbook.io/qdk-quick-start-guide/build-your-own-qpkg
============================================

### Frpc打包

+ 将对应平台的frpc执行文件cp到`example/frpc/x86_64`目录。
+ 创建`frpc.ini`到`Public/frpc/`目录，和自己对应的配置。
+ 入口文件在`example/frpc/shared/frpc.sh`。
+ 运行日志目录`Public/frpc/frpc.log`。
+ 这样就不需要自定义开机脚本或者通过`Container Station`启动frpc容器了。
+ 执行以下命令
```bash
git clone https://github.com/ou8zz/docker-qdk2
cd docker-qdk2
docker run -it --rm -v ${PWD}/example/frpc:/src dorowu/qdk2-build
```