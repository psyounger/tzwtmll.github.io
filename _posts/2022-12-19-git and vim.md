# git

## 常用

```js
git push --force //强制推送，慎用
git init 	//初始化
git clone 地址 // 克隆远程仓库
git status 	// 查看状态
git restore  // 回撤 commit 提交 ? 取消文件修改，变成初识状态
git add 文件名|. //添加到暂存区 .添加全部文件 
git checkout --file // 将缓存区中不需要的修改撤销
git stash // 隐藏文件，通常用于冲突时 或 提交到不同仓库时
git commit -m'提交注释的信息' // 提交到仓库
git commit -am'提交注释的信息'  // 如果文件已经放入，没有新文件，可以不用 add 和 commit 直接用 -am
git reset HEAD^xxxxxxx // 回撤到指定版本  
git diff // 查看变更 工作区与暂存去的差异对比
git log // 查看日志
git push // 提交
git config --global --unset https.proxy // 取消代理。需要在 git reomte rm origin 后操作
git config --global https.proxy xxx // 代理
git checkout 分支名 // 切换分支  
```

## 不常用

```js
git clone -d 分支名 地址 //  克隆分支仓库
git add -p 文件名  // 一个文件多次提交
git config --list // 获取配置信息
git blame 文件名 // 查看文件修改历史
git blame -L 100，10 文件名 // 从100 行开始到110行
git rm 文件名 //将该文件从commit后撤到 add 后，取消add提交的文件
git fetch  // 切换remote索引
```

## 分支操作

```js
git branch 新建分支名 // 新建分支
git branch  // 查看本地
git checkout 分支名 // 切换分支  
git branch -v // 查看分支以及提交hash值和commit信息
git merge 分支名	 // 把该分支的内容合并到现有分支上
git branch -d 分支名 // 删除分支
git branch -D 分支名 // 强制删除 若没有其他分支合并就删除 d会提示 D不会
```

### 远程分支

```js
git branch -r // 列出远程分支(远程所有分支名)
git branch -a // 查看远程分支
git psuh -u origin 分支名 // 提交到分支

```



# 文件操作

##  创建文件 touch 

```js
touch a //创建文件 a 
```

## 放入内容到文件 echo 

```js
echo 1234 >> a   //把1234这个内容放入 a 文件
如果不存在则直接创建文件再添加内容
```

## 打开文件	cat

```js
cat a  无法操作
```

## 删除文件 rm

```js
rm a
```



## 创建目录 mkdir

```js
mkdir test // 创建text文件
```



# 文件信息

```js
ls 						// 查看当前路径下的所以文件 ls
ls 文件夹名 		// 查看指定文件夹中的文件内容
ls -l 				//拉出最近git提交记录以及对应修改的文件名
ls -l -a 			// 拉出最近git提交记录以及对应修改的文件名，隐藏的文件也会显示
```

# cd 快速切换路径

```js
cd ~ 				// 将工作路径快速切换到 root
cd - 				// 将工作路径切换到上一个状态，而不是上一个目录
cd .. 			//返回上一个目录
cd 文件名		//进入对应文件名
cd /				//进入根目录
```



# vim 操作符

```js
vim 文件名 		// 新建一个文件
i							// 插入内容
按下 ese :wq   // 保存退出
按下 ese :q   // 直接退出
vi 文件名			// 打开文件
vim 模式下 文件中的#号开头的为注释
.project 忽略文件
*.obj 或者 *.exe 忽略一类文件 例如 .obj .exe 结尾的文件
```

# 命令模式

| hjkl        | 左下上右                 |
| ----------- | ------------------------ |
| gg          | 移动到文档首行           |
| G           | 移动到尾行               |
| ^或_        | 移动到行首第一个非空字符 |
| home键或者0 | 移动到行首第一个字符     |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |
|             |                          |



```





g_ 光标移动到行尾最后一个非空字符
end或者g 	光标移动到行尾最后一个字符
gm  光标移动到当前行中间处
b/B  光标向前移动一个单词（大写忽略/-等等特殊字符） 
w/W   光标向后移动一个单词（大写忽略/-等等特殊字符）
e/E    移到单词结尾（大写忽略/-等等特殊字符）
ctrl+b或pageUp键  翻屏操作，向上翻
ctrl+f或pageDn键  翻屏操作，向下翻
```



# 修改host 

```
sudo vi /etc/hosts
192.168.31.100 wapi.geelevel.com  // 支付一分
home=> waip 线下设备
```





