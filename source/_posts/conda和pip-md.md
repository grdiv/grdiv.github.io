---
title: conda和pip.md
date: 2022-11-28 23:34:17
tags: linux python
---
# pip与conda安装包的区别

- [Anaconda官方博客](https://www.anaconda.com/blog/understanding-conda-and-pip)
- [工具篇：conda and pip](https://zhuanlan.zhihu.com/p/508506160)

# conda与virtualenv,venv

////

# conda与Anaconda, miniconda

////

# conda基础命令

	# 创建环境
	conda create -n env_name python==3.6

	# 查看已有环境
	conda info --envs
	conda env list

	# 激活/退出环境
	conda activate env_name
	conda deactivate 或者 conda activate base

	# 删除环境
	conda remove -n env_name --all

	# 不在环境中查看安装的包
	conda list -n env_name

	# 给指定环境安装包
	conda install -n envname xxx=1.0.0

	# 克隆环境（envname是被克隆的环境）
	conda create --name clone_env --clone envname

	# 搜索包
	conda search numpy

# conda源配置

## pip
pip 安装 可以直接 -i 指定源：
```
pip install numpy -i https://mirrors.aliyun.com/pypi/simple/  
pip intsall -r requirements.txt 
```
国内的一些源：
```
清华：https://pypi.tuna.tsinghua.edu.cn/simple

阿里云：https://mirrors.aliyun.com/pypi/simple/

中国科技大学: https://pypi.mirrors.ustc.edu.cn/simple/

华中理工大学：https://pypi.hustunique.com/

山东理工大学：https://pypi.sdutlinux.org/ 

豆瓣：https://pypi.douban.com/simple/

```

## pip 设置代理

安装时的设置（注意打开代理）：  
```
pip install --proxy=127.0.0.1:7890 tensorflow-gpu==2.2.0 keras==2.3.1
```


## conda
conda指定源：
```
conda install xxx -c xxx
```
[https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)

- 文件： ~/.condarc
- 配置清华源（注意一定要用http而不是https！）
```
channels:
  - defaults
show_channel_urls: true
channel_alias: https://mirrors.tuna.tsinghua.edu.cn/anaconda
default_channels:
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: http://mirrors.tunas.tsinghua.edu.cn/anaconda/cloud
  menpo: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud

```

- 查看源
```
conda config --show channels
```

- 查看源配置
```
conda info
```
配好清华源后的输出。
```
channels:
  - defaults
show_channel_urls: true
channel_alias: https://mirrors.tuna.tsinghua.edu.cn/anaconda
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud

```

- 删除源 如：
```
conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
```