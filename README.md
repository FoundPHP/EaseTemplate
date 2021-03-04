# Ease Template

手册地址：https://foundphp.com/?m=manual&id=1740

　　Ease Template（简称：ET） 本是为了解决项目编译效率过慢问题而研发出来的，为了匹配各种语种项目，又研发了多语言解析功能；Ease Template 模板引擎于 2005 年正式发布，目前Ease Template 支持PHP5\PHP7\PHP8等多达12个版本。
  
　　PHP模板技术的核心是用最小成本和最高效率将html代码和程序分离：前端工程师将页面制作为htm文件，在制作中将(如数据库输出，用户交互等)变量放在模板文件中对应的位置，由PHP程序载入该模板文件后将模板中定义的变量进行替换，最终输出动态内容提供用户浏览。
   
　　在最小的代码量实现了：变量、路径解析、逻辑判断、循环处理、嵌套循环、特殊循环、弥补函数、连载执行、模版引用、引用PHP、多语言、多风格、调试平台、文件读写、CURL、缓存管理、半静态页面、静态网站、路由模式。


实例化代码：   
```php
<?php   
//引入Ease Template最新版本template.ease.php，旧版本引入template.php   
include "template/ease_template.php";
//Ease Template 设置   
$config['tpl']['ID']             = '1';                       //样式id
$config['tpl']['Style']         = 'default';                  //样式地址
$config['tpl']['CacheDir']        = 'cache';                  //缓存目录
$config['tpl']['HtmDir']         = 'data/html';               //静态化目录
$config['tpl']['TemplateDir']    = 'view';                    //模板目录
$config['tpl']['LangDir']        = 'language';                //语言包目录
$config['tpl']['AutoImage']        = 1;                       //自动解析照片
$config['tpl']['Compress']        = 0;                        //压缩代码
$config['tpl']['Rewrite']        = 0;                         //重写地址
$config['tpl']['Copyright']        = 0;                       //版权保护
$config['tpl']['Language']         = 'zh';                    //语言
//声明Ease Template   
$tpl    = new FoundPHP_template();
//对模板赋值
$et = 'Ease tempate';
//载入模板template/home.htm
$tpl->set_tpl('home');
//打印模板
$tpl->p();
?>
```

配置讲解：

ID 缓存id
当你的网站拥有多个风格的时候在cache模式下,需要对应风格id，黑色1，紫色2，绿色3，这样缓存文件会自动对应自己的id，不会出现界面颜色错乱

TplType 模板格式
每个人开发习惯不同，当用惯了smarty或是phplib就会习惯用index.tpl这样的后缀模板，而ET默认的格式是就是htm

CacheDir 缓存目录（编译引擎）
ET默认为程序目录下cache目录，如目录没有写入权限就自动转为替换引擎，不会因为权限问题造成程序错误

TemplateDir 视图目录
ET默认为当前程序目录下template目录

AutoImage 自动解析图片
1表示开放 0表示关闭，模板中存在有images的时候将自动替换，例如default.htm 中＜img src=”images/logo.gif”＞ 执行时ET会自动将图片的地址解析为：＜img src=”template/images/logo.gif”＞

LangDir 语言包目录
ET会自动收集语言到这个目录下建立语言包

Language 默认语言
，由于用户需要个性设置，可以设置默认的文件为cn，产生的文件就为cn.php，默认为default.php

Copyright 版权保护开关
1表示开放 0表示关闭，开发环境为编译模式的时候才生效，当程序全部执行完成后就生成了受版权保护代码，没有template目录也可以执行，只要不提供template时即可实现开源版权保护

MemCache Memcache设置
当您有Memcache服务器的时候，输入服务器地址例如（如:127.0.0.1:11211），就可以开启高效快速的Memcache引擎

Compress 压缩代码
1表示开放 0表示关闭，自动将输出到浏览器页面的内容代码压缩，移除换行与多余的空格减少网络流量

HtmDir 静态化地址
输出静态网站的输出目录

Rewrite 重写地址
1表示开放 0表示关闭，开启后自动将缓存静态也的连接对应班静态化或静态化地址
