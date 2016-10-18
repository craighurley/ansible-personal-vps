# personal-vps

[![Build Status](https://travis-ci.org/craighurley/personal-vps.svg?branch=master)](https://travis-ci.org/craighurley/personal-vps)

Configure a Virtual Private Server using Ansible.

## Ansible

Ansible will:

* Configure iptables.
* Install common applications.
* Enable auto security updates.
* Update all installed packages.
* Enable SELINUX.
* Configure bash.
* Add or update users.
* Tighten SSH security (e.g. allow key auth only).
* Set the locale.
* Add custom entries to sudo.
* Install and configure NTP.

### Running

Ping all dev servers

```sh
$ ansible-playbook ping.yml -i inventory -l dev
```

Check what will be changed on the dev server(s)

```sh
$ ansible-playbook vps.yml -i inventory -l dev --check
```

Run on all dev servers

```sh
$ ansible-playbook vps.yml -i inventory -l dev
```

Run specific tags, e.g. `yum`

```sh
$ ansible-playbook vps.yml -i inventory -l dev --tags="yum"
```

Run for real on prod, including more verbose logs

```sh
$ ansible-playbook vps.yml -i inventory -l prod -v
```

### Users

See the [users readme](roles/users/) for more information on how to configure users.

## Development

A `Vagrantfile` is included in this repository that creates a local server for testing.  To create the local server run:

```sh
$ vagrant up
```

On running the above command, Vagrant will:

* Create each of the servers defined in `boxes.yml`.
* Call a shell script to provision the server using cloud-init.  The cloud-init configuration files are in `./cloud-init/nocloud-net/`.

Once you're finished with the vagrant box, destroy it with:

```sh
$ vagrant destroy -f
```


## Links

[http://docs.ansible.com/ansible/](http://docs.ansible.com/ansible/)
[http://cloudinit.readthedocs.io/](http://cloudinit.readthedocs.io/)
