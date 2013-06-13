# Vagrant LAMP-Ruby stack
A dead-simple LAMP-Ruby stack without any bells and whistles for your basic Linux/Apache/MySQL/PHP install, using Chef Solo + Chef-Librarian for provisioning.
This project has been forked to accomodate the mass amount of people who should be porting older PHP applications to Ruby/Python/Node apps. Of course this 
will fit the bill for the Ruby/Rails nerds vs Pypyers or NodeHeads

## Requirements
* [VirtualBox](https://www.virtualbox.org)
* [Vagrant](http://vagrantup.com)
* [Chef-Librarian](https://github.com/applicationsonline/librarian)

## Installation
Clone this repository and it's submodules

    $ git clone git@github.com:MiniCodeMonkey/Vagrant-LAMP-Stack.git --recursive

Place your website in the `public_html` folder

## Usage
Start the VM

	$ cd Vagrant-LAMP-Stack
	$ chef-librarian install
	$ vagrant up

### Database dump import
Chef will automatically try to import the database dump specified by the filename set in the `:db_dump` option of your Vagrantfile.

If you are using the default configuration, just create a `dump.sql` file in the root directory with your table structure and/or content and it will be imported automatically when you run `vagrant up`.

## Installed software
* Apache 2
* MySQL
* PHP 5.4 (with mysql, curl, mcrypt, memcached, gd)
* memcached
* postfix
* vim, git, screen, curl, composer
* RVM + 1.9.3px
* Passenger

## Default credentials
### MySQL
* Username: root
* Password: root
* Host: localhost
* Port: 3306

### Memcached
* Port: 11211
