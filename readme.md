[![PHP >= 7+](https://img.shields.io/badge/php-%3E%3D%207-8892BF.svg?style=flat-square)](https://php.net/)

[![Build Status](https://img.shields.io/travis/ShkrutDenis/demo-laravel/master.svg?style=flat)](https://travis-ci.org/ShkrutDenis/demo-laravel.svg?branch=master)

[![Coverage Status](https://img.shields.io/coveralls/ShkrutDenis/demo-laravel/develop.svg?style=flat)](https://coveralls.io/r/ShkrutDenis/demo-laravel?branch=develop)

Project with basic functional:
 - authorization;
 - registration;
 - verify account by link (sending to email);
 - recovery password by link (sending to email);
 - simple ACL;
 - management users (CRUD).
 
Used next packages and dependencies:
 - PHP : ^7.1.3;
 - Laravel : 5.7.*;
 - Vue : ^2.5.17;
 - Vuex : ^3.0.1;
 - Element-ui: ^2.4.11;

## Getting started

Instruction how install project before using. 

### Setup project

Clone this repository to your local machine:

- git clone https://github.com/ShkrutDenis/demo-laravel.git

    > If your already have repository, you can add remote 
    
    > ``` git remote add https://github.com/ShkrutDenis/demo-laravel.git ```

- git checkout -b develop

- git pull https://github.com/ShkrutDenis/demo-laravel.git develop

Next step you need to setup environment. You can select any environment between `vagrant` or `docker`.

#### Setup environment

##### vagrant (homestead):

> Project use homestead, because your need install VirtualBox v 5.*
    
1) First you need run next bash command:
    ```
        bash ./provision/vagrant/init.sh
    ```
    > Now you will must be in vagrant, your user will must be vagrant@basicFunc:~$ 
    
3) Run migrations and seeders:
    ```
        php artisan migrate
        php artisan db:seed
    ```
    > This commands and any same must be run in vagrant machine
    
4) Run setup super admin:
    ```
        php artisan setup:super-admin
    ```

5) Now you can get access to site in your browser by next link:
    ```
        http://130.131.132.133
    ```
    
    > You can change path or any params in Homestead.yaml in root project directory
    
##### docker (laradock v7.8.0):

1) Run next bash command:
    ```
        bash ./provosion/docker/docker-up-script.sh
    ```
    > Now you must be in "workspace" docker container
    
2) Change user from root to laradock:
    ```
        su - laradock
        cd /var/www/
    ``` 
3) Now you can get access to site in your browser by next link:
    ```
       http://localhost
    ```
    
### Testing

> All command must be run on virtual machine (vagrant) or inside container (docker).

For start tests run next command:
```
    php vendor/bin/codecept run
```
For check codestyle by codesniffer run next command:
```
    php vendor/bin/phpcs
```
For check code for copy-paste run next command:
```
    php vendor/bin/phpcpd app/
```