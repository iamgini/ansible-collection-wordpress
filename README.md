# Ansible Collection - iamgini.wordpress

Collection Name: iamgini.wordpress

## Install this collection:

```shell
$ ansible-galaxy collection install iamgini.wordpress
```

## Install WordPress

Configure variables in `playbooks/vars/wp_install.yaml` (Encrypt the sensitive content as required)

```yaml
wordpress_project_dir: /var/www/demosite
wordpress_site_name: demosite
wordpress_domain_name: beta.iamgini.com

wordpress_database_server: your-database-host
wordpress_database_port: 3306
wordpress_database_name: wp_demosite
wordpress_database_username: dbuser
wordpress_database_password: password

wordpress_version: 6.4
```

```shell
$ ansible-playbook playbooks/wordpress_install.yaml \
    -i hosts-upcloud \
    -e @~/.config/wp-demosite.yaml
```