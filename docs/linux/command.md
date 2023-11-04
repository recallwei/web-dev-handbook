# 常用命令

## pwd

pwd = print working directory, 即打印当前工作目录。

```bash
pwd
```

## ls

### 查看当前目录下的文件

```bash
ls
```

### 以单列的形式显示文件

```bash
ls -1
```

### 以详细信息的形式显示文件

```bash
ls -l
```

## cd

### 切换目录

cd = change directory, 即切换目录。

```bash
cd <PATH> # 相对路径，不以 / 开头，表示从当前目录开始
cd /<PATH> # 绝对路径，以 / 开头，表示从根目录开始
```

### 返回上级目录

```bash
cd ..
```

## mkdir

### 创建目录

mkdir = make directory, 即创建目录。

```bash
mkdir <PATH> # 相对路径，不以 / 开头，表示从当前目录开始
mkdir /<PATH> # 绝对路径，以 / 开头，表示从根目录开始
```

## mv

### 移动文件

mv = move, 即移动文件或目录。

```bash
mv <SOURCE> <TARGET>
```

### 重命名文件

如果源文件和目标文件位于同一目录下，则相当于重命名文件。

## touch

### 创建文件

touch 用于创建文件。

```bash
touch [PATH]/<FILENAME>
```

### 批量创建文件

传递多个文件名参数，即可批量创建文件。

```bash
touch [PATH]/<FILENAME1> [PATH]/<FILENAME2> ...
```

## rm

### 删除文件

rm = remove, 即删除文件。

```bash
rm [PATH]/<FILENAME>
```

### 批量删除文件

传递多个文件名参数，即可批量删除文件。

```bash
rm [PATH]/<FILENAME1> [PATH]/<FILENAME2> ...
```

### 根据模式删除文件

```bash
rm <PATH>/* # 删除 PATH 目录下的所有文件
rm <PATH>/*.txt # 删除 PATH 目录下的所有 txt 文件
rm <PREFIX>* # 删除以 PREFIX 开头的文件
```

### 删除目录

Linux 删除其实是一个递归的过程，即先删除目录下的所有文件，再删除目录。  
-r = recursive, 即递归删除。

```bash
rm -r <PATH>
```

### 强制删除目录

-f = force, 即强制删除。

```bash
rm -rf <PATH>
```

## vi

vi 是一个文本编辑器，它在 Linux 系统中非常流行。它的特点是功能强大，但是使用起来比较复杂。

### 编辑模式

使用 i 键进入编辑模式，使用 ESC 键退出编辑模式。

### 命令模式

使用 : 键进入命令模式，常用的命令如下：

- q 退出命令模式
- q! 强制退出命令模式
- wq 保存并退出命令模式
- wq! 强制保存并退出命令模式

## cat

cat = concatenate，即连接，用于查看文件内容、连接或组合多个文件。

### 查看文件内容

```bash
cat <FILENAME>
```

### 连接多个文件

将多个文件连接起来，输出到一个文件中。

```bash
cat <FILENAME1> <FILENAME2> ... > <TARGET>
```

## more

more 用于分页查看文件内容。

```bash
more <FILENAME>
```

点击空格键查看下一页，点击回车键查看下一行。

## less

less 用于分页查看文件内容。

```bash
less <FILENAME>

```

与 more 不同的是，less 支持向上翻页，按 b 键即可向上翻页。  
退出 less，按 q 键即可。

## head

head 用于查看文件的前几行。

```bash
head -n <LINE_NUMBER> <FILENAME>
head -n 5 <FILENAME> # 查看文件的前 5 行
```

## tail

tail 用于查看文件的后几行。

```bash
tail -n <LINE_NUMBER> <FILENAME>
tail -n 5 <FILENAME> # 查看文件的后 5 行
```

## echo

### 输出文本

echo 用于输出文本。

```bash
echo <TEXT>
```

### 输出文本到文件

```bash
echo <TEXT> > <FILENAME>
```

## lsof

lsof 用于查看端口占用。

```bash
lsof -i:pid # pid 为端口号
```

## kill

kill 命令用于强制终止进程。

```bash
kill -9 pid # pid 为进程号
kill -9 node # 强制终止 node 进程
```
