# Ansible Collection - iamgini.wordpress

Collection Name: iamgini.wordpress

## Install this collection:

```shell
$ ansible-galaxy collection install iamgini.wordpress
```

## Install WordPress

Configure variables in `playbooks/vars/wp_install.yaml` (Encrypt the sensitive content as required)

```yaml
web_projects_dir: /var/www/demosite
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
    -i hosts-vagrant \
    -e "wp_debug=true"
```

Passing variables from external file. (For example, using managed database and details are coming from `~/.config/wp-demosite.yaml`)

```shell
$ ansible-playbook playbooks/wordpress_install.yaml \
    -i hosts-upcloud \
    -e @wp-demosite.yaml \
    -e "wp_debug=true"

# or customize the variables
$ ansible-playbook playbooks/wordpress_install.yaml \
    -i hosts-upcloud  \
    -e "wp_debug=true" \
    -e "wordpress_database_server=10.1.10.3" \
    -e "wordpress_domain_name=beta.iamgini.com" \
    -e "wordpress_http_method=https"
```

## Backup WordPress

```shell
$ ansible-playbook playbooks/wordpress_backup.yaml \
    -i hosts-upcloud \
    -e @~/.config/wp-demosite.yaml
```

## Restore WordPress

```shell
$ ansible-playbook playbooks/wordpress_restore.yaml \
    -i hosts-upcloud \
    -e @wp-demosite.yaml
```
