#### 环境：win10 10.0.17763.475 WSL Ubuntu 18.04 LTS
#### 编写时间：2019/05/13
1.安装mysql
   ```shell
   sudo apt-get install mysql-server
  ```  
  在此过程中，没有让你输入root密码,所以下面的登录也不需要输入密码  
2.使用root登录mysql
```shell
    mysql -uroot -p
```
* 遇到问题
   ```shell
   No directory, logging in with HOME=/”
   ```
* 解决办法,使用root权限登录
   ```shell
   sudo service mysql stop
   sudo usermod -d /var/lib/mysql/ mysql
   ```
3.再次登录
* 遇到问题
   ```shell
   ERROR 1698 (28000): Access denied for user 'root'@'localhost'
   ```
* 解决办法
   ```shell
   sudo mysql -uroot -p
  ```
4.新建一个不需要sudo登录的用户
   ```shell
   create user 'yourusername'@'localhost' identified by 'yourpassword';
   grant all on *.* to 'yourusername'@'localhost';
   FLUSH PRIVILEGES;
   ```
   * 代码解释  
   * 第一句：创建一个密码为yourpassword的yourusername的用户
   * 第二句：授权所有的权限给 yourusername用户
   * 第三句：立即生效
   