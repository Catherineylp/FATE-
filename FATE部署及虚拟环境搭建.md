# FATE部署及其虚拟环境创建

### 安装EPLE
```bash
sudo yum install epel-release -y
```

### 换yum源（阿里云）
```bash
sudo wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo
```

### 安装python3.6
```bash
yum install python36 -y yum install python36-devel -y
```
### 查看Python版本以确认正确安装
```bash
python3
```

### 安装pip3
```bash
yum install python36-pip -y
```
### 查看pip3版本 
```bash
pip3 -v
```

### 安装virtualenv 
```bash
pip3 install virtualenv –user
```

### 创建目录存放代码 
```bash
mkdir CV
```
### 进入创建的目录，创建虚拟环境 
```bash
cd CV 
virtualenv -p python3 venv
``` 
### 进入虚拟环境 
```bash
source venv/bin/activate
```
<img src=./进入虚拟环境.jpg>

### 查看cuda版本
```bash
nvcc -V
```
<img src=./查看cuda版本.jpg>

### 装带GPU的pytorch
进入[pytorch官网](https://pytorch.org/)，选择对应的cuda版本，复制命令安装。
<img src=./pytorch版本.jpg>

（安装过程出现timed out，原因是源不稳定，多试几次）

<img src=./pytorch安装完成.jpg>

### 测试pytorch(GPU)是否安装成功
<img src=./测试pytorch是否安装成功.jpg>

能看到上述结果，说明pytorch gpu版本安装成功。

### 安装cupy
```bash
pip3 install cupy_cuda90 //如果服务器上cuda是9.0版本
```
安装过程会特别慢，建议换pip3的源（清华）。
```bash
pip3 install pip -U
pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```
<img src=./换tuna源.jpg>

### 从github上拖代码:
```bash
wget https://github.com/FederatedAI/FATE.git
```
<img src=./github源码.jpg>

### 解压代码 
```bash
upzip FATE.zip
```

### 安装依赖 
```bash
pip install -r requirements.txt
```

<img src=./安装依赖.jpg>

出现上述报错，安装gcc。

```bash
 sudo yum install gcc-c++
 ```
 安装gcc后再次安装依赖，安装成功如下图所示。
 <img src=./依赖安装成功.jpg>