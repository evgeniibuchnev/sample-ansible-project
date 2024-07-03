# Sample Ansible Project

Welcome to the **Sample Ansible Project** repository. This project provides a basic folder and file structure to quickly get you started with Ansible.

## Getting Started

To get started with this project, follow these steps:

1. Star the repo, so you never need to find it again :)
1. You may share with friends - how to easy it's to have sample ansible project structure :)
2. Clone the repository:
```sh
git clone https://github.com/evgeniibuchnev/sample-ansible-project.git
cd sample-ansible-project
# rm -rf ./.git # Remove GIT folder, so you can start your GIT journey

# Once you sorted your inventory and passwordless access to your hosts, you may check with ping module
ansible all -m ping

host1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
host2 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}

# This is a playbook run
ansible-playbook ./playbooks/test-variables.yml

PLAY [Testing variables in playbook] **********************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ************************************************************************************************************************************************************************************************************************************************************
ok: [host1]
ok: [host2]

TASK [Print custom group and host variable] ***************************************************************************************************************************************************************************************************************************************
ok: [host1] => {
    "msg": [
        "Group variable: sample_group_value",
        "Host variable: This is Host One"
    ]
}
ok: [host2] => {
    "msg": [
        "Group variable: sample_group_value",
        "Host variable: This is Host Two"
    ]
}

PLAY RECAP ************************************************************************************************************************************************************************************************************************************************************************
host1                      : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
host2                      : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

## Project Structure

The following is the structure of the project:
```
    .
    ├── LICENSE
    ├── README.md
    ├── ansible.cfg
    ├── filter_plugins
    │   └── README.md
    ├── inventory
    │   ├── dev
    │   │   ├── 01-static
    │   │   ├── group_vars
    │   │   │   └── all
    │   │   │       └── vars.yml
    │   │   └── host_vars
    │   │       ├── host1
    │   │       │   └── vars.yml
    │   │       └── host2
    │   │           └── vars.yml
    │   ├── prod
    │   │   ├── 01-static
    │   │   ├── group_vars
    │   │   │   └── all
    │   │   │       └── vars.yml
    │   │   └── host_vars
    │   │       ├── host1
    │   │       │   └── vars.yml
    │   │       └── host2
    │   │           └── vars.yml
    │   └── stag
    │       ├── 01-static
    │       ├── group_vars
    │       │   └── all
    │       │       └── vars.yml
    │       └── host_vars
    │           ├── host1
    │           │   └── vars.yml
    │           └── host2
    │               └── vars.yml
    ├── library
    │   └── README.md
    ├── module_utils
    │   └── README.md
    ├── playbooks
    │   ├── test-role-variables.yml
    │   └── test-variables.yml
    ├── roles
    │   └── role1
    │       ├── defaults
    │       │   └── main.yml
    │       ├── files
    │       │   └── test_file.txt
    │       ├── handlers
    │       │   └── main.yml
    │       ├── library
    │       ├── lookup_plugins
    │       ├── meta
    │       │   └── main.yml
    │       ├── module_utils
    │       ├── tasks
    │       │   └── main.yml
    │       ├── templates
    │       │   └── sample.conf.j2
    │       └── vars
    │           └── main.yml
    ├── sample_ansible_project.sh
    └── tasks
        └── webservers-extra.yml
```

## Detailed Explanation

- **ansible.cfg**: Ansible configuration file to define paths to roles, inventory files, and other configurations.

- **filter_plugins**: Directory for custom filter plugins.

- **inventory**: Directory for inventory files that define hosts and groups for different environments.
  - **dev**, **prod**, **stag**: Directories for development, production, and staging environments.
    - **01-static**: Static inventory file for each environment.
    - **group_vars**: Directory for group variables.
      - **all/vars.yml**: Variables applied to all hosts in the environment.
    - **host_vars**: Directory for host-specific variables.
      - **host1/vars.yml**, **host2/vars.yml**: Variables for specific hosts.

- **library**: Directory for custom Ansible modules.

- **module_utils**: Directory for custom module utilities.

- **playbooks**: Directory for playbooks.
  - **test-role-variables.yml**: Playbook to test role variables.
  - **test-variables.yml**: Playbook to test general variables.

- **roles**: Directory for Ansible roles.
  - **role1**: Sample role directory.
    - **defaults/main.yml**: Default variables for the role.
    - **files/test_file.txt**: Static files used by the role.
    - **handlers/main.yml**: Handlers triggered by tasks.
    - **library**: Directory for custom modules specific to the role.
    - **lookup_plugins**: Directory for custom lookup plugins.
    - **meta/main.yml**: Metadata about the role, such as dependencies.
    - **module_utils**: Directory for module utilities specific to the role.
    - **tasks/main.yml**: Main list of tasks to be executed by the role.
    - **templates/sample.conf.j2**: Jinja2 templates used by tasks.
    - **vars/main.yml**: Variables specific to the role.

- **tasks**: Directory for additional task files.
  - **webservers-extra.yml**: Additional tasks related to web servers.

This structure helps to organize and manage the various components of an Ansible project, making it easy to scale and maintain. Each directory and file serves a specific purpose, ensuring a clear separation of concerns and better modularity.

