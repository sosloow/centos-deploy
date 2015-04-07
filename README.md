## подготовка 64-битной centOS 5.1 для node.js сервера

1. `useradd someone sudo`
2. `passwd someone`
3. `sudo yum install epel-release`
4. `curl -sL https://rpm.nodesource.com/setup | bash -`
5. `scp ./yum.repos.d/* root@remote:/etc/yum.repos.d`
6. `sudo yum update`
7. `sudo yum install git mongodb-org nodejs nginx`
8. `sudo /sbin/service mongod start`
9. `sudo /sbin/service httpd stop`
10. `sudo /sbin/service nginx start`
11. `sudo npm install -g forever coffee-script`
12. `scp ./node.conf root@remote:/etc/nginx/conf.d`
