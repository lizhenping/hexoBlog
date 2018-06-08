# hexoBlog
此项目源码为lizhenping.github.io博客的源码
基于hexo+githubPages搭建而成,若想访问前端界面,可以通过 http://lizhenping.github.io  进行访问.

## 20180608 Hexo统计阅读次数
http://www.icafebolger.com/hexo/hexopostcount.html  
https://www.cnblogs.com/stringfade/p/7738072.html  
注意点: 必须在leancloud安全中心,web安全域名设置两个安全域名,一个是正式环境域名,一个是调试的域名,不然会报错~
ps: 在本地的话,阅读次数始终是0,查看console,发现请求403;  
    部署到github上,阅读次数有变化,但是感觉数量不太对呢; 待我想明白了,再更新此blog.
开发暂未完成,等后期再调试~

###  特殊说明
关于20180605-vuecli.md中需要用到的图片,需要放在本地的nginx目录下哦.
然后将img文件夹拷贝过去,修改ip即可以访问.