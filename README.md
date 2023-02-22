# Aptos Ansible

> NOTE: Not for production use! This is an experimental deployment method, and has not been thoroughly tested or deployed. It may be lacking features critical to operating an Aptos node in production. 

## The Mission
We've come to realize that the majority of operators choose not to run their nodes in a k8s environment, largely due to the expensive and complexity. Despite that, we don't have much first class support in terms of tooling, configuration, or documentation for non-k8s deployment. This project aims to address that. Our goal with this is to support any combination of:

- VM / bare metal
- Docker / source code
- systemd / docker-compose
- OS (within reason, e.g. Debian-like, Arch, CentOS, Windows)

Beyond deployment environment, it is important that we support various “node profiles”, such as standard fullnode, light nodes, indexer nodes, and more.

We hope to encourage community contribution to this project:
- We aim to make roles as modular as possible, so anyone can add their own role that expands the functionality of this automation.
- Anyone can contribute their own playbook that combines these roles in the way that works best for them.
- We're building in the open, check out [the project](todo) and individual [issues](todo).

## Getting Started
We use [Poetry](https://python-poetry.org/docs/#installation) for packaging and dependency management. Install it like this:

```
curl -sSL https://install.python-poetry.org | python3 -
```

Then install dependencies like this:
```
poetry install
```

If you choose not to use the version of Ansible we've specified, note that you need Ansible >= 2.11 and Python >= 3.8.

## Setting up Ansible
There are some manual steps you must do first:

- Provision a machine with Python >= 3.8 on it.
- Ensure you can SSH into the machine as a user with sudo privileges.

## Running Playbooks
You can run a playbook like this:
```
poetry run ansible-playbook -i hosts playbooks/fullnode_from_source.yaml --extra-vars 'git_rev=devnet'
```

There are other ways to define the extra vars, e.g. in your inventory. [See more here](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_variables.html).

We use [role argument validation](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html#role-argument-validation) to ensure that you have passed in the necessary arguments.

