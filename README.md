## About

CS-Cart and Multi-Vendor deployment toolkit is a simple script that helps developers and system administrators save a lot of time when deploying CS-Cart or Multi-Vendor installations. It will deliver your files to the servers specified, import data dumps and run migrations.

Current version is 1.0.1.

  * [Demo](#demo)
  * [Requirements](#requirements)
  * [Getting started](#getting-started)
  * [Usage](#usage)
  * [Functions description](#functions-description)
      * [prepare](#prepare)
      * [deploy-clear](#deploy-clear)
      * [deploy](#deploy)
  * [Tasks description](#tasks-description)
      * [clear](#clear)
      * [deploy:prepare](#deployprepare)
      * [deploy:uploadcode](#deployuploadcode)
      * [deploy:clear_cache](#deployclear_cache)
      * [migrate:dbinit](#migratedbinit)
      * [migrate:dbmigrate](#migratedbmigrate)
      * [migrate:phinx_config](#migratephinx_config)
  * [Help needed?](#help-needed)
  * [License](#license)

#### Requirements

* [PHP](https://secure.php.net/) 5.5.0+
* [Deployer](http://deployer.org) 3.3.0+
* [YAML](https://pecl.php.net/package/yaml) PHP extension
* [ZIP](https://pecl.php.net/package/zip) PHP extension

#### Getting started

Firstly, acquire the script:
```
git clone https://github.com/simtechdev/deploy-toolkit.git
cd deploy-toolkit
mkdir -p deploy-toolkit/deploy
```

Then you'll need to edit `config.yml`, where all locations and servers are specified.
<!-- config -->

You can now proceed with the two main commands for deployment.

Running `dep prepare development` will create a ZIP archive for the development environment.
Then, `dep deploy development` will deploy everything to the remote servers.

#### Commands
<!-- commands -->

###### prepare

- create a zip archive of the project.

###### deploy-clear

This function can be used to deploy an entire project, both code and database.

###### deploy

This function can be used to deploy minor code changes and database migrations.

###### clear

Delete all files and directories from the deploy directory, excluding `vendor` directory.

###### deploy:prepare

Check ssh connection and create the deployment directory.

###### deploy:uploadcode

Upload zipped project to deploy directory and unzip it.

###### deploy:clear_cache

Clear CS-Cart cache.

###### migrate:dbinit

Restore mysql dump from the local archive.

###### migrate:dbmigrate

Run migrations on the remote servers.

###### migrate:phinx_config

Prepare phinx config file and upload it.

#### Help needed?

For more documentation see [Deployer docs](http://deployer.org/docs) and deploy.php source code.

#### License

MIT
