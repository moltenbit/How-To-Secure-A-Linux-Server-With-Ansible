# How To Secure A Linux Server With Ansible
Ansible playbooks of ["How To Secure A Linux Server"](https://github.com/imthenachoman/How-To-Secure-A-Linux-Server).

These Ansible playbooks are made to help install secure Linux servers faster.

## How to get started
1. Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
2. git-clone this repository
3. [Create SSH-Public/Private-Keys](https://github.com/imthenachoman/How-To-Secure-A-Linux-Server#ssh-publicprivate-keys)
  ```
  ssh-keygen -t ed25519
  ```
   
5. Change all variables in *group_vars/variables.yml* according to your needs.
6. Enable SSH root access before running the playbooks:
   
  ```
  nano /etc/ssh/sshd_config
  [...]
  PermitRootLogin yes
  [...]
  ```

7. Recommended: configure static IP address on your system.
8. Add your systems IP address to *hosts.yml*.

&nbsp;

Run the requirements playbook:

    ansible-playbook --inventory hosts.yml --ask-pass requirements-playbook.yml

&nbsp;

Run the main playbook:

    ansible-playbook --inventory hosts.yml --ask-pass main-playbook.yml

&nbsp;

If you need to run the playbooks multiple times remember to use the SSH key and the new SSH port:

    ansible-playbook --inventory hosts.yml -e ansible_ssh_port=SSH_PORT --key-file /PATH/TO/SSH/KEY main-playbook.yml

&nbsp;

Tested on Debian 12 Bookworm.

## Configurations
WIP

## Plans / ToDos
- [ ] use Ansible vault to securely store secrets

## Warning!
Read all tasks carefully and make sure they do not break your system before using these playbooks! Do not rely solely on the Ansible playbooks for security! It is your responsibility to make sure all settings you need have been set and are working. This is just a starting point! Depending on your needs and goals make sure to further secure your system.

## Credits
- [imthenachoman](https://github.com/imthenachoman) for creating the great [How To Secure A Linux Server](https://github.com/imthenachoman/How-To-Secure-A-Linux-Server) guide
- [Neo23x0](https://github.com/Neo23x0) for the auditd best practice rules
