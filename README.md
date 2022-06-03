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
- [meta](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/meta_module.html)
- [pear](https://docs.ansible.com/ansible/latest/collections/community/general/pear_module.html)
- [docker_image](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_image_module.html)
- [docker_container](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_container_module.html)
- [docker_network](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_network_module.html)
- [k8s](https://docs.ansible.com/ansible/latest/collections/kubernetes/core/k8s_module.html)
- [waldur_marketplace_os_instance](https://github.com/waldur/ansible-waldur-module/blob/develop/waldur_marketplace_os_instance.py)
- [waldur_marketplace_os_get_instance](https://github.com/waldur/ansible-waldur-module/blob/develop/waldur_marketplace_os_get_instance.py)

> You might need to run `ansible-galaxy collection install ansible.posix` to install the module in `posix`.
>
> You might need to run `ansible-galaxy collection install community.mysql` to install the module in `mysql`.
>
> You might need to run `ansible-galaxy collection install community.general` to install the module in `general`.
>
> You might need to run `ansible-galaxy collection install community.docker` to install the module in `docker`.
>
> You might need to run following command to install the module in `kubernetes`:
> ```shell
> ansible-galaxy collection install community.kubernetes
> ansible-galaxy collection install cloud.common
> ansible-galaxy collection install kubernetes.core
> ```
>
> For ansible-waldur-module please refer to the [ansible-waldur-module](https://github.com/waldur/ansible-waldur-module) repository.
> 
> It might be helpful for you to install ansible-waldur-module into user modules.
> 
> You might need to change `/.local/lib/python3.8/site-packages/` to your `python-packages` directory.
> ```shell
> pip install ansible-waldur-module
> mkdir -p /home/$USER/.ansible/plugins/modules
> cp -r /home/$USER/.local/lib/python3.8/site-packages/waldur* /home/$USER/.ansible/plugins/modules
> ```
> 
>> Deep note: I'm not that much good at `python-packages` so the commands above might not work for you.
> 


## Playbooks

```text
sys-admin-ansible
├── README.md
├── inventory
│   └── hosts
├── roles
│   ├── apache
│   │   ├── files
│   │   │   ├── modsecurity_localrules.conf
│   │   │   ├── php-fpm.conf
│   │   │   ├── proxy.service
│   │   │   ├── website.py
│   │   │   └── www.conf
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
│   ├── container
│   │   ├── files
│   │   │   ├── Dockerfile
│   │   │   └── server.py
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       └── virtualhostproxy.j2
│   ├── devops
│   │   ├── files
│   │   │   └── traefik.toml
│   │   ├── handlers
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yml
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
│   ├── docker
│   │   ├── files
│   │   │   └── daemon.json
│   │   └── tasks
│   │       └── main.yml
│   ├── email
│   │   ├── files
│   │   │   ├── 10-auth.conf
│   │   │   ├── 10-logging.conf
│   │   │   ├── 10-mail.conf
│   │   │   ├── 10-master.conf
│   │   │   ├── 10-ssl.conf
│   │   │   ├── 15-mailboxes.conf
│   │   │   ├── dovecot.conf
│   │   │   └── master.cf
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       ├── config.inc.php.j2
│   │       ├── main.cf.j2
│   │       └── virtualhostmail.j2
│   ├── etais
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       └── resolv.j2
│   ├── fs
│   │   ├── files
│   │   │   └── smb.conf
│   │   ├── handlers
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yml
│   ├── k8s
│   │   └── tasks
│   │       └── main.yml
│   ├── kubernetes
│   │   ├── files
│   │   │   ├── kubernetes.repo
│   │   │   └── traefik-config.yaml
│   │   ├── handlers
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yml
│   └── tls
│       ├── files
│       │   ├── 10-ssl.conf
│       │   ├── ca.crt
│       │   ├── cert.crt
│       │   ├── key.key
│       │   └── master.cf
│       ├── handlers
│       │   └── main.yml
│       ├── tasks
│       │   └── main.yml
│       └── templates
│           ├── main.cf.j2
│           ├── virtualhosthttp.j2
│           ├── virtualhostproxy.j2
│           └── virtualhostword.j2
├── site.yml
├── sys-admin-ansible.iml
├── sys-admin-labs.yml
├── templates
│   └── hosts.j2
├── vars.yml
├── vault.yml
├── waldur-create-vm.yml
└── waldur-delete-vm.yml

48 directories, 75 files
```
