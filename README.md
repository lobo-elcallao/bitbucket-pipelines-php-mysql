[![](https://images.microbadger.com/badges/image/ilestis/bitbucket-pipelines-php-mysql.svg)](http://microbadger.com/images/ilestis/bitbucket-pipelines-php-mysql "Get your own image badge on microbadger.com")

# bitbucket-pipelines-php-mysql

[Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) [Docker](https://www.docker.com/) image based on [Debian/Jessie](https://www.debian.org/releases/jessie/) with [PHP](http://php.net/)/[MySQL](https://www.mysql.com) (and more !)

More help in Bitbucket's [Confluence](https://confluence.atlassian.com/bitbucket/bitbucket-pipelines-beta-792496469.html)

Docker image at [ilestis/bitbucket-pipelines-php-mysql](https://hub.docker.com/r/ilestis/bitbucket-pipelines-php-mysql/) (no `CMD` as it is overriden by *Pipelines*)

## Packages installed

 - `php5-cli`, `php5-sqlite`, `php5-mysqlnd`, `php5-mcrypt`, `php5-curl`, `php-gettext`, `php5-gd`, `php5-json`, `php5-intl`, `php5-xdebug`, `php5-imagick`, `imagemagick`, `openssh-client`, `curl`, `gettext`, `zip`, `mysql-server`, `mysql-client`, `git`, `codeception`
 - [Perl](https://www.perl.org/) 5.20.2
 - [Python](https://www.python.org/) 2.7 + 3.4
 - [MySQL](https://www.mysql.com/) 5.5.50 (user `root:root`)
 - [PHP](http://www.php.net/) 5.6.24
 - [Ruby](https://www.ruby-lang.org/) 2.1.5
 - [Node.js](https://nodejs.org/) 4.x LTS
 - [Codeception](https://codeception.com/) 
 - Latest [Composer](https://getcomposer.org/), [Gulp](http://gulpjs.com/), [Webpack](https://webpack.github.io/), [Mocha](https://mochajs.org/), [Grunt](http://gruntjs.com/), [PHPUnit](https://phpunit.de/)

## Sample `bitbucket-pipelines.yml`

```YAML
image: ilestis/bitbucket-pipelines-php-mysql
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -p root -e "CREATE DATABASE test;"
          - composer config -g github-oauth.github.com XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
          - composer install --no-interaction --no-progress --prefer-dist
          - npm install --no-spin
          - gulp
```

## Changelog

### Latest

 - Added Codeception

### Fork

 - Fork from smartapps/bitbucket-pipelines-php-mysql
 - Perl, Python, PHP, MySQL, Node.js
 - Composer, Gulp
 - Adds Ruby, Grunt, Webpack, Mocha, Sqlite
 - Set `root` password to `root`
