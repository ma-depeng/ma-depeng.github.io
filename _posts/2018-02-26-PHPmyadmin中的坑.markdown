---
layout:     post
title:      "phpmyadmin配置注意事项"
subtitle:   " \"杂记\""
date:       2018-02-26 06:00:00
author:     "德鹏"
header-img: "img/bg/post-bg.jpg"
catalog: true
tags:
    - 程序开发

---

> “phpmyadmin配置注意事项”

为了本机测试方便，安装了XAMPP PHP集成环境，默认情况下，phpmyadmin连接mysql没有使用密码，即root密码为空。但如果要给root配置密码，需要注意以下事项。

1. config.default.php 这个文件只是一个配置样例，更改这个文件中的配置不会起作用，要留意。需要改的配置文件是config.inc.php后，配置方可起作用。  
文件位于xampp目录下。  

2. PHPmyadmin有三种登录方式，cookie、http和config，只有当配置方式改为config时，配置文件才起作用。其它两种方式下，会显示登录框，要求输入用户名和密码。这两种界面下，不能使用空密码。  

3. 与linux一样，可以在命令行界面下直接进入mysql数据库进行更改密码操作，更改密码后，重启MYSQL服务后，新的密码生效。但不可通过PHPMYADMIN直接更改MYSQL表的字段。  

4. 在linux下有一个mysqld_safe的脚本，windows下没有，如果要进入安全模式，直接使用mysqld.exe带参数即可。mysqld.exe --skip-grant-tables  

5. 如果需要通过PHPMYADMIN来更改MYSQL密码，方法为，点击主页（左上角）-> 选择用户账户 -> 修改用户权限，输入新密码。注意不要点生成，生成按钮的意思为生成一个新密码。  

6. 当MYSQL中的ROOT密码不为空时，参考更改xampp/phpmyadmin/config.inc.php中的密码来登录。特别注意，config.inc.php在安装后就存在，不要手工将config.default.php更改为config.inc.php（记得很早的版本才有这个操作，现在不需要）。
