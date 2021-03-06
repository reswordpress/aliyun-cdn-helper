# 阿里云 CDN 辅助插件 (Aliyun CDN Helper For WordPress)

本插件为 WordPress 的管理页面的工具栏添加快捷按钮，方便站长在修改完静态资源后能快速刷新 CDN 缓存。

### 当前版本

v2.2

![image][image-1]

### 插件特色

1. 一键刷新缓存
2. 配置简单
3. 设置页面可以显示当日的刷新剩余量
4. 中英文支持
5. 支持文件刷新和目录刷新
6. 支持批量预热文件

### 环境

WordPress 4.9.5 （低版本暂未测试，理论上是支持的）

PHP 5.3 ~ 7.1 （取决于阿里云 SDK）

### 插件的使用
#### 下载
[Latest Release][1]

#### 安装

插件已提交到 WordPress 插件商店，正在等待审核，在此之前，您需要使用以下的安装方法：

将压缩包解压，上传到 `/wp-content/plugins/` 或通过 WordPress 插件管理页面上传插件压缩包来安装

#### 配置

1. 启动插件
2. 进入 `设置->阿里云 CDN` 完成设置后即可使用

### 配置的相关说明
#### 刷新文件类型:

这个是对快捷按钮的设置，如果选择 `刷新当前主题目录内的静态文件（目录）` 或 `全站刷新（目录）` 则请求强制回源拉取更新的目录（使用一个刷新目录配额）。

#### URL 预热

预热可以将源站的内容主动预热到 L2 Cache 节点上，用户首次访问可直接命中缓存，缓解源站压力，

如果您是首次使用 CDN 和这个插件，您可以点击预热按钮，插件将会自动搜索当前主题目录类的静态资源文件，处理成标准的 URL 格式后提交到预热接口。

由于阿里云的 SDK 不支持批量刷新，所以现在使用循环提交的方式，主题内文件较多的话等待时间可能稍微长一点，具体使用 URL 配额由文件数量决定。

v2.2 版本更新：

1. 修复了一些小问题

2. 阿里云 SDK 已支持批量刷新，但貌似会提示文件名称格式不正确的问题，所以仍使用循环提交的方式，并做了一些小调整，只提交后缀为 `css, js` 的文件（下个版本会增加自定义后缀的功能），如果您有好的方案，欢迎提交 Pull Request

3. 为了提交到 WordPress 已将插件名更名为 `Jacky AliCDN Helper`。（求 dalao 给它取个更好听的名字w）

#### 刷新自定义 URL

功能如题所示，对应阿里云 CDN 控制台的 URL 刷新，如果强行要输入目录的话不要忘记末尾的 `/`。

容错机制暂未完善，一旦出现异常将立即返回错误，如果刷新错误请检查每一行的 URL 书写是否规范。


### 支持
如果您喜欢这个插件，欢迎捐助我~

![image][image-2]


[1]:	https://github.com/0xJacky/jacky-alicdn-helper/releases/latest

[image-1]:	https://github.com/0xJacky/aliyun-cdn-helper/raw/master/assets/screenshot-1.png
[image-2]:  https://github.com/0xJacky/aliyun-cdn-helper/raw/master/assets/my_alipay.png
