# Greenpeace Planet 4
This project provides the base for all Planet 4 sites. 
To create a new project, that is powered by Planet 4, fork this repository.

## Installation
All dependencies should be managed by [Composer](http://getcomposer.org). 
They are listed inside the `composer.json` file in the root of this repository.
Install all required dependencies with one simple command:

	composer install

If you want to add more dependencies to this project, you should also always
add them to the composer file.
No manual copying of files should be necessary and any time.

## Configuration
The complete configuration of Wordpress is stored inside the `wp-cli.yml` file.
When you need to change the database configuration, the title or the URL of this
installation, please take a look at that file.

Before we can initialize the installation, make sure you did create the database
that is configured inside the configuration file.
This can be easily done with this command:

	echo "CREATE DATABASE wordpress;" | mysql

It might be necessary to pass a username (`-u`) and a password (`-p`) to the 
mysql command. 
More information about this is available in the man page of `mysql` or 
[online](https://dev.mysql.com/doc/refman/5.7/en/mysql-command-options.html).

After the database is created, the new Wordpress installation is installed with 
one simple composer command:

	composer run config

This will perform multiple steps:

- Create a `wp-config.php` file with default values from the `wp-cli.yml`.
- Create the initial database structure and insert the default data
- Activate the theme that is configured inside the `wp-cli.yml`

### Changing the theme
Themes should never be changed inside the web front-end. 
This would make it impossible to have an automated installation that can be 
re-applied whenever needed. 
To change the theme add the dependency to the `composer.json` file and change
the related line inside the `wp-cli.yml`. 
After that you can run this composer command to activate the theme:

	composer run config:theme

The theme should be activated and be used by the Wordpress installation now.
