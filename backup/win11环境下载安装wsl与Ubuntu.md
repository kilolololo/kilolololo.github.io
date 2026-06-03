下载wsl花了较多时间，之前执行wsl --install总是在中途失败，下载速度又很慢。下面的方法一次成功了。
windows powershell以管理员身份运行，执行命令
`wsl --install --distribution Ubuntu-24.04 --location D:\WSL\Ubuntu`
等待较长时间即可下载安装完成。等待期间不要开梯子，可能会导致下载失败。下载安装结束命令行会出现下列信息，填写姓名与密码。
```
Installing, this may take a few minutes...
Please create a default UNIX user account. The username does not need to match your Windows username.
For more information visit: https://aka.ms/wslusers
 
Enter new UNIX username: yourname
Enter new UNIX password:
Retype new UNIX password:
```
在该路径下会出现两个文件，表示Ubuntu成功安装：
<img width="517" height="272" alt="Image" src="https://github.com/user-attachments/assets/f61454bd-dc10-4760-a2f3-3605c10fe66b" />
同时弹出窗口，表示成功启用wsl
然后执行下列命令更新Ubuntu的安装包
```Bash
# Ubuntu/Debian
sudo apt update && sudo apt upgrade -y
```
需要等待一段时间全部更新。

**进入Ubuntu的方式**
在开始图标右键进入终端，在终端下拉框选择Ubuntu。