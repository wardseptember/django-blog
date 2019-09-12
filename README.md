[![](https://img.shields.io/badge/python-3.6.8-orange.svg)](https://www.python.org/downloads/release/python-368/)
[![](https://img.shields.io/badge/django-1.11-green.svg)](https://docs.djangoproject.com/en/1.11/releases/1.11/)
[![](https://img.shields.io/badge/bootstrap-4.1.3-blue.svg)](https://getbootstrap.com/docs/4.1/getting-started/introduction/)
[![](https://img.shields.io/badge/license-MIT-000000.svg)](https://opensource.org/licenses/MIT)
# 个人博客
基于python3.6.8、django1.11.12、Bootstrap4.1.3、JQuery3.0.0搭建的简洁优雅的个人博客。

博客效果： [http://wardseptember.top/](http://wardseptember.top/)

## 功能介绍
- Django 自带的后台管理系统，方便对于文章、用户及其他动态内容的管理
- 文章分类、标签、浏览量统计以及规范的 SEO 设置
- 用户认证系统，在 Django 自带的用户系统的基础上扩展 Oauth 认证，支持微博、Github 等第三方认证
- 文章评论系统，炫酷的输入框特效，支持 markdown 语法，二级评论结构和回复功能
- 信息提醒功能，登录和退出提醒，收到评论和回复提醒，信息管理
- 强大的全文搜索功能，只需要输入关键词就能展现全站与之关联的文章
- RSS 博客订阅功能及规范的 Sitemap 网站地图
- 实用的在线工具
- 友情链接和推荐工具网站的展示
- 缓存系统，遵循缓存原则，加速网站打开速度
- RESTful API 风格的 API 接口

## 网站支持
- 前端使用 Bootstrap4 + jQuery 支持响应式；图标使用 Font Awesome
- 后端 Python 3.6.8，Django 1.11.12，其他依赖查看源码中 requirements.txt
- 后台数据库使用 MySQL，缓存数据库使用 Redis
- 网站部署使用 Nginx + gunicorn，之前使用的 Nginx + uwsgi
- bootstrap-admin 用于美化后台管理系统，变成响应式界面
- django-allauth 等用于第三方用户登录
- django-haystack 和 jieba 用于支持全文搜索
- django-redis 缓存
- 使用 django restframework 支持的 RESTful 风格的 API 接口

## 博客页面效果（响应式）
- PC 页面效果

![pc](https://raw.githubusercontent.com/wardseptember/django-blog/master/readme_img/pc.jpg)

- ipad 效果

![ipad](https://raw.githubusercontent.com/wardseptember/django-blog/master/readme_img/ipad.jpg)

- 手机效果

![iphone](https://raw.githubusercontent.com/wardseptember/django-blog/master/readme_img/iphone.jpg)

## 运行指导
我的运行环境是centos-release-7-3.1611.el7.centos.x86_64
### 环境配置
#### 安装python3.6和虚拟环境
[安装python3.6和虚拟环境教程](http://www.wardseptember.top/article/3/)
#### 安装配置mysql5.7
[安装配置mysql5.7教程](http://www.wardseptember.top/article/1/)
- 创建数据库
```
mysql -u root -p
CREATE DATABASE `mysite` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
```
#### 安装配置redis
[安装配置redis教程](http://www.wardseptember.top/article/2/)
#### 开启端口
不管是在腾讯还是阿里买的服务器，都需要放开端口，设置安全组。
然后再在linux里面开启端口，一般开启80、3306、6349等端口，见[开启端口教程](http://www.wardseptember.top/article/4/)
### 下载项目
```
git clone https://github.com/wardseptember/django-blog.git
cd django-blog
```
更改`django-blog/izone/settings.py`配置信息，如mysql,redis等
### 运行
进入python虚拟环境，安装依赖。我这边代码是`source /root/blog/bin/activate`
```
cd /root/django-blog  # 进入项目
pip3 install -r requirements.txt -i http://mirrors.aliyun.com/pypi/simple  --trusted-host mirrors.aliyun.com
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py collectstatic
python manage.py runserver 0.0.0.0:8080
```
然后就可以在`http://server_domain_or_IP:8080`看到效果了
### 部署
[nginx+gunicorn部署教程](http://www.wardseptember.top/article/5/)
### BUG
可能因为django版本较低，会有一个报错。
```
yum install mlocate -y
updatedb
locate configparser.py  # 找到configparser.py所在路径
# 我的路径是/usr/lib64/python3.6/configparser.py，将configparser.py复制为ConfigParser.py
cp /usr/lib64/python3.6/configparser.py /usr/lib64/python3.6/ConfigParser.py
# bug解决
```
## 参考链接
本博客主要参考于[TendCode](https://github.com/Hopetree/izone)，在此基础上做了一点点改动，并增加了详细的运行指导。
本博客一些功能实现的方法，参考[https://github.com/stacklens/django_blog_tutorial](https://github.com/stacklens/django_blog_tutorial)
## 捐赠
打码不易，欢迎star，如果请我喝水就更棒了。
![donate](https://raw.githubusercontent.com/wardseptember/django-blog/master/readme_img/donate.jpg)