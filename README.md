dokku-repodeploy
=============

Some useful commands for dokku to use with your continuous integration. Basically gives you a command which updates a bare repository on the server and pushes that to dokku:receive just like the dokku git plugin does.

This allows you to make for e.g. an Ansible playbook which runs the following to deploy your app:

`dokku repo:deploy myredonkapp https://github.com/redonk/app.git master`

## Installation

```sh
git clone https://github.com/fixate/dokku-deployrepo.git /var/lib/dokku/plugins/dokku-deployrepo
dokku plugins-install
```

## Usage

#### Your deploy step:

Too 'add' the application (usefull if you want to put ssl certificates in place before deploying)

`dokku repo:init [app_name] [scm_repository] (branch/ref or defaults to master)`

deploy (calls ansible:init)

`dokku repo:deploy [app_name] [scm_repository] (branch/ref or defaults to master)`

You will need to allow add github/bitbucket server key to known_hosts on the deployment target.
Something like:

`ssh-keyscan -H bitbucket.org >> ~/.ssh/known_hosts`

Not ideal I know...

#### Restart the app:

`dokku repo:restart_app [app_name]`

