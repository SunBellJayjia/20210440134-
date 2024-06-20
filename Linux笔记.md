以下是一份Linux指令学习记录，包括了指令的简介、参数说明、使用示例等

### 一、Linux 文件与目录管理

#### 1. `ls` 命令

**简介**：`ls` 命令用于列出目录内容。

**参数说明**：
- `-a`：显示所有文件和目录，包括隐藏的文件（以`.`开头的文件）。
- `-l`：使用长格式显示文件和目录的详细信息，包括权限、所有者、大小等。
- `-h`：以人类可读的格式显示文件大小（例如，K、M、G）。

**使用示例**：


```bash
# 列出当前目录下的所有文件和目录（包括隐藏的）
ls -a

# 以长格式列出当前目录下的所有文件和目录，并显示人类可读的文件大小
ls -lh
```
#### 2. `cd` 命令

**简介**：`cd` 命令用于切换当前工作目录。

**参数说明**：
- `目录路径`：要切换到的目录的路径。可以是绝对路径或相对路径。

**使用示例**：


```bash
# 切换到用户的家目录
cd ~

# 切换到根目录
cd /

# 切换到上一级目录
cd ..
```
#### 3. `pwd` 命令

**简介**：`pwd` 命令用于显示当前工作目录的路径。

**使用示例**：


```bash
# 显示当前工作目录的路径
pwd
```
#### 4. `mkdir` 命令

**简介**：`mkdir` 命令用于创建新目录。

**参数说明**：
- `-p`：递归创建目录，即如果父目录不存在，则一并创建。

**使用示例**：


```bash
# 创建一个名为 new_dir 的目录
mkdir new_dir

# 创建一个多级目录 structure/sub1/sub2
mkdir -p structure/sub1/sub2
```
#### 5. `rmdir` 命令

**简介**：`rmdir` 命令用于删除空目录。

**参数说明**：
- `-p`：递归删除目录，只有当子目录都为空时才能删除父目录。

**使用示例**：


```bash
# 删除一个空目录 empty_dir
rmdir empty_dir

# 递归删除一个多级空目录 structure/sub1/sub2
rmdir -p structure/sub1/sub2
```
#### 6. `cp` 命令

**简介**：`cp` 命令用于复制文件或目录。

**参数说明**：
- `-r` 或 `-R`：递归复制目录及其内容。
- `-v`：显示详细的复制过程。

**使用示例**：


```bash
# 复制 file1.txt 到 file2.txt
cp file1.txt file2.txt

# 递归复制 dir1 到 dir2
cp -r dir1 dir2
```
#### 7. `mv` 命令

**简介**：`mv` 命令用于移动或重命名文件或目录。

**使用示例**：


```bash
# 将 file1.txt 重命名为 file2.txt
mv file1.txt file2.txt

# 将 dir1 移动到 dir2（如果 dir2 不存在，则重命名 dir1 为 dir2）
mv dir1 dir2
```
#### 8. `rm` 命令

**简介**：`rm` 命令用于删除文件或目录。

**参数说明**：

- `-r` 或 `-R`：递归删除目录及其内容。
- `-f`：强制删除，不提示确认。
- `-v`：显示详细的删除过程。

**使用示例**：


```bash
# 删除 file1.txt 文件
rm file1.txt

# 递归删除 dir1 目录及其内容，并强制删除不提示确认
rm -rf dir1
```
#### 9.` cat`命令

* **简介**：显示文件内容，或连接文件内容。

* **参数说明**：无特殊参数，后面跟文件名。

* **使用示例**：

  ```bash
  cat file.txt       # 显示file.txt的内容
  cat file1.txt file2.txt > combined.txt  # 连接file1.txt和file2.txt的内容，并保存到combined.txt中
  ```

#### 10. `find` 命令

**简介**：`find` 命令用于在指定目录下查找文件。它可以基于文件名、文件权限、文件类型等各种条件来搜索文件。

**参数说明**：
- `-name`：按照文件名搜索，可以使用通配符。
- `-type`：按照文件类型搜索，如普通文件、目录等。
- `-size`：按照文件大小搜索。
- `-mtime`：按照文件修改时间搜索。
- `-user`：按照文件所有者搜索。

**使用示例**：
```bash
find /home/user -name "*.txt"  # 在/home/user目录下查找所有.txt文件
find / -type d -name "mydir"   # 在整个文件系统中查找名为mydir的目录
```

#### 11. `file` 命令

**简介**：`file` 命令用于确定文件的类型。它会尝试识别给定文件的类型，并显示相关信息。

**参数说明**：
- 通常不需要额外的参数，只需提供要检查的文件名。

**使用示例**：
```bash
file /etc/passwd  # 查看/etc/passwd文件的类型
```

#### 12. `touch` 命令

**简介**：`touch` 命令用于创建空文件或更新文件的时间戳。如果文件不存在，`touch` 会创建一个新的空文件；如果文件已经存在，`touch` 会更新文件的访问和修改时间。

**参数说明**：
- 通常不需要额外的参数，只需提供要创建或更新的文件名。
- `-c` 或 `--no-create`：不创建不存在的文件。
- `-t`：使用指定的时间而非当前时间更新文件时间戳。

**使用示例**：
```bash
touch newfile.txt  # 创建一个名为newfile.txt的空文件
touch existingfile.txt  # 更新existingfile.txt文件的时间戳
```

### 二、Linux用户和用户组管理

#### **1.用户管理**

`useradd -m -g [组名] [用户名]`：添加新用户，并指定用户所属组。`-m` 表示自动建立用户家目录。

**1.1 useradd**

* **简介**：用于创建新用户。

* **参数说明**：

  - `-m`：创建用户的主目录。
  - `-g`：指定用户所属的初始组。

* **使用示例**：

  ```bash
  useradd -m -g users newuser  # 创建一个新用户newuser，并将其添加到users组
  ```

`passwd [用户名]`：设置或更改用户的密码。

**1.2 passwd**

* **简介**：用于设置或更改用户密码。

* **使用示例**：

  ```bash
  passwd newuser  # 为newuser用户设置密码
  ```

`userdel -r [用户名]`：删除用户及其家目录。

**1.3 userdel**

* **简介**：用于删除用户。

* **参数说明**：

  - `-r`：同时删除用户的主目录。

* **使用示例**：

  ```bash
  userdel -r newuser  # 删除newuser用户及其主目录
  ```

`cat /etc/passwd | grep [用户名]`：确认用户信息，新用户信息保存在 `/etc/passwd` 文件中。

#### **2.组管理**

`groupadd [组名]`：添加新组。

**2.1 groupadd**

* **简介**：用于创建新组。

* **使用示例**：

  ```bash
  groupadd newgroup  # 创建一个名为newgroup的新组
  ```

`groupdel [组名]`：删除组。

**2.2 groupdel**

* **简介**：用于删除组。

* **使用示例**：

  ```bash
  groupdel newgroup  # 删除newgroup组
  ```

`cat /etc/group`：确认组信息，组信息保存在 `/etc/group` 文件中。

`chgrp -R [组名] [文件/目录名]`：递归修改文件或目录的所属组。

#### **3.其他用户管理命令**

`id [用户名]`：查看用户的UID和GID信息。

`who`：查看当前所有登录的用户列表。

`whoami`：查看当前登录用户的账户名。

`usermod -g [组名] [用户名]`：修改用户的主组。

`usermod -G [附加组名] [用户名]`：修改用户的附加组。

`chown -R [用户名]:[组名] [文件/目录名]`：递归修改文件或目录的拥有者和所属组。

**chown**

* **简介**：用于更改文件或目录的所有者和所属组。

* **参数说明**：

  - `-R`：递归地更改指定目录及其内容的所有者和组。

* **使用示例**：

  ```bash
  chown -R newuser:newgroup /path/to/directory  # 更改目录及其内容的所有者和组
  ```

### 三、Linux vi/vim

#### **1.vi/vim简介**

vi是Unix/Linux系统中最基本的文本编辑器，vim是从vi发展出来的一个功能更强大的文本编辑器。

```bash
vim filename.txt  # 打开或创建名为filename.txt的文件进行编辑
```

在vim中，可以使用`i`进入插入模式，编辑文本后按`Esc`退出插入模式，然后输入`:w`保存，`:q`退出，或使用`:wq`或`ZZ`（大写）保存并退出。

#### **2.vi/vim模式**

- 命令模式：启动vi/vim后默认进入的模式，可输入各种命令来操作文本。
- 输入模式：用于输入文本内容。
- 命令行模式：在vi/vim底部命令行输入命令，执行保存、退出等操作。

#### **3.常用命令**

- `i`：进入输入模式，在当前光标位置前插入文本。
- `x`：删除当前光标所在字符。
- `:w`：保存文件。
- `:q`：退出vi/vim。
- `:q!`：强制退出vi/vim，不保存修改。
- `dd`：删除当前行。
- `yy`：复制当前行。
- `p`：在当前光标位置后粘贴文本。

### 四、Linux yum命令

#### **1.yum简介**

yum是Yellowdog Updater Modified的缩写，是Fedora、RedHat以及CentOS中的Shell前端软件包管理器，能够自动查找、安装、升级、卸载软件包，并自动解决软件包之间的依赖关系。

#### **2.常用yum命令**

`yum check-update`：列出所有可更新的软件清单。

`yum update`：更新所有软件。

`yum install [软件包名]`：安装指定的软件包。

- **简介**：用于安装软件包。

* **使用示例**：

  ```bash
  yum install httpd  # 安装httpd软件包
  ```

`yum update [软件包名]`：更新指定的软件包。

- **简介**：用于更新所有软件包或指定软件包。

* **使用示例**：

  ```bash
  yum update httpd  # 更新httpd软件包
  ```

`yum list`：列出所有可安装的软件清单。

`yum remove [软件包名]`：删除软件包。

- **简介**：用于删除软件包。

* **使用示例**：

  ```bash
  yum remove httpd  # 删除httpd软件包
  ```

`yum search [关键字]`：查找软件包。

### 五、Linux apt命令

#### **1.apt简介**

apt是Advanced Package Tool的缩写，是Debian及其衍生版（如Ubuntu）中的软件包管理工具，用于自动下载、配置、安装和升级软件包。

#### **2.常用apt命令**

`apt list`：查询具体包的版本信息。

`apt search [关键字]`：模糊查找包。

`apt install [软件包名]`：安装软件包。

- **简介**：用于安装软件包。

* **使用示例**：

  ```bash
  apt install apache2  # 安装apache2软件包
  ```

`apt remove [软件包名]`：卸载软件包。

`apt update`：获取更新可用软件包列表。

- **简介**：用于更新软件包列表。

* **使用示例**：

  ```bash
  apt update  # 更新软件包列表
  ```

`apt upgrade`：升级所有可升级的软件包。

- **简介**：用于升级所有可升级的软件包。

* **使用示例**：

  ```bash
  apt upgrade  # 升级所有可升级的软件包
  ```

`apt autoremove`：卸载所有自动安装且不再使用的软件包。

<br>

> 请注意，yum和apt是特定于发行版的包管理器，yum主要用于Red Hat系列（如CentOS、Fedora），而apt则用于Debian系列（如Ubuntu、Debian本身）。因此，在使用时请根据您的Linux发行版选择合适的包管理器。

### 六、其他命令

#### 1.打包/解包

**tar命令**

* **简介**：用于文件的打包和解包。
* **参数说明**：
  - `-c`：创建新的归档文件。
  - `-v`：详细模式，显示进度。
  - `-f`：指定归档文件名。
  - `-x`：从归档文件中提取文件。
* **使用示例**：
  - 打包：`tar -cvf archive.tar file1 file2` （将file1和file2打包成archive.tar）
  - 解包：`tar -xvf archive.tar` （从archive.tar中解包文件）

#### 2.压缩/解压缩

**gzip命令**

* **简介**：用于文件的压缩和解压缩，采用gzip格式。
* **参数说明**：
  - `-d`：解压缩文件。
* **使用示例**：
  - 压缩：`gzip file` （压缩file文件为file.gz）
  - 解压缩：`gzip -d file.gz` （解压缩file.gz文件）

**zip和unzip命令**

* **zip命令简介**：用于压缩文件。
* **unzip命令简介**：用于解压缩zip格式的文件。
* **参数说明**：
  - `zip`：无需额外参数，直接指定压缩文件名和要压缩的文件。
  - `unzip`：无需额外参数，直接指定要解压的zip文件。
* **使用示例**：
  - 压缩：`zip archive.zip file1 file2` （将file1和file2压缩成archive.zip）
  - 解压缩：`unzip archive.zip` （解压缩archive.zip文件）

#### 3.查看系统信息命令

**df命令**

* **简介**：显示磁盘分区上的可用和已使用的磁盘空间。
* **参数说明**：
  - `-h`：以人类可读的格式显示大小（如K，M，G）。
* **使用示例**：`df -h` （显示各磁盘分区的使用情况）

**ps命令**

* **简介**：显示当前进程的状态。
* **参数说明**：
  - `aux`：a表示显示所有进程，u表示显示用户信息，x表示显示所有进程（包括无终端的进程）。
* **使用示例**：`ps aux` （显示所有进程的详细信息）

#### 4.远程管理常用命令

**ssh命令**

* **简介**：用于安全地连接到远程服务器。
* **参数说明**：
  - 无需额外参数，直接指定用户名和主机名。
* **使用示例**：`ssh username@hostname` （以username用户身份连接到hostname主机）

#### 5.重定向 > & >>

1. **`>`**：这个符号用于重定向命令的输出到一个文件，如果文件已存在，则会覆盖该文件的内容。

   **示例**：

   ```bash
   echo "Hello, World!" > output.txt
   ```

   这个命令会将文本“Hello, World!”写入`output.txt`文件。如果`output.txt`已经存在，其内容将被这段文本替换。

2. **`>>`**：这个符号也用于重定向命令的输出到一个文件，但如果文件已存在，它会将内容追加到文件的末尾，而不是覆盖原有内容。

   **示例**：

   ```bash
   echo "Another line of text." >> output.txt
   ```

   如果`output.txt`文件已经包含“Hello, World!”，执行上述命令后，文件内容将变为：

   ```
   Hello, World!
   Another line of text.
   ```

#### 6.管道 |

**`|`**：管道符号用于将一个命令的输出作为另一个命令的输入。这允许你创建一系列命令来处理数据，每个命令都以前一个命令的输出作为输入。

**示例**：

```bash
cat output.txt | grep "World"
```

这个命令会读取`output.txt`文件的内容，并通过`grep`命令搜索包含“World”的行。如果`output.txt`包含“Hello, World!”，则该命令会输出这一行。

另一个复杂一点的例子是使用`ps`和`grep`来查找特定进程：

```bash
ps aux | grep firefox
```

这个命令会列出所有运行中的进程，并通过`grep`来搜索包含“firefox”的行，从而找到Firefox进程的详细信息。

<br>

> 重定向和管道是Unix/Linux命令行中非常强大的工具，它们允许用户以灵活且高效的方式处理数据和命令输出。