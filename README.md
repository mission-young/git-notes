## Git notes

### 局域网创建Git服务器
服务器端代码编写功能较弱，缺乏必要的调试工具，因而希望在本机编写随后同步到服务器。在内网环境中，无法通过Github来管理项目。通过简单配置一个内网git服务器，能够很方便地实现代码管理。

首先在服务器创建项目目录(与本地已有项目同名),如`/home/yfs/python_notes`. 并在目录运行

    git init --bare
在本地项目目录下执行

    git init 
    git add .
    git commit -m "first"

随后关联本地仓库和远端仓库并推送,在本地项目目录下

    git remote add origin ssh://username@ip(:port)/abspath_toproject
    git push origin master

随后在其他主机可以通过

    git clone ssh://username@ip(:port)/abspath_toproject
来拉取项目.

git clone 支持本机推送和拉取，如果是服务器本身已有项目，可以通过

    git remote add origin /abspath_toproject
    git push origin master

的方式来推送，
    
    git clone /abspath_toproject
的方式来拉取。