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

#### Demo

[![asciicast](https://asciinema.org/a/abwq2v9d48saapc8bct9n2igo.png)](https://asciinema.org/a/abwq2v9d48saapc8bct9n2igo)

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

#### Functions description

###### prepare

- create a zip archive of the project.

This function will create a zip archive from project directory at the `./deploy` directory. Environment is supplied via a parameter.

###### deploy-clear

This function can be used to deploy an entire project, both code and database.
It will perform the following actions:

 - remove all files in `{{deploy_path}}`
 - restore archive `release-{{release_name}}.zip`
 - restore db from `release-{{release_name}}.sql.gz`
 - clear cache

###### deploy

This function can be used to deploy minor code changes and database migrations.
It will:

 - restore archive `release-{{release_name}}.zip`
 - run `phinx migrate` on the servers.
 - clear cache.

#### Tasks description

###### clear

Delete all files and directories from the deploy directory, excluding `vendor` directory.

###### deploy:prepare

Check ssh connection and create the deployment directory.

###### deploy:uploadcode

Upload zipped project to deploy directory and unzip it.

###### deploy:clear_cache

Clear CS-Cart cache.

###### migrate:dbinit

Restore mysql dump from local archive.

###### migrate:dbmigrate

Run migrations on remote servers.

###### migrate:phinx_config

Prepare phinx config file and upload it.

#### Help needed?

For more documentation see [Deployer docs](http://deployer.org/docs) and deploy.php source code.

#### License

MIT
