# personal-vps

[![Build Status](https://travis-ci.org/craighurley/personal-vps.svg?branch=master)](https://travis-ci.org/craighurley/personal-vps)

Create and configure a Virtual Private Server using Ansible.

Ansible will:

- Configure iptables.
- Install common applications.
- Enable auto security updates.
- Update all installed packages.
- Enable SELINUX.
- Configure bash.
- Add users.
- Tighten SSH security (e.g. allow key auth only).
- Set the locale.
- Add custom entries to sudo.
- Install and configure NTP.
- Install and configure ZNC.

# Running

1. Create your target VM.  If you create your VM using Vagrant, you can automatically have it 
2. Create and populate your inventory files for each environment.
3. Run `bootstrap.yml` playbook.  You can either run this automatically (using Vagrant for example), or manually like this:

```bash
ansible-playbook bootstrap.yml -i inventory.production
```

4. Once `bootstrap.yml` has run successfully the necessary users & keys have been added to the target VM, so you can run the main playbook, `vps.yml`:

```bash
ansible-playbook vps.yml -i inventory.production
```

# Environment

The provisioner passes Ansible a value for `v_environment`; that should be one of the following values:

- `production`
- `staging`
- `development`

This value will effect certain roles, for example, the `bash` role will set the colour of the bash prompt to red, yellow or green depending on the value of `v_environment`.  `v_environment` defaults to `development`.

You can set this this variable either on the command line or in your inventory file.

# Users

See the [users readme](roles/users/) for more information on how to configure users.
