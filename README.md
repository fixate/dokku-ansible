dokku-ansible
=============

Some useful commands for dokku to use with your continuous integration.

## Installation

```sh
git clone https://github.com/fixate/dokku-ansible.git /var/lib/dokku/plugins/dokku-ansible
dokku plugins-install
```

## Usage

#### Your deploy step:

`dokku ansible:deploy [app_name] [scm_repository]`

You will need to allow add github/bitbucket server key to known_hosts on the deployment target.
Something like:

`ssh-keyscan -H bitbucket.org >> ~/.ssh/known_hosts`

Not ideal I know...

#### Restart the app:

`dokku ansible:restart_app [app_name]`

