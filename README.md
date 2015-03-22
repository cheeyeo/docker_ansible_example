## Ansible + Docker + Docker Compose + Rails

An example application that uses Ansible and Docker for automated deployment
of a Rails app onto a remote host.

## Setup

You need the following tools to work:
* Docker
* Docker compose (formerly fig)
* Ansible

If you installed Ansible on the Mac using Homebrew, please make sure your hosts
file is located inside /usr/local/etc/ansible/hosts.

If you get errors such as 'client and server' are not the same version, then
you need to uninstall and reinstall Go and then update the boot2docker image:

```
boot2docker update
```

To test locally, clone this repo and run the following:

```
docker-compose build

docker-compose up
```

To test remotely, run the following ansible playbooks:

```
ansible-playbook main_playbook.yml

ansible-playbook secondary_playbook.yml
```

The main_playbook.yml contains tasks for installing git, docker (& set it up as a service) and then clones the repo and runs docker compose on it.

The secondary_playbook.yml contains other tasks to be run such as migrations.

This is my first attempt at learning Ansible and playbooks hence the playbooks
here are very basic and not meant for production use!

## Idea

After reading the [following blog post about hot code dpeloys using docker](http://ionicframework.com/blog/docker-hot-code-deploys/) I decided to build this experiment to try it out.

The idea is to use Ansible to clone and copy the code into the docker container
rather than building it all into one big image.
