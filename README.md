# System Administration Ansible Playbooks

This is a collection of Ansible playbooks that can be used to automate the System Administration course practicals.

## Disclaimer ⚠️

>This repository is created for **myself** and students who wants to **learn `Ansible`**. 
>I assumes **no responsibility** for any **damage**, any **error**, as well as students who has used this repository for the exam.

## How to

To run the playbook, run the following command:
```shell
ansible-playbook site.yml -i inventory/hosts --ask-vault-pass
```

You can add `-v` to see the output of the playbook. `-i` is the inventory file and `--ask-vault-pass` is to ask for the vault password.

You can use `ansible-vault` to create `vault.yml` file, so you can store sensitive data in it.

## The ansible modules I have used for this repository
- [user](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html)
- [file](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html)
- [template](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/template_module.html)
- [uri](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/uri_module.html)
- [lineinfile](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/lineinfile_module.html)
- [dnf](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)
- [firewalld](https://docs.ansible.com/ansible/latest/collections/ansible/posix/firewalld_module.html)
- [systemd](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/systemd_module.html)
- [copy](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html)
- [sysctl](https://docs.ansible.com/ansible/latest/collections/ansible/posix/sysctl_module.html)
- [yum](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/yum_module.html)
- [blockinfile](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/blockinfile_module.html)
- [set_fact](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/set_fact_module.html)
- [service](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/service_module.html)
- [reboot](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/reboot_module.html)
- [pip](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/pip_module.html)
- [seboolean](https://docs.ansible.com/ansible/latest/collections/ansible/posix/seboolean_module.html)
- [mysql_user](https://docs.ansible.com/ansible/latest/collections/community/mysql/mysql_user_module.html)
- [mysql_db](https://docs.ansible.com/ansible/latest/collections/community/mysql/mysql_db_module.html)
- [get_url](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/get_url_module.html)
- [unarchive](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/unarchive_module.html)
- [shell](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/shell_module.html)
- [sefcontext](https://docs.ansible.com/ansible/latest/collections/community/general/sefcontext_module.html)

> You might need to run `ansible-galaxy collection install ansible.posix` to install the module in `posix`.
> You might need to run `ansible-galaxy collection install community.mysql` to install the module in `mysql`.
> You might need to run `ansible-galaxy collection install community.general` to install the module in `general`.

## Playbooks

```text
sys-admin-ansible
├── README.md
├── inventory
│   └── hosts
├── roles
│   ├── apache
│   │   ├── files
│   │   │   ├── proxy.service
│   │   │   └── website.py
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       ├── forensic.j2
│   │       ├── index.j2
│   │       ├── virtualhosthttp.j2
│   │       ├── virtualhostproxy.j2
│   │       └── virtualhostword.j2
│   ├── dns
│   │   ├── files
│   │   │   ├── 70-ipv6.conf
│   │   │   └── named.conf
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       ├── hostname.j2
│   │       ├── hosts.j2
│   │       ├── resolv.j2
│   │       ├── reverse.j2
│   │       └── zonefile.j2
│   └── etais
│       ├── tasks
│       │   └── main.yml
│       └── templates
│           └── resolv.j2
├── site.yml
├── sys-admin-ansible.iml
└── vault.yml
```

