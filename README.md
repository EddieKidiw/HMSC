# Version
 2.0.0
# HMSC
 Hide My Source Code
## How to get my OS architecture

### Linux
Open command line
Type `uname -a` , `uname -m` or 
 `dpkg --print-architecture` into the command line, and press Enter

```bash
$ uname -m
```
ex: result `arm, arch64 ,x86_64`


### windows
Open command prompt

Type `systeminfo` into the command prompt, and press Enter


```bash
$ systeminfo
```
See if your **System Type:**

## ZTS or NTS

where can i find out?

check php version `php -v`

example:
```bash
$ php -v
PHP 7.4.3 (cli) (built: Mar  2 2022 15:36:52) ( NTS )
Copyright (c) The PHP Group
```
Already seen your php system using NTS

```bash
$ php -v
PHP 7.3.10 (cli) (built: Dec  5 2019 01:21:06) ( ZTS )
Copyright (c) 1997-2018 The PHP Group
```
And this is the ZTS version

# instalation
Get extension_dir
```bash
$ php -i | grep extension_dir
```
result
```bash
extension_dir => /usr/lib/php/20190902 => /usr/lib/php/20190902
```
Download the hmsc extension according to your php version and architecture and copy or move to the extension directory (example directory /usr/lib/php/20190902)



```bash
ls /usr/lib/php/20190902 | grep hmsc
```
***note: not in all os the extension directory is always /usr/lib/php/20190902 it can be different depending on the php version***

enable zend_extension

`php --ini` to get location php.ini

Example:
```bash
$ php --ini
```
result
```bash
Configuration File (php.ini) Path: /etc/php/7.4/cli
Loaded Configuration File:         /etc/php/7.4/cli/php.ini
Scan for additional .ini files in: /etc/php/7.4/cli/conf.d
Additional .ini files parsed:      /etc/php/7.4/cli/conf.d/10-mysqlnd.ini,
```

Open the path/to/php. ini file in any editor.
```bash
nano path/to/php.ini
```
search until you find it like this

```bash
;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;

; If you wish to have an extension loaded automatically, use the following
; syntax:
;
;   extension=modulename
;
; For example:
;
;   extension=mysqli
```
put the `zend_extension=hmsc.so` for ***linux***  `zend_extension=php_hmsc.dll` for ***Windows***

```bash
Note : The syntax used in previous PHP versions ('extension=<ext>.so' and
; 'extension='php_<ext>.dll') is supported for legacy reasons and may be
; deprecated in a future PHP major version. So, when it is possible, please
; move to the new ('extension=<ext>) syntax.
```
Save the path/to/php.ini file.

Don't forget to check whether the hmsc extension is active or not `php -i | grep hmsc` , `php -v` or `php -m`

```bash
$ php -i | grep hmsc
hmsc
hmsc support     => enabled
```
```bash
$ php -v
PHP 7.3.10 (cli) (built: Dec  5 2019 01:21:06) ( ZTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.10, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.3.10, Copyright (c) 1999-2018, by Zend Technologies
    with Hide My Source Code v1.0.1, Copyright (c) 2021, by Eddie Kidiw
```

```bash
php -m
[PHP Modules]
.....
hmsc
....

[Zend Modules]
Hide My Source Code
Zend OPcache
```

:+1: 
## with nginx
```bash
syatemctl restart nginx
```
```bash
service nginx restart
```
## with apache
```bash
systemctl restart apache
```
```bash
apache2ctl restart
```
## with php-fpm
```bash
systemctl restart php-fpm
```
```bash
service restart php-fpm
```
### specific version
```bash
syatemctl restart php7.x-fpm
```
```bash
service php7.X-fpm restart
service php8.X-fpm restart
```


Online tool encoder
[https://blog.eddiekidiw.org/hmsc-encoder.html](https://blog.eddiekidiw.org/hmsc-encoder.html)
