**如何发布一个npm包？**

这个问题困扰了我很久，倒不如说是懒得要死，一直不肯花时间去查。今天破天荒看了下，竟是如此简单。其实难的是你发布了一个包有大量的人来用，就跟你git仓库被**人star了一样。

>开始之前先到[npm官网](https://www.npmjs.com/)，注册一个npm账号，到时后发布会用到。
需要注意，npm包不能重名，起好名字之后最好本地`npm install`一下，如果能安装成功，说明你这名字有人用过啦。

正式开始：

（1）首先在你仓库里执行 `npm init`，这个就不细说了，填上所需字段，最好在你的github上建一个仓库写到package里的git仓库。

（2）然后执行`npm adduser && npm login`,按照你注册的npm账号-邮箱-密码，填一下。最后会提示你

```
Logged in as western-ranger on https://registry.npmjs.org/.
```

western-ranger是我npm账号的名字

（3）执行`npm publish`，顺利的话会输出命令 `+ readcurpwd@1.0.0` (readcurpwd是我起的包名)，但是天有不测风云，你可能遇到这样的问题：

```
npm ERR! publish Failed PUT 403
npm ERR! Darwin 16.5.0
npm ERR! argv "/usr/local/bin/node" "/usr/local/bin/npm" "publish"
npm ERR! node v7.4.0
npm ERR! npm  v4.2.0
npm ERR! code E403

npm ERR! no_perms Private mode enable, only admin can publish this module: readcurpwd
npm ERR!
npm ERR! If you need help, you may report this error at:
npm ERR!     <https://github.com/npm/npm/issues>

npm ERR! Please include the following file with any support request:
npm ERR!     /Users/WesternRanger/atomProjects/fightting/readcurpwd/npm-debug.log
```

百度||谷歌关键字 -- “no_perms Private mode enable”，你会得到答案 - npm registry指向了其他三方的仓库了。我的就是指向了taobao的npm仓库了。

（4）搞定了之后验证下，npm install <your-package>，或者从你的[npmjs主页](https://www.npmjs.com/)上，查看你名下的npm包。如果要修改包内容发布新版本，手动改package.json里的version就行。然后执行`npm publish`。
