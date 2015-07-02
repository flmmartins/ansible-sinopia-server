# Ansible Playbook for Sinopia

An ansible playbook to build ghost blog

**Important**: This script will update your nodejs to a stable version

### Packages installed by Ansible
* Nodejs (latest stable)
* Npm
* Wget
* zip
* vim

### Configurations made by Ansible

* Instalation directory: /var/www/sinopia
* URL: http://localhost:4873/
* Create user called sinopia in the server
* Install sinopia with a non-restriction config file which means that everyone will be able to pubilsh and read packages
* Creates a sinopia.sh script to start and stop the server
* Add sinopia.sh to cron so it can start sinopia on every reboot


### How to run the installation

Install ansible in your machine and clone this repository.
Edit the inventory file with the host's ips you want to run sinopia on
Run:

```bash
ansible-playbook -i inventory playbook.yml -u <machine-user> -kK
```

### How to publish

Run this in your machine:

```bash
$npm set registry http://localhost:4873
```

Create a user (in this case any user is allowed):

```bash
$npm adduser --registry http://localhost:4873
```

This settings will be saved in your ~/.npmrc now it's only a matter to run:

```bash
$npm publish
```


### Run sinopia manually in the server

Start

```bash

$cd /var/www/sinopia

$sudo ./sinopia.sh start

```
Stop

```bash

$cd /var/www/sinopia

$sudo ./sinopia.sh stop


```

### What if I want to restrict access to sinopia?

* Change config file
* Go to the server and run $npm login or $npm adduser. It will create a user and sinopia will use it
* After that don't forget to ask you team to run: $npm adduser --registry http://localhost:4873
