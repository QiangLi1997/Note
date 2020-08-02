# 基本命令
#### 创建用户&赋予权限
```bash
sudo useradd -m -s /bin/bash -d /data/liqiang liqiang
sudo passwd liqiang
sudo usermod -aG sudo liqiang
```
#### 用户组
```bash
cat /etc/group
groups username #查看用户所属组
sudo usermod -aG groupname username #添加用户到用户组
sudo gpasswd -a username groupname #添加用户到用户组
sudo gpasswd -d username groupname #从用户组删除用户
```
#### 查找库
```bash
ldconfig -p | grep libnccl
库路径：LD_LIBRARY_PATH & LIBRARY_PATH
```
#### 查找文件
```bash
find / -name "hdf5.h"
find /dir/path -name "test*"
```
#### 当前目录文件(夹)大小
```bash
du -sh * / du -sh .[!.]* (隐藏目录)
```
#### 计算机磁盘空间用量
```bash
df -h
```
#### 打开(图片)
```bash
xdg-open a.png
```
#### 查看登陆用户
```bash
who/lastlog
```
#### 统计字节数字数行数
```bash
wc (-l 只统计行数)
```
#### zip压缩
```bash
zip -r target.zip targetdir
unzip target.zip
```
#### tee命令
```bash
stdout生成log | tee 1.log
```
#### 后台不挂断
```bash
nohup ./runfile &
```
#### 前后台切换
```bash
jobs -> bg/fg/kill %id
```
#### 文件夹内容比较
```bash
diff -q	#仅报告文件是否相异,不报告详细的差异
```
#### 创建软连接
```bash
ln -s spath dpath
```
#### 文件校验
```bash
# linux
md5sum filepath
sha1sum filepath

# windows powershell
# MD5(SHA1/SHA256/SHA384/SHA512/MACTripleDES/RIPEMD160)
Get-FileHash -Path filepath -Algorithm MD5
```
#### firefox

# 特殊命令
## screen
```bash
创建：screen (-S name)
分离：ctrl&a +d ATTENTION：press d AFTER a
罗列：screen -ls
恢复：screen -r id
```
### git
```bash
git clone https://github.com/QiangLi1997/Note
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git add -A
git commit -m "update"
git push origin master
```
### nethogs
```bash
查看网络流量进程
sudo apt-get install nethogs
sudo nethogs
```

# 其他
#### linux回收站
```bash
mkdir -p /data/liqiang/trash
alias rm=trash
alias r=trash
alias rl='ls /data/liqiang/trash'
alias ur=undelfile
undelfile(){
	mv -i /data/liqiang/trash/$@ ./
}
trash(){
	mv -i $@ /data/liqiang/trash/
}
```
### aptitude
```bash
sudo apt-get aptitude(库依赖处理)
```
### 解决Chrome想创建登录密钥环
```
直接回车
```
### 解决/usr/lib/snapd/snapd占用网络
```bash
#To temporarily disable snap packages (until reboot or if you run with start):
sudo systemctl stop snapd.service
#To permanently disable snap packages:
sudo systemctl stop snapd.service
sudo systemctl disable snapd.service
#To reenable snap packages:
sudo systemctl reenable snapd.service
sudo systemctl start snapd.service
```
### 解决linux wget下载arxiv论文出现403错误
```bash
wget -U NoSuchBrowser/1.0 链接
```
### shell命令中--的含义
 - 作为输入选项的含义
 	 - 通过命令选项，我们可以修改命令执行的行为。命令行选项可以分为短命令行选项和长命令行选项两种。短命令行选项是由字母组成，长命令行选项是由单词组成。短命令行选项在选项前使用单横杠'-'，长命令行选项前使用双横杠'--'。如果选项后面需要输入选项的参数，短命令行选项和参数之间使用空格分隔，而长命令行选项使用等号'='连接选项和参数。
 - 单独使用的含义
	 - The first -- argument that is not an option-argument should be accepted as a delimiter indicating the end of options. Any following arguments should be treated as operands, even if they begin with the '-' character.
	  - [example](https://serverfault.com/questions/114897/what-does-double-dash-mean-in-this-shell-command)
### 解决shell行尾多出0D的问题
```
windows打开过的文档会被改为dos格式
dos格式：CR LF
unix格式：LF
在vim中用:set ff查看格式
用:set ff=unix和:set ff=dos来改变格式
```


