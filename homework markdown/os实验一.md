# 实验一 作业
 ## 姓名：李国旗      
 学号：20222241410   
---

## 一、more、cat、find、管道、重定向、grep等命令的用法

### 1.more的用法  
在Linux中，more是一个用于逐页显示文本文件内容的命令行工具。它允许您在终端窗口中逐页浏览大文件，而不是一次性将整个文件内容输出到屏幕上。以下是more命令的基本用法：  
<div style="text-align: center; color:red;">
    <code>more [options] [file]</code>
</div>  
[options]->可选参数，可以用来控制more的行为.


[file]->要查看的文件的路径.


一旦你运行了more命令，它会显示文件的第一页内容，并等待你的指令。以下是一些常用的more命令操作：

按下 Space 键或者 Page Down 键：显示下一页内容。  
按下 Enter 键：显示下一行内容。  
按下 q 键：退出more命令。  
按下 / 键，然后输入搜索词并按下 Enter 键：在文件中搜索指定的字符串，并显示匹配行的下一页。  
more命令还支持一些选项，如 -d 用于显示文件的信息， -f 用于统计行数， -p 用于指定显示百分比等。  
在Ubuntu下的示例：  
![alt text](image.png)


### 2.cat的用法  
cat 是一个常用的命令行工具，用于显示文件内容。它的名称源自 concatenate（连接）的缩写，因为它最初的作用是将多个文件连接在一起显示，但现在它通常用于显示单个文件的内容。

基本语法是：  
<div style="text-align: center; color:red;">
    <code>cat [选项] [文件]</code>
</div>  
[选项]->可以是一系列的选项，用来控制 cat 命令的行为。  

[文件]->要显示内容的文件路径  
一些常用的选项包括：  
-n：显示行号。  
-b：显示非空行的行号。  
-E：在每行的结尾显示一个 $ 符号。  
在Ubuntu下的示例：  

![alt text](image-1.png)  
注意：  
more与cat的区别：  
如果您只需要查看文件的内容，并且文件不是很大，可以使用 cat 命令。但如果文件较大，或者您想要逐页查看文件内容，那么更适合使用 more 命令。


### 3.find的用法  
find 命令用于在指定的目录树中搜索文件，并根据指定的条件进行匹配。  
它的基本语法是：  
<div style="text-align: center; color:red;">
    <code>find [路径] [表达式]</code>
</div>  
[路径]：指定要搜索的目录路径，默认为当前目录。   

[表达式]：用于指定搜索条件的表达式  
一些常用的 find 表达式包括：  
-name：按照文件名进行匹配。  
-type：按照文件类型进行匹配，比如普通文件、目录、符号链接等。  
-size：按照文件大小进行匹配。  
-exec：对匹配到的文件执行指定的命令。  
在Ubuntu下的示例：  

![alt text](image-2.png)

### 4.管道的用法  
管道（Pipeline）是一种在Unix和类Unix操作系统中常见的概念，用于将一个命令的输出作为另一个命令的输入。通过管道，可以将多个命令串联起来，形成一个命令序列，使得每个命令的输出都成为下一个命令的输入，从而实现复杂的数据处理和操作。  
在Unix和类Unix系统中，管道由竖线符号 | 表示。  
例如：
<div style="text-align: center; color:red;">
    <code>command1 | command2</code>
</div>  
这个命令的含义是将 command1 的输出作为 command2 的输入。command1 和 command2 可以是任何合法的命令，它们之间通过管道连接起来，形成一个命令序列。

通过管道，可以实现诸如数据过滤、数据转换、数据排序、数据统计等各种复杂的数据处理任务。管道是Unix哲学中的重要概念之一，体现了“将简单的程序组合成复杂的系统”的设计原则。  


在Ubuntu下的示例：
![alt text](image-3.png)  
说明：ls的输出作为grep的输入，grep的作用是过滤出里面含关键字"osdir"的文件
### 5.重定向的用法  
重定向是将命令的输入输出重定向到其他地方的过程。在Unix和类Unix操作系统中，重定向通常用于控制命令的输入来源和输出目标。  
输出重定向：使用 > 符号将命令的标准输出重定向到指定文件，如果目标文件已存在，则会被覆盖。  
例如：
<div style="text-align: center; color:red;">
    <code>ls > test.txt</code>
</div>  
在Ubuntu下的示例：  

![alt text](image-4.png)

追加输出重定向：使用 >> 符号将命令的标准输出追加到指定文件末尾，如果目标文件不存在，则会创建。  
例如：  
<div style="text-align: center; color:red;">
    <code>echo "Hello, World!" >> test.txt</code>
</div>  
在Ubuntu下的示例：  

![alt text](image-5.png)  

标准错误重定向：使用 2> 符号将命令的标准错误重定向到指定文件。  
例如：
<div style="text-align: center; color:red;">
    <code>command 2> error.txt</code>
</div>  
在Ubuntu下的示例：  

![alt text](image-6.png)

### 6.grep的用法  
grep 是一个常用的命令行工具，用于在文本文件中搜索指定的模式（字符串）。  
它的基本语法是：
<div style="text-align: center; color:red;">
    <code>grep [选项] 模式 [文件]</code>
</div>  
[选项]：可以是一系列的选项，用来控制 grep 命令的行为。  

模式：要搜索的模式或正则表达式。    
[文件]：要搜索的文件路径，如果未指定文件，则 grep 将从标准输入中读取数据进行搜索。  
基本用法：
<div style="text-align: center; color:red;">
    <code>grep "pattern" file.txt</code>
</div>  
在Ubuntu下的示例：  

![alt text](image-7.png)  
递归搜素：  
<div style="text-align: center; color:red;">
    <code>grep -r "pattern" directory/</code>
</div>  
在Ubuntu下的示例：  

![alt text](image-8.png)

## 二、Shell脚本  
### （1）脚本内容  
![alt text](image-9.png)

### （2）f1、f2、f3内容  

![alt text](image-10.png)

## 三、hello.c  
### （1）代码  
![alt text](image-11.png)
### （2）输出  
![alt text](image-12.png)

# LLM实验⼀：大模型部署,qwen1.5-0.5b  
## 1.模型部署  
### 1.1模型下载
首先，我们现在魔搭平台命令行中用如下命令创建一个名叫module_download的文件夹：  
<div style="text-align: center; color:red;">
    <code>mkdir module_download</code>
</div>  

![alt text](image-13.png)  
然后，我们需要下载模型到文件夹中，我们这里直接使用网站自带的git功能：  
![alt text](image-14.png)  
我们先在命令行cd到module_download文件夹，再在命令行中使用语句：  
<div style="text-align: center; color:red;">
    <code>git clone https://www.modelscope.cn/qwen/Qwen1.5-0.5B-Chat-GGUF.git</code>
</div>  
这样我们就把模型下载到了module_download文件夹下。 

### 1.2 下载llama.cpp  
类似于模型下载，我们在目录下用同样的方法把llama.cpp下载到目录下方。  
<div style="text-align: center; color:red;">
    <code>git clone https://github.com/ggerganov/llama.cpp</code>
</div>  


结果如图所示：
![alt text](image-15.png)  
下载完后，我们需要对llama.cpp进行编译，这里我们cd到llama.cpp里进行编译：  
<div style="text-align: center; color:red;">
    <code>cd llama.cpp  
    
make -j</code>
</div>  

### 1.3 加载模型，并执行  
在llama.cpp⽬录中执⾏命令：  

<div style="text-align: center; color:red;">
    <code> ./main -m /mnt/workspace/module_download/llama.cpp/qwen/Qwen1.5-0.5B-Chat-GGUF/qwen1_5-0_5b-chat-q5_k_m.gguf -n 512 --color -i -cml</code>
</div>  
运行成功后便可使用模型。

![alt text](image-17.png)

## 2.基于OpenVINO的模型量化实践
### 2.1 安装基本环境
首先我们在魔搭平台命令行中创建一个名叫qwen-ov的文件夹：  
<div style="text-align: center; color:red;">
    <code> mkdir qwen-ov</code>
</div>  
结果如图所示：

![alt text](image-19.png)
接着创建python虚拟环境：  
<div style="text-align: center; color:red;">
    <code>python -m venv qwenVenv</code>
</div>  

![alt text](image-21.png)
激活环境：
<div style="text-align: center; color:red;">
    <code>source qwenVenv/bin/activate</code>
</div>  

![alt text](image-22.png)
在activate虚拟环境之后，我们直接在虚拟环境中使用：
<div style="text-align: center; color:red;">
    <code>pip install wheel setuptools</code>
</div>  

![alt text](image-23.png)

在执行pip install -r requirements.txt之前，我们需要在创建该文件，直接去GitHub官网复制：

![alt text](image-24.png)
粘贴到文件中：
![alt text](image-26.png)
现在执行：
<div style="text-align: center; color:red;">
    <code>pip install -r requirements.txt</code>
</div>  

结果如下图：
![alt text](image-27.png)
等待安装完成：
![alt text](image-28.png)

### 2.2下载模型
首先，我们先创建一个安装模型的脚本文件：  
<div style="text-align: center; color:red;">
    <code>touch download_model.sh</code>
</div>  
再将以下内容编辑到脚本文件中：
<div style="text-align: center; color:red;">
    <code>export HF_ENDPOINT=https://hf-mirror.com
huggingface-cli download --resume-download --local-dir-use-symlinks False Qwen/Qwen1.5-0.5B-Chat --local-dir Qwen/Qwen1.5-0.5B-Chat</code>
</div>  

![alt text](image-29.png)
为脚本文件添加执行权限：
<div style="text-align: center; color:red;">
    <code>chmod +x download_model.sh</code>
</div>  
执行脚本文件：
<div style="text-align: center; color:red;">
    <code>./download_model.sh</code>
</div> 

![alt text](image-30.png)

### 2.3 转换模型
首先，我们先在GitHub官网把convert.py复制到我们模型目录下：

![alt text](image-31.png)

![alt text](image-32.png)
之后执行命令：
<div style="text-align: center; color:red;">
    <code>python3 convert.py --model_id /mnt/workspace/qwen-ov/Qwen/Qwen1.5-0.5B-Chat --precision int4 --output /mnt/workspace/qwen-ov/Qwen/Qwen1.5-0.5B-Chat/Qwen1.5-0.5B-Chat-ov</code>
</div> 
这一步注意要确保自己的网络能够连接上该网站，并且路径一定要正确！

![alt text](image-33.png)
到这说明你模型已经转换成功了！
![alt text](image-34.png)

### 2.4加载模型并执行
首先我们需要将chat.py从GitHub官网上复制下来：
![alt text](image-35.png) 
我们在轻量化模型目录下创建chat.py文件并将内容粘贴进去：
![alt text](image-36.png)
执行以下指令加载并执行模型
<div style="text-align: center; color:red;">
    <code>python3 chat.py --model_path /mnt/workspace/qwen-ov/Qwen/Qwen1.5-0.5B-Chat/Qwen1.5-0.5B-Chat-ov --max_sequence_length 4096 --device CPU</code>
</div> 
这一步也要注意路径问题！

![alt text](image-37.png)
看见‘用户’二字说明此次加载已经成功！可以开始向模型询问问题了！
示例：
![alt text](image-38.png)
这里我们询问了一个问题，但是有一些问题，似乎是我们的权限不够。但是问题是能正常回答的。
![alt text](image-39.png)

![alt text](image-40.png)
![alt text](image-41.png)
![alt text](image-42.png)

## 3. 开展多个模型部署的横向对比
### 3.1 智谱 ChatGLM3-6B
#### 3.1.1 创建一个文件夹并git仓库
<div style="text-align: center; color:red;">
    <code>mkdir model_3</code>
</div> 
<div style="text-align: center; color:red;">
    <code>git clone https://github.com/THUDM/ChatGLM3</code>
</div> 

![alt text](image-43.png)
结果如图：
![alt text](image-44.png)
#### 3.1.2创建虚拟环境
<div style="text-align: center; color:red;">
    <code>python -m venv yourname</code>
</div> 
<div style="text-align: center; color:red;">
    <code>source model_3/ChatGLM3/venv/bin/activate</code>
</div> 

![alt text](image-45.png)  
![alt text](image-46.png)
### 3.1.3 使用pip安装依赖
在虚拟环境中，使用如下命令进行依赖包的安装：
<div style="text-align: center; color:red;">
    <code>pip install -r requirements.txt</code>
</div> 

![alt text](image-47.png)
### 3.1.4 下载模型
去魔搭平台官网下载模型：
![alt text](image-48.png)
在ChatGLM3下创建一个名叫model的文件夹并将模型下载到里面：
<div style="text-align: center; color:red;">
    <code>mkdir model</code>
</div> 
<div style="text-align: center; color:red;">
    <code>git clone https://www.modelscope.cn/ZhipuAI/chatglm3-6b.git</code>
</div> 
下载好之后如图所示：

![alt text](image-49.png)
下载好模型之后我们需要进入basic_demo修改文件的路径：
![alt text](image-51.png)
我们需要将模型路径换成我们实际的路径，如下图。
![alt text](image-50.png)
修改完路径之后，执行以下语句即可开始使用模型：
![alt text](image-52.png)
回答效果如下图：
![alt text](image-53.png)

### 3.2