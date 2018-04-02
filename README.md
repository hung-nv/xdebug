## Install xdebug for macos

##### 1. Setup path php xampp for mac
1. sudo nano ~/.bash_profile
2. added the following to it
```
export XAMPP_HOME=/Applications/XAMPP
export PATH=${XAMPP_HOME}/bin:${PATH}
export PATH
```

##### 2. Download [xdebug-2.4.0.tgz]
http://xdebug.org/files/xdebug-2.4.0.tgz


##### 3. Unpack the downloaded file
https://codex.wordpress.org/WordPress_Coding_Standards

```angular2html
cd ~/Downloads
tar -xvzf xdebug-2.4.0.tgz
cd xdebug-2.4.0
run phpize
```

example output
```
Configuring for:
PHP Api Version:         20131106
Zend Module Api No:      20131226
Zend Extension Api No:   220131226
```

##### 4. Configure with XAMPP php-config.

```
./configure --enable-xdebug --with-php-config=/Applications/XAMPP/xamppfiles/bin/php-config
```

##### 5. run make

```
make
```

##### 6. Copy xdebug.so

```
cp modules/xdebug.so /Applications/XAMPP/xamppfiles/lib/php/extensions/no-debug-non-zts-20131226
```

Or run if not see xdebug.so
```
sudo pecl install xdebug
```

##### 7. Edit /Applications/XAMPP/xamppfiles/etc/php.ini

After “;zend_extension”, add the zend_extension setting from the xdebug.org instructions, for example:

```
zend_extension=/Applications/XAMPP/xamppfiles/lib/php/extensions/no-debug-non-zts-20131226/xdebug.so
```

##### 8. Additionally, add these xdebug configuration settings in php.ini after the zend_extension setting

```
xdebug.remote_enable=1
xdebug.remote_handler=dbgp
xdebug.remote_host=localhost
xdebug.remote_autostart = 1
xdebug.remote_port=9000
xdebug.show_local_vars=1
xdebug.remote_log=/Applications/XAMPP/logs/xdebug.log

;---------------------------------
; uncomment these dev environment
; specific settings as needed
;---------------------------------
;xdebug.idekey = "netbeans-xdebug"
;xdebug.idekey = "sublime.xdebug"

;some pages in your Drupal site will not work default = 100
;xdebug.max_nesting_level=256

```

Find “max_execution_time” and set to unlimited:

```
max_execution_time=0
```
