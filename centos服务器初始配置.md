# 服务器初始配置
```bash
# 添加用户
adduser shi
# 设置密码
passwd shi
# 可以使用root访问
gpasswd -a shi wheel
# 生成密钥对
ssh-keygen
# 下载docker
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
# 更新安装包
yum update
```
