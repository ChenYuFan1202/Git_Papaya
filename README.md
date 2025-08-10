# PAPAYA 的 Git 教學

## 新學到的 Git 指令

### ```git add *.<file extension>```
除了所有檔案的 ```git add .``` 以外，也可以使用萬用字元。

### ```git log --oneline```
這指令在 VS Code 中的 Terminal 很好用，可以看到所有的 log 以及資訊不會太雜。  

### ```git diff SHA1 -- <filename>```
這個指令可以比較某檔案在當前 commit 與之前 commit 的差異，這裡 commit 的意思是做完新增、修改、刪除並提交後的結果，此外，要注意 ```--``` 前後是有空格的。  
**補充：** 
- 這裡的 SHA1 就是每次 commit 的 ID。  
- ```--``` 只是分隔符，告訴 Git 後面都是路徑（避免把檔名誤判成分支或參數）。

### ```git checkout SHA1 -- <filename>```
除了 ```--``` 前後空格要注意以外，這裡不是像 ```git checkout <branchname>``` 或 ```git reset --hard <branchname>``` 那樣切換分支，是把特定 commit 中的特定檔案取出來到 ``` HEAD``` 的暫存區和工作目錄 ，因此，如果確定要之前的版本，需要再使用 ```git add .``` 以及 ```git commit -m <message>```。  
**補充：** 
- 不移動 ```HEAD``` !
- ```SHA1``` 可以互換 ```<branchname>```。
- 無論是用 ```SHA1``` 或是 ```HEAD``` 都會覆蓋工作目錄和暫存區。  
- ```git checkout -- <filename>``` 只會覆蓋工作目錄，這等價 ```git restore <filename>```。

### git clone
複製 GitHub 上的 repo 時，複製下來的結果會用資料夾包著，因此，還會需要用 cd 進入此資料夾。