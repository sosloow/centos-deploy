## подготовка 64-битной centOS 6 для node.js сервера

1. `useradd someone sudo`
2. `passwd someone`
3. `scp ./yum.repos.d/* root@remote:/etc/yum.repos.d`
4. `sudo yum update`
5. `sudo yum install epel-release`
6. `sudo yum install git mongodb-org nodejs nginx`
