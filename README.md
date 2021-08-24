NOTE: Current status is got tested using docker images for composer and php cli commands

Tuesday, August 24, 2021 at 9:31:49 AM

```bash
~/p/nrm-limesurvey ❯❯❯ git clone --branch 5.1.3+210817 --single-branch https://github.com/LimeSurvey/LimeSurvey.git src
```

--

```bash
~/p/nrm-limesurvey ❯❯❯ git clone --branch 5.1.3+210817 --single-branch https://github.com/LimeSurvey/LimeSurvey.git src
Cloning into 'src'...
remote: Enumerating objects: 366997, done.
remote: Counting objects: 100% (3780/3780), done.
remote: Compressing objects: 100% (1510/1510), done.
remote: Total 366997 (delta 2468), reused 3440 (delta 2232), pack-reused 363217
Receiving objects: 100% (366997/366997), 1009.10 MiB | 2.05 MiB/s, done.
Resolving deltas: 100% (264071/264071), done.
Note: switching to '78427c37def79ad165a3dc2ead0d22d18a965f98'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

Updating files: 100% (13717/13717), done.
```

---


```bash

~/p/nrm-limesurvey ❯❯❯ docker run --rm --interactive --tty --volume $PWD:/app \                     
    docker.io/library/composer init

                                            
  Welcome to the Composer config generator  
                                            


This command will guide you through creating your composer.json config.

Package name (<vendor>/<name>) [root/app]: bcgov/nrm-limesurvey
Description []: NRM LimeSurvey customized for OpenShift 
Author [, n to skip]: Gary Wong <Gary.T.Wong@gov.bc.ca>
Minimum Stability []: dev
Package Type (e.g. library, project, metapackage, composer-plugin) []: project
License []: Apache-2.0

Define your dependencies.

Would you like to define your dependencies (require) interactively [yes]? no
Would you like to define your dev dependencies (require-dev) interactively [yes]? yes
Search for a package: composer/composer
Enter the version constraint to require (or leave blank to use the latest version): ^2.0
Search for a package: overtrue/phplint
Enter the version constraint to require (or leave blank to use the latest version): ^2.0
Search for a package: phpspec/prophecy
Enter the version constraint to require (or leave blank to use the latest version): ^1.12
Search for a package: phpunit/phpunit
Enter the version constraint to require (or leave blank to use the latest version): ^9.5
Search for a package: squizlabs/php_codesniffer
Enter the version constraint to require (or leave blank to use the latest version): ^3.5
Search for a package: 
Add PSR-4 autoload mapping? Maps namespace "Bcgov\NrmLimesurvey" to the entered relative path. [src/, n to skip]: 

{
    "name": "bcgov/nrm-limesurvey",
    "description": "NRM LimeSurvey customized for OpenShift",
    "type": "project",
    "require-dev": {
        "composer/composer": "^2.0",
        "overtrue/phplint": "^2.0",
        "phpspec/prophecy": "^1.12",
        "phpunit/phpunit": "^9.5",
        "squizlabs/php_codesniffer": "^3.5"
    },
    "license": "Apache-2.0",
    "autoload": {
        "psr-4": {
            "Bcgov\\NrmLimesurvey\\": "src/"
        }
    },
    "authors": [
        {
            "name": "Gary Wong",
            "email": "Gary.T.Wong@gov.bc.ca"
        }
    ],
    "minimum-stability": "dev",
    "require": {}
}

Do you confirm generation [yes]? 
Would you like to install dependencies now [yes]? 
```

--

```bash

~/p/nrm-limesurvey ❯❯❯ docker run --rm --interactive --tty --volume $PWD:/app \                     
    docker.io/library/composer update
```

--
```bash
docker run --rm -it --name phpfpm -v $PWD:/app docker.io/bitnami/php-fpm /bin/bash
```

NOTE: `--extensions=php`

---

https://github.com/axelerant/db-docker/blob/master/composer.json

https://github.com/axelerant/db-docker/blob/master/.github/workflows/phpchecks.yml

