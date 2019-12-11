## 1. 拉去镜像
docker pull gitlab/gitlab-ce
## 2. 创建挂载目录
mkdir -p /home/gitlab/config
mkdir -p /home/gitlab/logs
mkdir -p /home/gitlab/data
## 3. 运行镜像
docker run -d  -p 443:443 -p 9999:80 -p 222:22 --name gitlab --restart always -v /home/gitlab/config:/etc/gitlab -v /home/gitlab/logs:/var/log/gitlab -v /home/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce:latest
## 4. 修改配置
vi /home/gitlab/config/gitlab.rb

#配置http协议所使用的访问地址,不加端口号默认为80
external_url 'http://192.168.199.231'

#配置ssh协议所使用的访问地址和端口
gitlab_rails['gitlab_ssh_host'] = '192.168.199.231'
gitlab_rails['gitlab_shell_ssh_port'] = 222 # 此端口是run时22端口映射的222端口
:wq #保存配置文件并退出

docker restart gitlab
