# Aptos Ansible

## Getting started
We use [Poetry](https://python-poetry.org/docs/#installation) for packaging and dependency management. Install it like this:

```
curl -sSL https://install.python-poetry.org | python3 -
```

Then install dependencies like this:
```
poetry install
```

## Setting up Ansible
There are some manual steps you must do first:
- Ensure can SSH into the machine as a user with sudo privileges.

## Configuration
todo talk about how to piece together a super playbook that does what you want

```
poetry run ansible-playbook -i hosts playbooks/source_deps.yaml
```

