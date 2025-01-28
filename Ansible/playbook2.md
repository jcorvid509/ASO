# Caso práctio despliegue Ansible

Creamos la carpeta `ansible` en `~`

```bash
mkdir ~/ansible
```

Entramos en ella y creamos el directorio `nginx`

```bash
cd ~/ansible
mkdir nginx
```

Creamos la siguiente estructura de carpetas

```
main.yml
inventory/
    hosts
group_vars/
    all
roles/
    common/
        tasks/
        handlers/
        files/
        templates/
        vars/
        defaults/
        meta/
    webservers/
        tasks/
        defaults
```

## Creamos el directorio `inventory`

```bash
mkdir inventory
nano inventory/hosts.ini   # definimos los servidores que vamos a configurar
```

dentro de `hosts.ini`

```ini
[webservers]
10.0.0.1
```

## Creamos el archivo `main.yml`

Dentro del directorio `nginx` creamos el archivo `main.yml`

```bash
nano main.yml
```

```yml
---
# nginx playbook

- hosts: webservers
  remote_user: "root"
  roles:
  - role: nginx_install
```

# Creamos el fichero de `roles`

```bash
mkdir roles
```

dentro de `roles`, creamos el fichero `nginx_install`

```bash
mkdir roles/nginx_install
```

dentro de la carpeta `nginx_install` creamos el directio `tasks`

```bash
mkdir roles/nginx_install/tasks
```

y el archivo `/main.yml`, este archivo contiene las tareas a realizar en el rol

```bash
nano roles/nginx_install/tasks/main.yml
```

```yml
---
# install nginx

- name: Update
  apt:
    name: "*"
    state: lastest

- name: Install nginx
  apt:
    name: "nginx"
    state: present

- name: Start and enable service nginx
  systemd:
    name: "nginx"
    state: started
    enabled: yes
```