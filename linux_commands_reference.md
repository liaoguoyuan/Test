# Linux 常用命令参考指南

## 文件和目录操作

### 基本文件操作
- `ls` - 列出目录内容
  ```bash
  ls -la          # 显示详细信息包括隐藏文件
  ls -lh          # 以人类可读格式显示文件大小
  ls -lt          # 按修改时间排序
  ```

- `cd` - 切换目录
  ```bash
  cd /path/to/dir # 切换到指定目录
  cd ~            # 切换到用户主目录
  cd ..           # 返回上级目录
  cd -            # 返回上次访问的目录
  ```

- `pwd` - 显示当前工作目录
  ```bash
  pwd             # 打印当前完整路径
  ```

- `mkdir` - 创建目录
  ```bash
  mkdir dirname          # 创建目录
  mkdir -p path/to/dir   # 递归创建多级目录
  ```

- `rmdir` - 删除空目录
  ```bash
  rmdir dirname          # 删除空目录
  ```

- `rm` - 删除文件和目录
  ```bash
  rm file.txt            # 删除文件
  rm -r dirname          # 递归删除目录
  rm -rf dirname         # 强制递归删除（危险命令）
  rm -i file.txt         # 交互式删除，会询问确认
  ```

### 文件复制和移动
- `cp` - 复制文件或目录
  ```bash
  cp file1 file2         # 复制文件
  cp -r dir1 dir2        # 递归复制目录
  cp -p file1 file2      # 保持文件属性复制
  ```

- `mv` - 移动/重命名文件或目录
  ```bash
  mv oldname newname     # 重命名
  mv file /path/to/dir   # 移动文件到目录
  ```

- `ln` - 创建链接
  ```bash
  ln -s target linkname  # 创建符号链接
  ln target linkname     # 创建硬链接
  ```

## 文件内容查看和编辑

### 查看文件内容
- `cat` - 显示文件内容
  ```bash
  cat file.txt           # 显示整个文件
  cat -n file.txt        # 显示行号
  ```

- `less` / `more` - 分页查看文件
  ```bash
  less file.txt          # 可前后翻页查看
  more file.txt          # 只能向前翻页
  ```

- `head` - 显示文件开头
  ```bash
  head file.txt          # 显示前10行
  head -n 20 file.txt    # 显示前20行
  ```

- `tail` - 显示文件结尾
  ```bash
  tail file.txt          # 显示后10行
  tail -n 20 file.txt    # 显示后20行
  tail -f file.txt       # 实时监控文件变化
  ```

### 文件搜索和过滤
- `grep` - 文本搜索
  ```bash
  grep "pattern" file.txt     # 搜索包含模式的行
  grep -i "pattern" file.txt  # 忽略大小写搜索
  grep -r "pattern" dir/      # 递归搜索目录
  grep -n "pattern" file.txt  # 显示行号
  grep -v "pattern" file.txt  # 显示不匹配的行
  ```

- `find` - 查找文件和目录
  ```bash
  find /path -name "*.txt"    # 按文件名查找
  find /path -type f          # 查找文件
  find /path -type d          # 查找目录
  find /path -size +100M      # 查找大于100M的文件
  find /path -mtime -7        # 查找7天内修改的文件
  ```

- `locate` - 快速文件定位
  ```bash
  locate filename        # 快速查找文件位置
  updatedb              # 更新locate数据库
  ```

### 文本处理
- `sort` - 排序文本
  ```bash
  sort file.txt          # 按字母顺序排序
  sort -n file.txt       # 按数字排序
  sort -r file.txt       # 反向排序
  ```

- `uniq` - 去重
  ```bash
  uniq file.txt          # 去除相邻重复行
  sort file.txt | uniq   # 先排序再去重
  ```

- `wc` - 统计字数
  ```bash
  wc file.txt            # 显示行数、词数、字符数
  wc -l file.txt         # 只显示行数
  wc -w file.txt         # 只显示词数
  ```

- `cut` - 提取列
  ```bash
  cut -d',' -f1 file.csv # 提取CSV第一列
  cut -c1-10 file.txt    # 提取每行前10个字符
  ```

- `awk` - 文本处理工具
  ```bash
  awk '{print $1}' file.txt      # 打印第一列
  awk -F',' '{print $2}' file.csv # 以逗号分隔，打印第二列
  ```

- `sed` - 流编辑器
  ```bash
  sed 's/old/new/g' file.txt     # 替换文本
  sed -i 's/old/new/g' file.txt  # 直接修改文件
  sed -n '1,10p' file.txt        # 显示1-10行
  ```

## 系统信息和监控

### 系统信息
- `uname` - 系统信息
  ```bash
  uname -a               # 显示所有系统信息
  uname -r               # 显示内核版本
  ```

- `whoami` - 当前用户
  ```bash
  whoami                 # 显示当前用户名
  ```

- `id` - 用户和组信息
  ```bash
  id                     # 显示用户ID和组ID
  ```

- `date` - 日期和时间
  ```bash
  date                   # 显示当前日期时间
  date +%Y-%m-%d         # 自定义格式显示日期
  ```

- `uptime` - 系统运行时间
  ```bash
  uptime                 # 显示系统运行时间和负载
  ```

### 进程管理
- `ps` - 显示进程
  ```bash
  ps aux                 # 显示所有进程详细信息
  ps -ef                 # 另一种显示所有进程的方式
  ps -u username         # 显示特定用户的进程
  ```

- `top` - 实时进程监控
  ```bash
  top                    # 实时显示进程信息
  htop                   # 更友好的进程监控工具
  ```

- `kill` - 终止进程
  ```bash
  kill PID               # 终止指定进程ID的进程
  kill -9 PID            # 强制终止进程
  killall processname    # 终止所有同名进程
  ```

- `jobs` - 作业控制
  ```bash
  jobs                   # 显示当前作业
  bg                     # 将作业放到后台
  fg                     # 将作业调到前台
  nohup command &        # 后台运行命令，忽略挂起信号
  ```

### 系统资源监控
- `df` - 磁盘空间使用
  ```bash
  df -h                  # 以人类可读格式显示磁盘使用情况
  df -i                  # 显示inode使用情况
  ```

- `du` - 目录空间使用
  ```bash
  du -h dirname          # 显示目录大小
  du -sh *               # 显示当前目录下各项大小
  du -ah dirname         # 显示所有文件和目录大小
  ```

- `free` - 内存使用情况
  ```bash
  free -h                # 以人类可读格式显示内存使用
  ```

- `iostat` - I/O统计
  ```bash
  iostat                 # 显示CPU和I/O统计
  iostat -x 1            # 每秒显示详细I/O统计
  ```

## 网络命令

### 网络连接
- `ping` - 测试网络连通性
  ```bash
  ping google.com        # 测试与服务器连通性
  ping -c 4 google.com   # 发送4个包后停止
  ```

- `wget` / `curl` - 下载文件
  ```bash
  wget https://example.com/file.zip    # 下载文件
  curl -O https://example.com/file.zip # 下载文件
  curl -s https://api.example.com      # 静默获取API响应
  ```

- `ssh` - 远程登录
  ```bash
  ssh user@hostname      # SSH登录远程主机
  ssh -p 2222 user@host  # 指定端口登录
  ```

- `scp` - 远程文件复制
  ```bash
  scp file.txt user@host:/path/        # 复制文件到远程主机
  scp user@host:/path/file.txt ./      # 从远程主机复制文件
  ```

### 网络信息
- `netstat` - 网络连接状态
  ```bash
  netstat -tuln          # 显示所有监听端口
  netstat -an            # 显示所有网络连接
  ```

- `ss` - 现代版netstat
  ```bash
  ss -tuln               # 显示监听端口
  ss -an                 # 显示所有连接
  ```

- `ifconfig` / `ip` - 网络接口配置
  ```bash
  ifconfig               # 显示网络接口信息
  ip addr show           # 现代方式显示IP地址
  ip route show          # 显示路由表
  ```

## 文件权限和所有权

- `chmod` - 修改文件权限
  ```bash
  chmod 755 file.txt     # 设置文件权限
  chmod +x script.sh     # 添加执行权限
  chmod -R 644 dirname   # 递归设置目录权限
  ```

- `chown` - 修改文件所有者
  ```bash
  chown user:group file.txt      # 修改所有者和组
  chown -R user dirname          # 递归修改目录所有者
  ```

- `umask` - 设置默认权限
  ```bash
  umask                  # 显示当前umask值
  umask 022              # 设置默认权限掩码
  ```

## 压缩和解压

- `tar` - 打包和解包
  ```bash
  tar -czf archive.tar.gz dirname    # 创建gzip压缩包
  tar -xzf archive.tar.gz            # 解压gzip压缩包
  tar -cjf archive.tar.bz2 dirname   # 创建bzip2压缩包
  tar -xjf archive.tar.bz2           # 解压bzip2压缩包
  tar -tf archive.tar.gz             # 查看压缩包内容
  ```

- `zip` / `unzip` - ZIP压缩
  ```bash
  zip -r archive.zip dirname    # 创建ZIP压缩包
  unzip archive.zip             # 解压ZIP文件
  unzip -l archive.zip          # 查看ZIP内容
  ```

- `gzip` / `gunzip` - gzip压缩
  ```bash
  gzip file.txt          # 压缩文件
  gunzip file.txt.gz     # 解压文件
  ```

## 系统管理

### 用户管理
- `su` - 切换用户
  ```bash
  su username            # 切换到指定用户
  su -                   # 切换到root用户
  ```

- `sudo` - 以管理员权限执行
  ```bash
  sudo command           # 以root权限执行命令
  sudo -u user command   # 以指定用户权限执行
  ```

- `passwd` - 修改密码
  ```bash
  passwd                 # 修改当前用户密码
  sudo passwd username   # 修改指定用户密码
  ```

### 服务管理（systemd）
- `systemctl` - 服务控制
  ```bash
  systemctl status service    # 查看服务状态
  systemctl start service     # 启动服务
  systemctl stop service      # 停止服务
  systemctl restart service   # 重启服务
  systemctl enable service    # 开机自启动
  systemctl disable service   # 禁用开机自启动
  ```

### 包管理（根据发行版不同）
- **Ubuntu/Debian (apt)**
  ```bash
  apt update             # 更新包列表
  apt upgrade            # 升级所有包
  apt install package    # 安装包
  apt remove package     # 卸载包
  apt search keyword     # 搜索包
  ```

- **CentOS/RHEL (yum/dnf)**
  ```bash
  yum update             # 更新系统
  yum install package    # 安装包
  yum remove package     # 卸载包
  yum search keyword     # 搜索包
  ```

## 文本编辑器

- `nano` - 简单文本编辑器
  ```bash
  nano file.txt          # 编辑文件
  # Ctrl+X 退出，Ctrl+O 保存
  ```

- `vim` - 高级文本编辑器
  ```bash
  vim file.txt           # 编辑文件
  # :w 保存，:q 退出，:wq 保存并退出
  # i 进入插入模式，Esc 退出插入模式
  ```

- `emacs` - 另一个高级编辑器
  ```bash
  emacs file.txt         # 编辑文件
  # Ctrl+X Ctrl+S 保存，Ctrl+X Ctrl+C 退出
  ```

## 环境变量和Shell

- `echo` - 输出文本
  ```bash
  echo "Hello World"     # 输出文本
  echo $PATH             # 输出环境变量
  ```

- `env` - 显示环境变量
  ```bash
  env                    # 显示所有环境变量
  env | grep PATH        # 查找特定环境变量
  ```

- `export` - 设置环境变量
  ```bash
  export VAR=value       # 设置环境变量
  export PATH=$PATH:/new/path  # 添加到PATH
  ```

- `which` - 查找命令位置
  ```bash
  which python           # 查找python命令的路径
  ```

- `type` - 显示命令类型
  ```bash
  type ls                # 显示ls是别名还是可执行文件
  ```

## 输入输出重定向和管道

- **重定向**
  ```bash
  command > file.txt     # 重定向输出到文件（覆盖）
  command >> file.txt    # 重定向输出到文件（追加）
  command < file.txt     # 从文件读取输入
  command 2> error.log   # 重定向错误输出
  command &> all.log     # 重定向所有输出
  ```

- **管道**
  ```bash
  command1 | command2    # 将command1的输出作为command2的输入
  ps aux | grep python   # 查找python进程
  ls -la | sort          # 排序目录列表
  ```

## 历史和快捷键

- `history` - 命令历史
  ```bash
  history                # 显示命令历史
  history | grep keyword # 搜索历史命令
  !n                     # 执行历史中第n条命令
  !!                     # 执行上一条命令
  ```

- **常用快捷键**
  ```bash
  Ctrl+C                 # 中断当前命令
  Ctrl+Z                 # 暂停当前命令
  Ctrl+D                 # 结束输入/退出shell
  Ctrl+L                 # 清屏
  Ctrl+A                 # 光标移到行首
  Ctrl+E                 # 光标移到行尾
  Ctrl+U                 # 删除光标前的内容
  Ctrl+K                 # 删除光标后的内容
  Ctrl+R                 # 反向搜索历史命令
  Tab                    # 自动补全
  ```

## 磁盘和文件系统

- `mount` / `umount` - 挂载文件系统
  ```bash
  mount /dev/sdb1 /mnt   # 挂载设备
  umount /mnt            # 卸载挂载点
  mount                  # 显示所有挂载点
  ```

- `fdisk` - 磁盘分区
  ```bash
  fdisk -l               # 列出所有磁盘分区
  ```

- `lsblk` - 列出块设备
  ```bash
  lsblk                  # 以树形显示块设备
  ```

## 性能监控

- `vmstat` - 虚拟内存统计
  ```bash
  vmstat 1               # 每秒显示系统统计
  ```

- `sar` - 系统活动报告
  ```bash
  sar -u 1 10            # 每秒显示CPU使用率，共10次
  ```

- `lsof` - 列出打开的文件
  ```bash
  lsof                   # 列出所有打开的文件
  lsof -p PID            # 列出指定进程打开的文件
  lsof -i :80            # 列出使用80端口的进程
  ```

## 其他实用命令

- `alias` - 创建命令别名
  ```bash
  alias ll='ls -la'      # 创建别名
  unalias ll             # 删除别名
  alias                  # 显示所有别名
  ```

- `crontab` - 定时任务
  ```bash
  crontab -e             # 编辑定时任务
  crontab -l             # 列出定时任务
  ```

- `screen` / `tmux` - 终端复用器
  ```bash
  screen                 # 启动screen会话
  tmux                   # 启动tmux会话
  ```

- `rsync` - 文件同步
  ```bash
  rsync -av source/ dest/           # 同步目录
  rsync -av user@host:/path/ ./     # 从远程同步
  ```

## 帮助命令

- `man` - 查看手册页
  ```bash
  man command            # 查看命令的详细手册
  man -k keyword         # 搜索相关命令
  ```

- `--help` - 快速帮助
  ```bash
  command --help         # 显示命令帮助信息
  ```

- `info` - 信息文档
  ```bash
  info command           # 查看GNU info文档
  ```

---

## 实用技巧

1. **使用Tab键自动补全**文件名和命令
2. **使用通配符**：`*`（任意字符）、`?`（单个字符）、`[]`（字符范围）
3. **命令组合**：使用`;`分隔多个命令，使用`&&`只在前一个命令成功时执行下一个
4. **后台运行**：在命令后加`&`使其在后台运行
5. **查看命令历史**：使用`Ctrl+R`搜索历史命令
6. **使用别名**简化常用的长命令

这些命令涵盖了Linux系统管理和日常使用的大部分需求。建议从基本的文件操作命令开始学习，逐步掌握更高级的功能。