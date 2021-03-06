# Webserver with Apache/2.4.18 and PHP 7.0.22-0ubuntu0.16.04.1 on Ubuntu

Image with extension oci8, allow you to access Oracle Database 12c, 11g, 10g, 9i and 8i.

The default virtualhost has default params:
- display_errors **on**
- error_reporting **22527**
  - You can get the number of error_reporting on [PHP Error Reporting Wizard](http://www.bx.com.au/tools/ultimate-php-error-reporting-wizard)
- date.timezone **America/Sao_Paulo**
- max_execution_time **60**
- max_input_time **120**
- memory_limit **512**
- post_max_size **30M**
- upload_max_filesize **30M**

The port 80 is expose

# How to use
###### Using docker in command line
```
docker run -d -v [host_path]:/var/www/html -p [host_port]:80 edersondev/php7_oci
```

###### Using docker-compose
```
version: '3'
services:
  webphp:
    image: edersondev/php7_oci
    ports:
      - "[host_port]:80"
    volumes:
      - [host_path]:/var/www/html

```

This image has a environment variable called WEB_DOCUMENT_ROOT if you need to point DocumentRoot to another folder. For exemple the framework Laravel, the DocumentRoot needs to point to public folder.

###### Using docker in command line
```
docker run -d -v [host_path]:/var/www/html -p [host_port]:80 -e WEB_DOCUMENT_ROOT=public edersondev/php7_oci
```

###### Using docker-compose
```
version: '3'
services:
  webphp:
    image: edersondev/php7_oci
    ports:
      - "[host_port]:80"
    volumes:
      - [host_path]:/var/www/html
    environment:
      WEB_DOCUMENT_ROOT: public
```