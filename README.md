# Ansible Collection - iamgini.wordpress

Collection Name: iamgini.wordpress

## Install this collection:

```shell
$ ansible-galaxy collection install iamgini.wordpress
```

## Install WordPress

```shell
$ ansible-playbook playbooks/wordpress_install.yaml \
    -i hosts-upcloud \
    -e @~/.config/wp-demosite.yaml
```