https://code.visualstudio.com/docs/containers/overview


https://docs.docker.com/docker-for-windows/install/

https://docs.microsoft.com/en-us/windows/wsl/install-win10

https://docs.microsoft.com/zh-cn/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package


### Docker


1. 使用当前目录(`.`)下的`Dockerfile`文件来`build`一个名为`bustub`镜像。

```bash
docker build  -t bustub .
```

2. 使用上面的`bustub`镜像创建一个可写的`bustub`的容器(`--name bustub`)，并为后面运行指定的命令做准备。

```bash
docker create -t -i --name bustub -v "$(pwd):/bustub" bustub bash
```

`-v`： 使用`bind挂载`将位于当前目录（`$(pwd)`）的源代码挂载到容器`/bustub `下，使得我们在主机上的修改操作对于容器来说是可见的。

`-i`：`--interactive`, 允许在容器启动可进行交互，默认打开标准输入`STDIN`，这里我们同时指定了`bash` Shell 环境。

3. 运行刚才创建的`bustub`容器:

```bash
docker start -a -i bustub
```

此时可以进入到容器`bustub`中,发现当前目录下存在名为`bustub`的文件目录。我们可以在本机上编辑代码。然后在`docker`中的虚拟容器`bustub`上编译和运行我们的代码。


```bash
root@e0fec830c440:/bustub# ls -al
bin   bustub  etc   lib    lib64  mnt  proc  run   srv  tmp  var
boot  dev     home  lib32  media  opt  root  sbin  sys  usr
```

### Build



### Test

本地测试：使用`GTest`



课程项目线上提交测试方法：
https://15445.courses.cs.cmu.edu/fall2020/faq.html#q5

注意内存泄露、代码格式和输出正确。

测试网站：
https://www.gradescope.com/

邮箱：liuzengh@qq.com
密码：CMU15445DBfall2020




### 实现注意

1. 从类模板中继承时，在派生类中使用基类中protected段的成员变量时要用this。
2. unique_ptr不具有值语义，只有移动语义，所以要使用std::move函数。