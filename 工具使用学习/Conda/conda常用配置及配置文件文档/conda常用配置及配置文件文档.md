## Conda 配置文档地址

https://conda.io/projects/conda/en/latest/configuration.html

## Conda 常用镜像配置

```
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch-lts: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
envs_dirs:  # 目录
  - D:/apps/conda/envs
pkgs_dirs: 
 - XXXX
```

## .condarc文档内容如下

### 清华镜像源

```
channels:
  - defaults
    show_channel_urls: true
    default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
    custom_channels:
      conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
      msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
      bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
      menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
      pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
      simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

### 中科大镜像源
``` 
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/
```

### 阿里镜像源
```
conda config --add channels https://mirrors.aliyun.com/pypi/simple/
```

### 豆瓣的python的源

```
conda config --add channels http://pypi.douban.com/simple/ 
```

### Python与算法社区《conda国内镜像修改（最新版）》

https://zhuanlan.zhihu.com/p/95100538

### 清华镜像源
``` 
channels:
 - https://mirrors.tuna.tsinghua.edu.cn/tensorflow/linux/cpu/

 - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/

 - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/

 - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

 - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
```

### pip 源
老聂学技术 《国内常用源镜像地址》
https://www.cnblogs.com/niewd/p/12218552.html

清华 https://pypi.tuna.tsinghua.edu.cn/simple
阿里云 http://mirrors.aliyun.com/pypi/simple/
中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/
华中理工大学 http://pypi.hustunique.com/
山东理工大学 http://pypi.sdutlinux.org/ 
豆瓣 http://pypi.douban.com/simple/

