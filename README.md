# [PDFfiller Blog](http://blog.pdffiller.com/)

Created using Wordpress and [Bedrock](https://roots.io/bedrock/).
All plugins and themes can be installed using composer.

## Requirements
#### Docker
* PHP >= 5.6
* Composer - [Install](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)
* Docker - [Install](https://docs.docker.com/install/)
* Docker compose - [Install](https://docs.docker.com/compose/install/)

#### Local server
* PHP >= 5.6
* Composer - [Install](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)
* WP-CLI - [Install](http://wp-cli.org/#installing)

## Installation
#### Docker

1. Clone this repo:

    `git clone git@github.com:pdffiller/blog.git`
  
2. Install Wordpress, plugins and themes by composer.

    `composer install`
  
3. Run:

    `sudo docker-compose up`
  
    Makes sure it works [http://localhost:8081](http://localhost:8081)
  
4. Put MySQL dump into your local server.

   Use pre-installed Adminer - [http://localhost:8082](http://localhost:8082)
   
   Or [install](https://www.adminer.org/#download) your own

   Connection data(according to docker-compose.yml):

    * Server - database-wp.dev
    * User - admin
    * Password - admin
    * Database  - wp_blog

   If you need console. Run:

       sudo docker ps -a
       sudo docker exec -it <CONTAINER_ID>/bin/sh
    
5. [Login](http://localhost:8081/wp/wp-login.php) using existed admin credentials, create your own admin user. 
Go to "Plugins" and deactivate "WP Force SSL" plugin, because built in php server can't work trough HTTPS


#### Local server

1. Clone this repo:

  `git clone git@github.com:pdffiller/blog.git`

2. Copy `.env.example` to `.env` and update environment variables:
  * `DB_NAME` - Database name
  * `DB_USER` - Database user
  * `DB_PASSWORD` - Database password
  * `DB_HOST` - Database host
  * `WP_ENV` - Set to environment (`development`, `staging`, `production`)
  * `WP_HOME` - Full URL to WordPress home (http://example.com)
  * `WP_SITEURL` - Full URL to WordPress including subdirectory (http://example.com/wp)
  * `AUTH_KEY`, `SECURE_AUTH_KEY`, `LOGGED_IN_KEY`, `NONCE_KEY`, `AUTH_SALT`, `SECURE_AUTH_SALT`, `LOGGED_IN_SALT`, `NONCE_SALT`

  If you want to automatically generate the security keys (assuming you have wp-cli installed locally) you can use the very handy [wp-cli-dotenv-command][wp-cli-dotenv]:

      wp package install aaemnnosttv/wp-cli-dotenv-command

      wp dotenv salts regenerate

  Or, you can cut and paste from the [Roots WordPress Salt Generator][roots-wp-salt].

3. Install Wordpress, plugins and themes by composer.

  `composer install`

4. Put MySQL dump into your local server.

4. Set your site vhost document root to `/path/to/site/web/` (`/path/to/site/current/web/` if using deploys)

5. Access WP admin at `http://example.com/wp/wp-admin`

## Updating

You can update Wordpress, plugins and themes using `composer update`, no more updates from wp-admin.

## Documentation

Bedrock documentation is available at [https://roots.io/bedrock/docs/](https://roots.io/bedrock/docs/).