# Islandora Vagrant Base Box [![Build Status](https://travis-ci.org/Islandora-Labs/islandora_vagrant_base_box.svg?branch=master)](https://travis-ci.org/Islandora-Labs/islandora_vagrant_base_box)

## Introduction

This is a base box for [Islandora Vagrant](https://github.com/Islandora-Labs/islandora_vagrant), and an export box lives on [atlas](https://atlas.hashicorp.com/ruebot/boxes/islandora-base).

The virtual machine that is built uses 3GB of RAM. Your host machine will need to be able to support that.

N.B. This virtual machine **should not** be used in production.

## Requirements

1. [VirtualBox](https://www.virtualbox.org/)
2. [Vagrant](http://www.vagrantup.com)
3. [git](https://git-scm.com/)

## Use

1. `git clone https://github.com/islandora-labs/islandora_vagrant_base_box`
2. `cd islandora_vagrant_base_box`
3. `vagrant up`

## Connect

You can connect to the machine via the browser at [http://localhost:8000](http://localhost:8000).

The default Drupal login details are:
  - username: admin
  - password: islandora

MySQL:
  - username: root
  - password: islandora

Tomcat Manager:
  - username: islandora
  - password: islandora

Fedora:
  - username: fedoraAdmin
  - password: fedoraAdmin

GSearch:
  - username: fgsAdmin
  - password: fgsAdmin

ssh, scp, rsync:
  - username: vagrant
  - password: vagrant
  - Examples
    - `ssh -p 2222 vagrant@localhost` or `vagrant ssh`
    - `scp -P 2222 somefile.txt vagrant@localhost:/destination/path`
    - `rsync --rsh='ssh -p2222' -av somedir vagrant@localhost:/tmp`

## Environment

- Ubuntu 14.04
- Drupal 7.43
- MySQL 5.5.47
- Apache 2.4.7
- Tomcat 7.0.55.0
- Solr 4.2.0
- Fedora 3.8.1
- GSearch HEAD
- PHP 5.5.9-1ubuntu4.14
- Java 8 (Oracle)
- FITS 0.10.1
- drush 5.10.0
- jQuery 1.10.2

## Customization

If you'd like to add your own customization script (to install additional modules, call other scripts, etc.), you can create a `custom.sh` file in the project's `scripts` directory. When that file is present, Vagrant will run it after all the other provisioning scripts have been run.

### Custom base box
To create a custom base box to use with Atlas (e.g., if you need different versions of Solr, Fedora, Java, etc.) the basic steps are as follows: 
- Clone the repo 
 - `git clone https://github.com/Islandora-Labs/islandora_vagrant_base_box`
 - `cd islandora_vagrant_base_box`
- Customize the provisioning scripts as necessary (Make note of the VM name)
- Provision the VM
 - `vagrant up`
- Export the VM to a box file 
 - `vagrant package --base <VM NAME>`
- [Upload the box file to Atlas using the web interface or otherwise](https://atlas.hashicorp.com/help/vagrant/boxes/create)
- **NOTE: Vagrant will replace the default ssh keys during the provision step. To disable this behavior, add the following line to your Vagrantfile:** 
 - `config.ssh.insert_key = false`

## Maintainers

* [Nick Ruest](https://github.com/ruebot)
* [Luke Taylor](https://github.com/lutaylor)

## Authors

* [Nick Ruest](https://github.com/ruebot)
* [Jared Whiklo](https://github.com/whikloj)
* [Logan Cox](https://github.com/lo5an)
* [Kevin Clarke](https://github.com/ksclarke)
* [Mark Jordan](https://github.com/mjordan)

## Acknowledgements

This project was inspired by Ryerson University Library's [Islandora Chef](https://github.com/ryersonlibrary/islandora_chef), which was inspired by University of Toronto Libraries' [LibraryChef](https://github.com/utlib/chef-islandora). So, many thanks to [Graham Stewart](https://github.com/whitepine23), and [MJ Suhonos](http://github.com/mjsuhonos/).
