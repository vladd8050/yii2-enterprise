Yii2 Enterprise Application Template
====================================

Yii 2 Enterprise Application Template is a skeleton Yii 2 application best for rapidly creating enterprise projects.

Basis on [wfcreations/yii2-app-api](https://github.com/wfcreations/yii2-app-api)

REQUIREMENTS
------------

The minimum requirement by this application template that your Web server supports PHP 5.6.0.

DIRECTORY STRUCTURE
-------------------

```
common
    config/              contains shared configurations
    mail/                contains view files for e-mails
    models/              contains model classes used in both backend and frontend
console
    config/              contains console configurations
    controllers/         contains console controllers (commands)
    migrations/          contains database migrations
    models/              contains console-specific model classes
    runtime/             contains files generated during runtime
backend
    assets/              contains application assets such as JavaScript and CSS
    config/              contains backend configurations
    controllers/         contains Web controller classes
    models/              contains backend-specific model classes
    runtime/             contains files generated during runtime
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
api
    assets/              contains application assets such as JavaScript and CSS
    config/              contains api configurations
    controllers/         contains Web controller classes
    models/              contains api-specific model classes
    runtime/             contains files generated during runtime
    modules/             contains api versioning
    v1/                  contains module version 1
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
frontend
    assets/              contains application assets such as JavaScript and CSS
    config/              contains frontend configurations
    controllers/         contains Web controller classes
    models/              contains frontend-specific model classes
    runtime/             contains files generated during runtime
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
    widgets/             contains frontend widgets
vendor/                  contains dependent 3rd-party packages
environments/            contains environment-based overrides
tests                    contains various tests for the advanced application
    codeception/         contains tests developed with Codeception PHP Testing Framework
```

INSTALLATION
------------

### Install from an Archive File

Extract the github archive file to a directory named `yii2-enterprise` that is directly under the Web root.

After extraction run
```
php composer.phar global require "fxp/composer-asset-plugin:1.0.0-beta1"
php composer.phar install
```

You can then access the application through the following URL:

~~~
http://localhost/yii2-enterprise/project/web/
~~~


### Install via Composer

If you do not have [Composer](http://getcomposer.org/), you may install it by following the instructions
at [getcomposer.org](http://getcomposer.org/doc/00-intro.md#installation-nix).

You can then install this application template using the following command:

~~~
composer global require "fxp/composer-asset-plugin:~1.0.0"
php composer.phar create-project --prefer-dist --stability=dev sibds/yii2-enterprise app
~~~

Now you should be able to access the application through the following URL, assuming `app` is the directory
directly under the Web root.

~~~
http://localhost/app/api/web/
http://localhost/app/backend/web/
http://localhost/app/frontend/web/
~~~

CONFIGURATION
-------------

### Database

Edit the file `common/config/db.php` with real data, for example:

```php
return [
    'class' => 'yii\db\Connection',
    'dsn' => 'mysql:host=localhost;dbname=yii2-enterprise',
    'username' => 'root',
    'password' => '123',
    'charset' => 'utf8',
];
```
**NOTE:** Yii won't create the database for you, this has to be done manually before you can access it.

Also check and edit the other files in the `config/` directory to customize your application.

#### Apply migrations

```php
php console/yii migrate
```

### Initial RBAC config

```php
php console/yii rbac/init
```

### Enabling JSON Input

To let the API accept input data in JSON format, configure the [[yii\web\Request::$parsers]] property of
the `request` [application component](http://www.yiiframework.com/doc-2.0/guide-structure-application-components.html)
to use the [[yii\web\JsonParser]] for JSON input:

```php
'request' => [
    'parsers' => [
        'application/json' => 'yii\web\JsonParser',
    ]
]
```

> Info: The above configuration is optional. Without the above configuration, the API would only recognize 
  `application/x-www-form-urlencoded` and `multipart/form-data` input formats.
  
**IMPORTANT: without rbac/init you CAN'T LOG IN into backend**
### Demo user
~~~
Login: webmaster
Password: webmaster
~~~
