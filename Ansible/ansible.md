# Despliegues con Ansible

## Índice
- [Despliegues con Ansible](#despliegues-con-ansible)
  - [Índice](#índice)
  - [Introducción](#introducción)
    - [Instalación de Ansible](#instalación-de-ansible)
  - [Playbooks](#playbooks)
  - [Creación de un playbook](#creación-de-un-playbook)
  - [Apendices no explicados en el curso](#apendices-no-explicados-en-el-curso)
    - [Como habilitar el ssh en ubuntu](#como-habilitar-el-ssh-en-ubuntu)
    - [Fallo al conectar con ssh](#fallo-al-conectar-con-ssh)

## Introducción

Ansible es una herramienta de automatización de sistemas de código abierto que permite a los administradores de sistemas y desarrolladores automatizar la configuración y el despliegue de aplicaciones y servicios en entornos de TI.

Ansible utiliza un modelo de configuración basado en **playbooks**, que son archivos de texto que describen las acciones que se deben realizar en un sistema o grupo de sistemas.

No necesita instalar agentes en los sistemas que se van a gestionar, lo que lo hace una herramienta muy ligera y fácil de usar.

### Instalación de Ansible

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

## Playbooks

## Creación de un playbook

## Apendices no explicados en el curso

### [Como habilitar el ssh en ubuntu](https://es.dade2.net/como-habilitar-el-servidor-ssh-en-ubuntu-22-04/)

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