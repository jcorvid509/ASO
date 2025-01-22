![](https://github.com/jcorvid509/.resGen/blob/main/_bannerD.png#gh-dark-mode-only)
![](https://github.com/jcorvid509/.resGen/blob/main/_bannerL.png#gh-light-mode-only)

<a href="/README.md"><img src="https://github.com/jcorvid509/.resGen/blob/main/_home.svg" width="30"></a>

# Despliegues con Ansible

## Índice
- [Despliegues con Ansible](#despliegues-con-ansible)
  - [Índice](#índice)
  - [Introducción](#introducción)
  - [Requisitos previos](#requisitos-previos)
  - [Instalación de Ansible](#instalación-de-ansible)
    - [Creación de Maquinas Virtuales en Porxmox](#creación-de-maquinas-virtuales-en-porxmox)
    - [Nodo de Control de Ansible](#nodo-de-control-de-ansible)
      - [**Usuario no Root Sudo**](#usuario-no-root-sudo)
      - [**Claves SSH**](#claves-ssh)
      - [**Hosts de Ansible**](#hosts-de-ansible)
  - [Recursos](#recursos)

## Introducción

Ansible es una herramienta de automatización de sistemas de código abierto que permite a los administradores de sistemas y desarrolladores automatizar la configuración y el despliegue de aplicaciones y servicios en entornos de TI.

Ansible utiliza un modelo de configuración basado en [playbooks](#playbooks), que son archivos de texto que describen las acciones que se deben realizar en un sistema o grupo de sistemas.

No necesita instalar agentes en los sistemas que se van a gestionar, lo que lo hace una herramienta muy ligera y fácil de usar.

## Requisitos previos

Antes de instalar ansible, deberemos de tener lo siguiente:

- [Despliegues con Ansible](#despliegues-con-ansible)
  - [Índice](#índice)
  - [Introducción](#introducción)
  - [Requisitos previos](#requisitos-previos)
  - [Instalación de Ansible](#instalación-de-ansible)
    - [Creación de Maquinas Virtuales en Porxmox](#creación-de-maquinas-virtuales-en-porxmox)
    - [Nodo de Control de Ansible](#nodo-de-control-de-ansible)
      - [**Usuario no Root Sudo**](#usuario-no-root-sudo)
      - [**Claves SSH**](#claves-ssh)
      - [**Hosts de Ansible**](#hosts-de-ansible)
  - [Recursos](#recursos)

## Instalación de Ansible

Para instalar Ansible, necesitamos tener dos equipos o maquinas configuradas de la siguiente manera:
- Una como [Nodo de Control](#nodo-de-control-de-ansible), desde el cual accederemos al host.
- Otra como [Host](#hosts-de-ansible),que se configurará con Ansible.

### Creación de Maquinas Virtuales en Porxmox

En nuestro caso, crearemos dos maquinas virtuales en Porxmox, una para el [Nodo de Control](#nodo-de-control-de-ansible) y otra para el [Host](#hosts-de-ansible).

Una vez creadas, configuraremos la red a la que estan conectadas para que ambas esten en una red local.

| nombre | dirección IP | Puerta de enlace |
| -- | -- | -- |
| Host de Ansible | 10.0.0.1 | 10.0.0.1 |
| Nodo de Control | 10.0.0.2 | 10.0.0.1 |

Tras esto, comprobaremos que ambas maquinas sean visibles entre ellas.

- Host de Ansible

```bash
$ ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.966 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.487 ms
```

- Nodo de Control

```bash
$ ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=0.503 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=0.438 ms
```

### Nodo de Control de Ansible
---

El nodo de control, será usada para conectar a los [Hosts de Ansible](#hosts-de-ansible), y controlarlos a traves de `ssh`.

Este **Nodo de Control**, debe contener lo siguiente:

#### **Usuario no Root Sudo**
---

Para crear un nuevo usuario con permisos de sudo, ejecutaremos el siguiente comando:

```bash
$ sudo adduser noroot
```

```bash
Añadiendo el usuario `noroot' ...
Añadiendo el nuevo grupo `noroot' (1001) ...
Añadiendo el nuevo usuario `noroot' (1001) con grupo `noroot' ...
Creando el directorio personal `/home/noroot' ...
Copiando los ficheros desde `/etc/skel' ...
Nueva contraseña:
CONTRASEÑA INCORRECTA: La contraseña tiene menos de 8 caracteres
Vuelva a escribir la nueva contraseña:
passwd: contraseña actualizada correctamente
Cambiando la información de usuario para noroot
Introduzca el nuevo valor, o presione INTRO para el predeterminado
        Nombre completo []:
        Número de habitación []:
        Teléfono del trabajo []:
        Teléfono de casa []:
        Otro []:
¿Es correcta la información? [S/n] s
```

hola

#### **Claves SSH**
---

hola

#### **Hosts de Ansible**
---

hola

## Recursos

[Instalar Ansible](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-20-04-es)

[Configuración Servidor](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04-es)


<!-- ## Generación de claves ssh

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

### [Habilitar ssh](https://es.dade2.net/como-habilitar-el-servidor-ssh-en-ubuntu-22-04/) -->