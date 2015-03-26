# Git一般流程

##创建新项目（以[Git@OSC](http://git.oschina.net/)为例）
1. 设置用户基本信息
    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your@email.com"
    ```
这些配置都会存放在用户所在目录下的`.gitconfig`文件中, 用户可使用文本编辑软件进行修改查看。

2. 建立自己的工程（也就是工作目录），比如一个`HelloWorld`工程。
3. 我们现切换到这个目录下，即`HelloWorld`目录下，运行
    ```bash
    git init
    ```
    这个命令会在需要使用Git管理的目录下生成一个`.git`的隐藏目录，这说明该目录可以使用Git进行管理了。

4. 输入
    ```bash
    git add .
    ```
    把该目录下的所有文件全部提交到缓冲区。

5. 使用
    ```bash
    git commit -m "Git HelloWorld first commit"
    ```
    将代码提交到`HEAD`，注意此时还没有提交到服务器.

6. 建立远程仓库

    * 6.1 生成ssh密匙
    ```bash
    ssh-keygen -t rsa -C "youremail@xxx.com"
    ```
    一路回车,这个会在当前用户文件夹下，生成`.ssh`文件夹，里边有个 `id_rsa.pub`文件，用记事本打开，复制其中的全部内容。

    * 6.2 打开 <http://git.oschina.net/keys>页面，在该页面中添加公钥，标题可以随便填,公钥就是刚才复制过的内容,然后保存即可。

    * 6.3 添加一个新项目, 比如 `HelloWorld`，这个名称后面会用到,这个步骤是必须的。

    * 6.4 测试下与远程代码仓库是否联通, 输入命令：
    ```bash
    ssh -T git@git.oschina.net
    ```
    然后会通知你输入用户名/密码，该密码就是你的osc账户密码，然后会提示你输入yes/no，输入yes后回车，显示出`Welcome to Git@OSC, xxx!`，说明连接成功。

    * 6.5 下面就可以提交项目到git仓库中了。
    ```bash
    git remote add origin http://git.oschina.net/XXX/HelloWolrd.git

    git push origin master
    ```
    如果远程仓库初始化的过程中建立了初始化READE.MD文件，则直接推送本地仓库到远程仓库会出错，应通过以下步骤进行解决：
    ```bash
    git remote add origin http://git.oschina.net/XXX/HelloWolrd.git

    git pull origin master

    git push origin master
    ```
    * 6.6 以后的操作就是 `本地修改 -> add -> commit -> push`

## 参与已有项目
1. 在GitHub上fork已有项目作为自己的仓库，如`fw1121/snp-pipeline`，然后`git clone`到本地，并设置用户信息。

    ```
    $ git clone git@github.com:your_github_username/snp-pipeline.git
    $ cd snp-pipeline
    $ git config user.name "Your Name"
    $ git config user.email "your@email.com"
    ```

2. 修改内容后提交，并`git push`到之前`fork`的仓库。

    ```
    $ git commit -am "Fix issue #1: change typo: helo to hello"

    $ git push
    ```

3. 在GitHub网站上提交`pull request`。

4. 定期使用项目仓库内容更新自己仓库内容。

    ```
    $ git remote add upstream https://github.com/fw1121/snp-pipeline.git
    $ git fetch upstream
    $ git checkout master        //切换到master支上，准备进行合并
    $ git merge upstream/master  //合并
    $ git push origin master     //推送到自己的远程仓库
    ```
