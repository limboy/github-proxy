### 这是什么

作为一个序员，经常会显式/隐式地执行 `git clone git@github.com:author/repo.git`，但因为某些原因，这个操作会执行很长的时间，然后生活就不再美好了。

这个脚本要解决的就是 clone github repo 过慢的问题。

### 实现原理

在执行 `git clone git@github.com:author/repo.git` 命令时，将 `git@github.com:` 重定向到此脚本，然后这里会判断是否已经 clone 过该 repo，如果是的话，直接返回，不然就去 github 获取一下，然后存到本地。

### 使用方法

服务端需要安装 nodejs，然后执行 `./github-proxy /location/you/want/to/store/repos`

客户端执行 `git config --global url."http://your-host:port/".insteadOf "git@github.com:"`，执行完后，会在 ~/.gitconfig 里多了这么两行

```
[url "http://your-host:port/"]
	insteadOf = git@github.com:
```

That's it!

### TODO

* 定时更新 clone 下来的 repos
* 后台运行

### 感谢

[@yegle](https://twitter.com/yegle)
