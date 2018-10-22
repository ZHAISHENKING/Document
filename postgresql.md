# redis和postgres安装

### redis

```bash
# 安装
apt-get install redis-server
```

打开配置文件. `/etc/redis/redis.conf`，将daemonize属性改为yes（表明需要在后台运行）

后台启动

```bash
redis-server /erc/redis/redis.conf
```

运行`redis-cli`查看是否配置成功

<center><img src="http://qiniu.s001.xin/phoww.jpg" width=600></center>



### postgresql

```bash
apt-get install postgresql
```

启动

```bash
/etc/init.d/postgresql start
```



查看库`\l`

<center>
    <img src="http://qiniu.s001.xin/w1c6g.jpg" width="600">
</center>

切换表 `\c tablename`

<center><img src="http://qiniu.s001.xin/4duv4.jpg" width=600></center>

查看表 `\dt`

查看用户 `\du`

修改数据库用户密码

`ALTER USER postgres WITH PASSWORD 'password';`

退出 `\q`

