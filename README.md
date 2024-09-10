# ขั้นตอนการติดตั้ง Docker บน Oracle Linux 9

1. Remove Docker Old Version

   ```bash
   yum remove docker \
                     docker-client \
                     docker-client-latest \
                     docker-common \
                     docker-latest \
                     docker-latest-logrotate \
                     docker-logrotate \
                     docker-engine
   ```

   1. Installation methods

      ```bash
      yum install -y yum-utils
      ```

      ```bash
      yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
      ```
2. Install Docker Engine

   ```bash
   yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```
3. Start Docker 

   ```bash
   systemctl start docker
   ```

   ```bash
   systemctl enable docker
   ```
4. Start mysql5.6

   ```bash
   docker run -dit --name mysql5.6 \
   	-p 3333:3306 \
   	-e MYSQL_ROOT_PASSWORD=123456 \
   	-v /var/lib/mysql:/var/lib/mysql:rw \
   	-v /root/my.cnf:/etc/my.cnf \
   	--restart always cytopia/mysql-5.6
   ```
