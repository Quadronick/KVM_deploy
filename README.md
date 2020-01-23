Personal KVM services
=====================

This repo contains two Ansible roles at the moment.

First one build 3proxy (https://github.com/z3APA3A/3proxy) service and save it as ~5Mb alpine docker image.  
Another is for bootstrapping purposes on Arch Linux OS.

You may found useful Jenkinsfiles, which are located in 'ci' directory in every role base directory.  

Playbooks usage example:  

    ansible-playbook 3proxy.yml -i ./inventory/kvm.env -e ns_server_1=77.88.8.8 -e ns_server_2=77.88.8.1 -e username=user -e userpass=reallygoodpassword -e CLEANUP=true
