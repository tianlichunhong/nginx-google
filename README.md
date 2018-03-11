# Nginx-Google
## 项目说明

这是一个通过Nginx反代google的一键安装脚本。脚本来源https://github.com/arnofeng/ngx_google_deployment
由于原作者很久没有更新了。所以克隆过来，设置安装最新的Nginx版本。脚本运行后，要求输入一个你自己站点的域名（原作者设置输入2个，嫌麻烦就修改了）。如果没有域名也可以随便输入，安装完成后，修改/etc/nginx/nginx.conf 就可以。
* * *
## 安装方法：
```bash
wget -N --no-check-certificate https://raw.githubusercontent.com/tianlichunhong/nginx-google/master/install.sh
chmod 771 ./install.sh
bash ./install.sh
```
然后选择1（debain 系统），并输入你的域名
按任意键继续
一直到出现"Everything seems OK!Go ahead to see your google!"，就代表成功了
* * *
## 使用
脚本已经配置好自启动设置。Nginx的启动、重启、停止命令：

安装目录位于 /etc/nginx

配置文件为 /etc/nginx/nginx.conf

启动命令:/etc/nginx/sbin/nginx 

停止命令:/etc/nginx/sbin/nginx -s stop
 
重启命令:/etc/nginx/sbin/nginx -s reload

在浏览器中打开http://你的域名，就可以正常使用谷歌了。也可以通过nginx.conf的配置实现对其他网站的反代。

## SSL配置
建议采用SSL，否则国内用户可能打不开。GFW对http://可能有过滤。

设置SSL方法：
编辑/etc/nginx/nginx.conf 中证书的路径：

        ssl                  on;
		
        ssl_certificate      /etc/letsencrypt/live/g.adminhost.org/fullchain.pem;
		
        ssl_certificate_key  /etc/letsencrypt/live/g.adminhost.org/privkey.pem;
		
证书获取方法，请参考https://certbot.eff.org/#debianwheezy-nginx


