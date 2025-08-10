# PAPAYA 的 Git 教學

## 新學到的 Git 指令

### ```git add *.<file extension>```
除了所有檔案的 ```git add .``` 以外，也可以使用萬用字元。

### ```git log --oneline```
這指令在 VS Code 中的 Terminal 很好用，可以看到所有的 log 以及資訊不會太雜。  

### ```git diff <SHA1> -- <filename>```
這個指令可以比較某檔案在當前工作目錄與之前指定提交 ```<SHA1>``` 的差異，這裡提交的意思是做完新增、修改、刪除並提交後的結果，此外，要注意 ```--``` 前後是有空格的。  
**補充：** 
- 這裡的 SHA1 就是每次 commit 的 ID。  
- ```--``` 只是分隔符，告訴 Git 後面都是路徑（避免把檔名誤判成分支或參數）。
- 如果輸入 ```git diff <SHA1> HEAD -- <filename>``` 的話，是比較 ```<SHA1>``` 那次提交和 ```HEAD```（目前分支的最新提交）中該檔案的差異。
- ```git diff <SHA1> -- <filename>```（不帶 ```HEAD```）才是拿「目前工作目錄」去對比 ```<SHA1>``` 的版本。

### ```git checkout <SHA1> -- <filename>```
除了 ```--``` 前後空格要注意以外，這裡不是像 ```git checkout <branchname>``` 或 ```git reset --hard <branchname>``` 那樣切換分支，是把 ```<SHA1>``` 版本的檔案取出來，覆蓋暫存區（Index） + 工作目錄，不移動 ```HEAD``` ，因此，如果確定要之前的版本，需要再使用 ```git add .``` 以及 ```git commit -m <message>```。  
**補充：** 
- 不移動 ```HEAD``` !
- ```<SHA1>``` 可以互換 ```<branchname>```。
- 無論是用 ```<SHA1>``` 或是 ```HEAD``` 都會覆蓋工作目錄和暫存區。  
- ```git checkout -- <filename>``` 只會覆蓋工作目錄，這等價 ```git restore <filename>```。

### ```git clone```
複製 GitHub 上的 repo 時，複製下來的結果會用資料夾包著，因此，還會需要用 ```cd``` 進入此資料夾。

### ```git branch```
列出本機所有分支，前面帶 * 的就是目前所在分支。

### ```git checkout -b <branchname>```
建立並切換到新分支。  
**補充：** 
- 以下 ```switch``` 指令是 Git 2.23 之後推出的更明確指令 ```git switch``` 預設接受『分支名』；若要切到某個 commit，需用 ```--detach <SHA1>```（進入 detached HEAD），例如：```git switch --detach <SHA1>``` 等效於 ```git checkout <SHA1>```。
- ```git switch <branchname>``` 等價 ```git checkout <branchname>```。
- ```git switch -c <branchname>``` 等價 ```git checkout -b <branchname>```，```-c``` 為 ```--create```。