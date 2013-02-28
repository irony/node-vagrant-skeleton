node-vagrant-skeleton
============

## TODO

* add mongodb cookbook
* add coding standards testing script

## Introduction

This is a fork of another vagrant-skeleton (thanks @pchalasis for the start box!) that I plan to use to develop Node.js powered applications. It runs on Vagrant powered  CentOS Virtual Machine.

## Components

The idea is to give full working nginx / node / mongodb stack working out of the box.

### Nginx
Nginx is preconfigured with upstream containing one server (127.0.0.1:8001).
I will serve static files from `public` folder and redirect all other requests to above upstream.
You can find Configuration file template in `build/cookbooks/nginx/templates/default/default.erb

### Node.js
Node.js will be compiled from source (http://nodejs.org/dist/node-latest.tar.gz). It contains NPM as well.

### Mongodb

### Coding standards


## Running Virtual Machine

### Vagrant
This virtual machine is managed through Vagrant. You can download Vagrant from http://vagrantup.com/.
You should consider reading http://vagrantup.com/v1/docs/getting-started/index.html as well.

### Librarian
To make it easier to install new cookbooks I use Librarian to add new cookbooks. Just edit the file
`/build/Cheffile with new cookbooks and then run
```sh
librarian-chef install
```
and after that you may use these new cookbooks in your Vagrantfile.

### Booting up
This package uses Centos box (the original skeleton used Ubunto but I prefer CentOS).
To download Centos box, type:
```sh
vagrant box add centos https://dl.dropbox.com/u/7225008/Vagrant/CentOS-6.3-x86_64-minimal.box
```
When the download is completed, type:
```sh
vagrant up
```
in project home directory. This will create virtual machine using 1 CPU core and 1024 MB of memory.

### Accessing VM
In your browser, open http://127.0.0.1:9000. This should return Nginx response.

You can also log in to VM by typing:
```sh
vagrant ssh
```
On windows system it will give you access information, on *nix systems it will log you automatically.

Default port mapping:
* 9000 points to 80 (Nginx)
* 2220 points to 22 (ssh)
* 9001 points to 8001 (Node sample app)


## Coding standard and tests
