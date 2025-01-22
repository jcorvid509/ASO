# Despliegues con Ansible

## Índice
- [Despliegues con Ansible](#despliegues-con-ansible)
  - [Índice](#índice)
  - [Introducción](#introducción)
  - [Requisitos previos](#requisitos-previos)
  - [Nodo de Control de Ansible](#nodo-de-control-de-ansible)
    - [Usuario no Root Sudo](#usuario-no-root-sudo)
    - [Claves SSH](#claves-ssh)
  - [Hosts de Ansible](#hosts-de-ansible)
  - [Generación de claves ssh](#generación-de-claves-ssh)
  - [Instalación de Ansible](#instalación-de-ansible)
  - [Playbooks](#playbooks)
  - [Creación de un playbook](#creación-de-un-playbook)
  - [Apendices no explicados en el curso](#apendices-no-explicados-en-el-curso)
    - [Como habilitar el ssh en ubuntu](#como-habilitar-el-ssh-en-ubuntu)
    - [Fallo al conectar con ssh](#fallo-al-conectar-con-ssh)
  - [Recursos](#recursos)
    - [Intalar Ansible](#intalar-ansible)
    - [Habilitar ssh](#habilitar-ssh)

## Introducción

Ansible es una herramienta de automatización de sistemas de código abierto que permite a los administradores de sistemas y desarrolladores automatizar la configuración y el despliegue de aplicaciones y servicios en entornos de TI.

Ansible utiliza un modelo de configuración basado en [playbooks](#playbooks), que son archivos de texto que describen las acciones que se deben realizar en un sistema o grupo de sistemas.

No necesita instalar agentes en los sistemas que se van a gestionar, lo que lo hace una herramienta muy ligera y fácil de usar.

## Requisitos previos

Antes de instalar ansible, deberemos de tener lo siguiente:

- [Nodo de control de Ansible](#nodo-de-control-de-ansible)
  - [Un usuario no root con privilegios sudo](#usuario-no-root-sudo)
  - [Un par de claves `ssh`](#claves-ssh)
- `Hosts de Ansible`
  - Clave pública `ssh` del nodo de control de Ansible

## Nodo de Control de Ansible

Maquina usada para conectar a los [Hosts de Ansible](#hosts-de-ansible), y controlarlos a traves de `ssh`.

Este **Nodo de Control**, debe contener lo siguiente:

### Usuario no Root Sudo

### Claves SSH

## Hosts de Ansible


------------
------------
## Generación de claves ssh

Para instalar Ansible en Ubuntu primero debemos de generar un par de claves `ssh`:

``` cmd
ssh-keygen -t rsa -b 4096
```

Con esto crearíamos nuestra clave `ssh`, ahora debemos de copiar la clave pública a la máquina que queremos gestionar:

Antes, debemos realizar los pasos que se describen en el siguiente: [->](#como-habilitar-el-ssh-en-ubuntu)

``` cmd
ssh-copy-id -i ~/.ssh/id_rsa.pub usuario@10.0.0.2
```

`~/.ssh/ide_rsa.pub` es la ruta a la clave pública generada anteriormente.

`usuario@10.0.0.2` es el usuario y dirección IP del nodo remoto.

Esto copiará la clave pública a la máquina remota y la agregará a la lista de claves autorizadas.

## Instalación de Ansible

## Playbooks

## Creación de un playbook

## Apendices no explicados en el curso

### [Como habilitar el ssh en ubuntu](#habilitar-ssh)

Primero deberemos activar el ssh en el servidor al que queremos conectarnos:

Instalamos el ssh en el servidor:

``` cmd
sudo apt-get update
```

``` cmd
sudo apt-get install openssh-server
```

Comprobamos que el servicio ssh se encuentre activo:

``` cmd
sudo systemctl status ssh
```

Por último, debemos permitir el puerto ssh para usuarios remostos, para ello:

``` cmd
sudo ufw allow 22/tcp
```

### Fallo al conectar con ssh

## Recursos

### [Intalar Ansible](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-20-04-es)

### [Habilitar ssh](https://es.dade2.net/como-habilitar-el-servidor-ssh-en-ubuntu-22-04/)