
# 说明
- 本项目无法适用于 2018 年前开发的小程序(如最后更新时间为 2017.7.12), 请过早的小程序不用再尝试了
- 本项目完全基于 [wxappUnpacker](https://github.com/qwerty472123/wxappUnpacker "wxappUnpacker") 改进的。

下载 nodejs https://nodejs.org/en/ 到linux服务器 解压配置环境
vim /etc/profile 添加 /xxx/为解压包绝对路径
export NODE_HOME=/xxx/node-v12.16.3-linux-x64
export PATH=$PATH:$NODE_HOME/bin 
export NODE_PATH=$NODE_HOME/lib/node_modules
退出vim
//使环境生效
source /etc/profile
cd 到拉去代码的根目录 下面有 wuConfig.js  wuJs.js  wuLib.js  wuRestoreZ.js  wuWxapkg.js  wuWxml.js  wuWxss.js
然后 npm install
然后就可以解包了

# 分包功能

当检测到 wxapkg 为子包时, 添加-s 参数指定主包源码路径即可自动将子包的 wxss,wxml,js 解析到主包的对应位置下. 完整流程大致如下: 
1. 获取主包和若干子包
2. 解包主包 `./bingo.sh testpkg/master-xxx.wxapkg`
3. 解包子包 `./bingo.sh testpkg/sub-1-xxx.wxapkg -s=../master-xxx`

TIP
> -s 参数可为相对路径或绝对路径, 推荐使用绝对路径, 因为相对路径的起点不是当前目录 而是子包解包后的目录

```
├── testpkg
│   ├── sub-1-xxx.wxapkg #被解析子包
│   └── sub-1-xxx               #相对路径的起点
│       ├── app-service.js
│   ├── master-xxx.wxapkg
│   └── master-xxx             # ../master-xxx 就是这个目录
│       ├── app.json
```





