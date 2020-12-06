# Guide-for-the-installation-of-Paddlehub
# Paddlehub安装教程  

# 1. 安装PaddlePaddle  
   （1） 环境依赖  
          Python>=3.6  
          PaddlePaddle>=2.0.0rc  

   （2） 安装PaddlePaddle深度学习框架  
          登录飞桨官网，选择适合自己的安装方式（推荐使用pip安装）  
          选择CPU/GPU：  
          如果您的计算机没有 NVIDIA® GPU，请安装CPU版的PaddlePaddle。  
          如果您的计算机有 NVIDIA® GPU，并且满足以下条件，推荐安装GPU  
          版的PaddlePaddle：  
          CUDA 工具包 9.0/10.0/10.1/10.2 配合 cuDNN v7.6.5+  
          GPU运算能力超过3.0的硬件设备  
          （注: 目前官方发布的windows安装包仅包含 CUDA 9.0/10.0/10.1/10.2，不包含 CUDA 9.1/9.2，如需使用，需通过源码自行编译。）  

    验证安装：
    安装完成后您可以使用 python 进入python解释器，输入import paddle.fluid as fluid，再输入 fluid.install_check.run_check()。
    如果出现Your Paddle Fluid is installed succesfully!，说明您已成功安装。

# 2. 安装Paddlehub
   （1） 安装命令 
           pip install paddlehub==2.0.0b  
          （注：PaddleHub的预训练模型和预置数据集需要连接服务端进行下载，请确保机器可以正常访问网络。若本地已存在相关的数据集和预训练模型，则可以离线运行PaddleHub。）  

   （2） 检查连接状态  
           使用PaddleHub下载数据集、预训练模型等，要求机器可以访问外网。通过使用server_check()可以检查本地与远端PaddleHub-Server的连接状态，使用方法如下：  
           import paddlehub  
           paddlehub.server_check()  
        （如果可以连接远端PaddleHub-Server，则显示Request Hub-Server successfully。）  
        （如果无法连接远端PaddleHub-Server，则显示Request Hub-Server unsuccessfully。）  

# 3. 问题解决
   3.1出现export GIT_PYTHON_REFRESH=quiet问题  
         （1）引入包并添加变量  
              import os  
              os.environ["GIT_PYTHON_REFRESH"] = "quiet"  
              import json  
              from git.repo import Repo  
              from git.repo.fun import is_git_dir  
         （2）Linux操作系统下  
              vim /etc/profile  
              添加 ：export GIT_PYTHON_REFRESH=quiet  
              wq 保存  
              source /etc/profile  
          (3)没有安装git  
               sudo apt install git  

   3.2出现ModuleNotFoundError: No module named 'sentencepiece'
       （在Anaconda下运行程序时，会出现这种情况）  
        （1）打开 anaconda prompt  
        （2）激活pytorch环境后  
        （3）输入 conda install -c roccqqck sentencepiece 进行安装  

                
