# 常用GIt指令

## 1.从0开始使用Git

1. **安装 Git：** 如果你还没有安装 Git，首先需要在你的计算机上安装 Git。你可以从 [Git 官方网站](https://git-scm.com/) 下载并按照说明进行安装。
   
2. **设置用户信息：** 在安装完 Git 后，你需要配置一些基本的用户信息，如用户名和邮箱，这些信息将会出现在你的提交记录中。在命令行中运行以下命令，将其中的 `"Your Name"` 和 `"your.email@example.com"` 替换为你的实际信息。
   
    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    ```
    
3. **创建一个新的 Git 仓库：** 如果你已经有一个项目，可以直接进入项目目录并执行 `git init` 来初始化一个新的 Git 仓库。如果你想从头开始创建一个新的项目，可以先创建一个新的文件夹，进入文件夹后执行 `git init`。
   
    ```bash
    mkdir my_project
    cd my_project
    git init//在现有目录中初始化一个仓库，将会创建一个.git文件
    ```
    
4. **进行第一次提交：** 现在你的仓库已经初始化，你可以开始添加文件并进行第一次提交。以下是一个例子：
   
    ```bash
    # Linux下创建一个新文件
    touch README.md  
    
    # 将文件添加到暂存区
    git add README.md
    
    # 提交到本地git仓库，追加消息"Initial commit"
    git commit -m "Initial commit"
    ```
    
5. **关联远程仓库（可选）：** 如果你计划将项目上传到 GitHub 或其他远程仓库，你需要将本地仓库与远程仓库关联。首先，在 GitHub 上创建一个新的仓库，然后按照 GitHub 提供的指南将远程仓库关联到本地仓库。
   
    ```bash
    # 添加远程仓库
    git remote add origin [远程仓库URL]//
    
    # 推送到远程仓库
    git push -u origin master
    ```
    

![image-20231116203236870](C:\Users\乾乾\AppData\Roaming\Typora\typora-user-images\image-20231116203236870.png)

### 基本概念：

* **工作区（Working Directory）：** 你实际工作的目录，包含你的项目文件。
  
* **暂存区（Staging Area）：** 一个临时区域，用于存储你想要提交的更改。
  
* **本地仓库（Local Repository）：** 包含你项目的所有版本历史的数据库。
  
* **远程仓库（Remote Repository）：** 存储在网络上的仓库，比如 GitHub。
  
* **分支（Branch）：** 用于独立开发特性或修复 bug，不影响主分支（通常是 `master`）。
  
* **提交（Commit）：** 一个保存更改的快照，每个提交都有一个唯一的标识符。



## 2.从Github上clone一个项目

1. **获取项目的URL：** 在 GitHub 上找到你想要克隆的项目，并复制项目的 URL。URL 通常以 `https` 或 `git` 协议开头。
   
2. **打开命令行终端：** 打开一个命令行终端（例如，使用命令提示符（Command Prompt）或终端（Terminal））。

3. **选择克隆位置：** 使用 `cd` 命令切换到你想要将项目克隆到的本地目录。例如：

    ```bash
    cd C:\Users\乾乾\Desktop\Web第二次授课
    ```

4. **执行克隆命令：** 使用 `git clone` 命令，将项目克隆到本地。将 `[项目URL]` 替换为你复制的项目 URL。

    ```bash
    git clone [项目URL]
    ```

    例如，如果项目 URL 是 `https://github.com/example/repository.git`，则克隆命令为：

    ```bash
    git clone clone https://github.com/HDU-HelloWorld/HelloWorld.git
    ```

    

5. **输入凭据（如果需要）：** 如果你使用的是 HTTPS URL，可能会要求输入 GitHub 的用户名和密码，或者是个人访问令牌（Personal Access Token）。

6. **等待克隆完成：** Git 将下载项目的所有文件，并将它们保存在你选择的本地目录中。

7. **进入项目目录：** 使用 `cd` 命令进入克隆下来的项目目录。

    ```bash
    cd HelloWorld
    ```


## 3.关联远程仓库

当你关联远程仓库并进行推送（`git push`）时，如果使用的是 HTTPS URL，可能需要提供验证信息（用户名和密码或个人访问令牌）。这样可以确保只有经过授权的用户能够与远程仓库进行交互。

### 使用用户名和密码：

如果使用的是用户名和密码进行验证，Git 在推送时会要求你输入用户名和密码。以下是一些步骤：

1. **使用 HTTPS URL 关联远程仓库：**
   
    ```bash
    git remote add origin https://username@github.com/username/repository.git
    ```
    
    替换 `username` 为你的 GitHub 用户名，`repository` 为你的仓库名称。
    
2. **推送到远程仓库：**
   
    ```bash
    git push -u origin master
    ```
    
    在这一步，Git 会提示你输入用户名和密码。
    

### 使用个人访问令牌：

如果你使用的是个人访问令牌，可以在 GitHub 或其他托管服务上生成令牌，然后在推送时使用该令牌进行验证。以下是一些步骤：

1. **生成个人访问令牌：**
   
    * 在 GitHub 上，进入 Settings -> Developer settings -> Personal access tokens。
    * 生成一个新的访问令牌，选择适当的权限（至少需要 repo 权限）。
2. **使用个人访问令牌关联远程仓库：**
   
    ```bash
    git remote add origin https://<个人访问令牌>@github.com/username/repository.git
    ```
    
    替换 `<个人访问令牌>` 为你生成的个人访问令牌。
    
3. **推送到远程仓库：**
   
    ```bash
    git push -u origin master
    ```
    
    在这一步，Git 会使用你提供的个人访问令牌进行验证。
    

使用个人访问令牌相对更安全，因为它可以提供受限的访问权限，而不需要暴露你的密码。请注意令牌是敏感信息，不应该轻易泄露。

