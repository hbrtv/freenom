安装之后，发现php版本未安装composer，会提示

use class LuoLongFei\lib\log 没有这个class

安装过程如下：
cd /usr/local/php/etc/
php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');"
php composer-setup.php


会提示
```
PHP Warning:  require(): open_basedir restriction in effect. 
File(composer.phar) is not within the allowed path(s): 
(/data/www/default/:/data/www/default/kod/data/User/admin/home/document/:/usr/local/php/etc/:/tmp:/root/.composer) 
in /usr/local/bin/composer on line 24
```

这个错误表示/usr/local/php/etc/php.ini 中的有个配置open_basedir生效，大致类似于只运行php程序调用open_basedir这个参数规定的位置的类

修改open_basedir参数，加入需要引用的位置，即可

mv composer.phar /usr/local/bin/composer

然后将/usr/local/bin/加入到open_basedir

然后运行
```
php run
```

即可
