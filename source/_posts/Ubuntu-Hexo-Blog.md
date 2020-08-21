---
title: Ubuntu 搭建 Hexo 博客(butterfly 主题)
date: 2020-07-24 16:42:27
tags: Blog
cover:  "/img/c5.jpg"

mathjax: true
---

环境 Ubuntu 18.04

## 安装nodejs以及npm

``` bash
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
```
安装完成 提示你用以下代码安装 nodejs 和 npm

```bash
sudo apt-get install -y nodejs
```
查看 nodejs 以及 npm 版本

```bash
nodejs --version
npm --version
```
这种比ubuntu软件源的要新,也可以google一下其他安装方式,选择适合自己的安装方法


## hexo 本地博客创建及预览

安装hexo
```bash
npm install -g hexo-cli
```
创建本地博客文件夹并初始化,安装组件
```bash
mkdir your_blog
cd your_blog
hexo init
npm install
```
生成网站并启动本地服务器进行预览
```bash
hexo g
hexo s
```
访问 http://127.0.0.1:4000/, 出现 hexo 的默认界面

{% asset_img hexo.png [title] %}


恭喜你,本地博客初步完成!
如果4000端口被占用,可以使用
```bash
hexo server -p 5000
```
更换端口为 5000 进行预览


## 部署到 Github Pages

### 注册 github 并设置 ssh key

如果你没有github 可以先去注册一下, 注册完成后终端运行
```bash
git config --global user.name "your_github_name"
git config --global user.email "your_github_email"
```
设置你的github用户名和邮箱
之后使用你的邮箱创建ssh key

```bash
ssh-keygen -t rsa -C "your_github_email"
```
默认回车就好
根据提示的存放ssh key的地址, 你可以找到 id_rsa.pub 公钥文件
将文件中的内容复制
登陆 GitHub ，进入 Settings 页面，选择左边栏的 SSH and GPG keys，点击 New SSH key
把你复制的公钥粘贴到 Key 下面的框里 点击 Add SSH key 完成添加

终端输入
```bash
ssh -T git@github.com
```
出现"Are you sure...", 输入yes 确认, 出现

"Hi your_github_name! You've successfully authenticated, but GitHub does not provide shell access."

证明你已经连接成功了!

### 创建 github 仓库,开启Github Pages

创建一个新仓库

{% asset_img new_repo.png [newrepo] %}

进入你仓库的Setting界面(不是你头像下拉栏的Setting!) 往下翻到Github Pages 界面

{% asset_img githubpages.png [] %}

点击master branch开启Github Pages

分配的博客地址为
https://your_github_name.github.io/your_site_name.github.io

如果你的github仓库名(也就是你存放博客的地方)与你的github账户名一致 那么你的地址会简洁很多:
https://your_site_name.github.io

不过我的github的账户名已经用于创建另一个仓库了, 所以就只能用第一种
更改域名可以参考网上的其他教程 这里就不再说了



### 配置本地 hexo github deploy

安装 hexo-deployer-git
```bash
npm install hexo-deployer-git --save

```
修改_config.yml文件 在末尾修改deploy
```bash
deploy:
  type: git
  repo: git@github.com:your_github_name/your_site_name.github.io.git
  branch: master
```
保存修改并运行```hexo d``` 将网站上传到GitHub Pages
访问域名 https://your_github_name.github.io/your_site_name.github.io (github 用户名不同于仓库名) 或
https://your_site_name.github.io(github 用户名与仓库名相同)
即可看到你的 你的博客!!!

然而你会发现 博客完全不是你想的样子 直接变成了文字版

这是因为没有配置_config.yml 编辑_config.yml 发现URL这块需要设置你的博客地址
并且如果你是像我一样github用户名跟博客仓库名不同的话 需要将root 设置为 /your_site_name.github.io/

```bash
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://your_github_name.github.io/your_site_name.github.io/
root: /your_site_name.github.io/
```
运行 ```hexo g -d``` 重新生成博客并部署 应该就可以了

## butterfly 主题配置

### 官方文档网站
https://demo.jerryc.me/
大多数问题可以在上面找到 以下的配置也可以在官网找到

默认的主题是landscape 我不是很喜欢 所以用了butterfly主题

### 安装以及配置
在博客根目录下
```bash
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```
在_config.yml中更改主题
```bash
theme: butterfly
```
安装渲染器
```bash
npm install hexo-renderer-pug hexo-renderer-stylus --save
```
主要注意的点是要把主题的配置文件_config.yml 复制到博客根目录的source中的_data目录下
 (如果不存在就自己创建一个)并将文件名改为 butterfly.yml 之后有关主题的配置都会在这个文件中修改

运行 ```hexo g -d``` 你应该可以看到更换了主题的博客了
{% asset_img butterfly.png [] %}


### 更换主页图片
在butterfly source的 img 中添加图片 your_image 并在
butterfly.yml 中设置 index_img
```bash
 index_img: /img/your_image
  ```

## 配置 gitalk 评论区

### 开启gitalk

登陆 GitHub ，进入 Settings 页面，选择左边栏的Developoer settings，点击 OAuth Apps 点击 New OAuth App
Homepage URL 和 Authorization callback URL 填主页地址 其他随便填 点击 Register application 完成

{% asset_img gitalk.png [] %}

需要把Client ID 和Client Secret 填写到butterfly.yml gitalk配置的相应位置


### 配置评论区的注意事项

在butterfly.yml中设置
```bash
# gitalk
# https://github.com/gitalk/gitalk
gitalk:
  enable: true
  client_id: your_client_id
  client_secret: your_client_secret
  repo: your_site_name.github.io
  owner:your_github_name
  admin: your_github_name
  language: zh-CN # en, zh-CN, zh-TW, es-ES, fr, ru
  perPage: 10 # Pagination size, with maximum 100.
  distractionFreeMode: false # Facebook-like distraction free mode.
  pagerDirection: last # Comment sorting direction, available values are last and first.
  createIssueManually: false # Gitalk will create a corresponding github issue for your every single page automatically
  count: false # dispaly comment count in top_img
```

yml文件里的repo需要填 仓库名而不是地址!!!!


## 修正Mathjax与默认渲染器冲突的问题

先卸载原来的渲染器, 安装新的渲染器

```bash
npm uninstall hexo-renderer-marked --save
npm install hexo-renderer-kramed --save

```
并在文件```node_modules\kramed\lib\rules\inline.js```中修改
```
//escape: /^\\([\\`*{}\[\]()#$+\-.!_>])/,      第11行，将其修改为
escape: /^\\([`*\[\]()#$+\-.!_>])/,
//em: /^\b_((?:__|[\s\S])+?)_\b|^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,    第20行，将其修改为
em: /^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
```


### 好了, 博客搭建到此结束,如果你还有更多问题,可以去google问一下哈哈哈.
