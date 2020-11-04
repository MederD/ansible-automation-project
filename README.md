# Ansible-automation-project

Automation with ansible of sample LAMP installation &amp; configuration for "kodekloudhub/learning-app-ecommerce"


# Introduction

This is automation with ansible of a sample e-commerce application built for learning purposes forked from [kodekloudhub/learning-app-ecommerce](https://github.com/kodekloudhub/learning-app-ecommerce).

Here's how to deploy it on CentOS systems with Docker containers:


## Deploy Pre-Requisites

1. Install Docker with systemd. I used "centos/systemd" image and build my own with a little modifications by enabling ssh, then run it:

```
sudo docker run --privileged --name < target_node_name > --hostname < target_node_hostname > -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p < example_port >:22 -d  < modified_image_name >

```

2. Install ansible on control node.

```
sudo yum install -y ansible

```
## Creating inventory and playbook files.

1. Create inventory file.
```
sudo touch inventory.txt
sudo vi inventory.txt

    < target_node_name > ansible_host=< target_node_ip > ansible_connection=ssh ansible_user=< user_name > ansible_ssh_pass= < user_password >
    
```

2. Create playbook file.

```
sudo touch < playbook_name >.yaml
sudo vi < playbook_name >.yaml

```

## Run ansible playbook.

```
ansible-playbook < playbook_name > -i inventory.txt

```

## Check deployments on target node.

1. SSH to target node to check automation.
```
sudo systemctl status httpd.service
sudo systemctl status mariadb.service

curl http://localhost
    
```

