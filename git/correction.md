##常见错误处理
- **push本地代码到github出错**

**错误提示**
```bash
$ git push -u origin master
To git@github.com:******/Demo.git
 ! [rejected] master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:******/Demo.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
hint: before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
<br/>
**错误原因:**

远程repository和本地的repository冲突导致

<br/>
**解决方法**

1. 使用强制push的方法：
```bash
$ git push -u origin master -f
```
这样会使远程修改丢失，一般是不可取的，尤其是多人协作开发的时候。

2. push前先将远程repository修改pull下来

    ```bash
    $ git pull origin master

    $ git push -u origin master
    ```

3. 若不想merge远程和本地修改，可以先创建新的分支：
    ```bash
    $ git branch [name]

    然后pull

    $ git pull -u origin [name]
    ```

------------
- push本地代码到github出错
