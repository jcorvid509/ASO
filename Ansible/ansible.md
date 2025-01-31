![](https://github.com/jcorvid509/.resGen/blob/main/_bannerD.png#gh-dark-mode-only)
![](https://github.com/jcorvid509/.resGen/blob/main/_bannerL.png#gh-light-mode-only)

<a href="/README.md"><img src="https://github.com/jcorvid509/.resGen/blob/main/_home.svg" width="30"></a>

# Despliegues con Ansible

## Índice

- [Despliegues con Ansible](#despliegues-con-ansible)
  - [Índice](#índice)
  - [Introducción](#introducción)
  - [Requisitos previos](#requisitos-previos)
  - [Creación de Maquinas Virtuales en Porxmox](#creación-de-maquinas-virtuales-en-porxmox)
  - [Configuración Previa](#configuración-previa)
  - [Instalación de Ansible](#instalación-de-ansible)
  - [Secure Shell (ssh)](#secure-shell-ssh)

## Introducción

Ansible es una herramienta de automatización de sistemas de código abierto que permite a los administradores de sistemas y desarrolladores automatizar la configuración y el despliegue de aplicaciones y servicios en entornos de TI.

Ansible utiliza un modelo de configuración basado en [playbooks](#playbooks), que son archivos de texto que describen las acciones que se deben realizar en un sistema o grupo de sistemas.

No necesita instalar agentes en los sistemas que se van a gestionar, lo que lo hace una herramienta muy ligera y fácil de usar.

## Requisitos previos

Antes de instalar ansible, deberemos de tener lo siguiente:

- Una como Nodo de Control, desde el cual accederemos al host.
- Otra como Host, el cual se configurará con Ansible.

## Creación de Maquinas Virtuales en Porxmox

En nuestro caso, crearemos dos maquinas virtuales en Porxmox, una para el [Nodo de Control](#nodo-de-control-de-ansible) y otra para el [Host](#hosts-de-ansible).

Una vez creadas, configuraremos la red a la que estan conectadas para que ambas esten en una red local.

| nombre | dirección IP | Puerta de enlace |
| -- | -- | -- |
| _@ansibleHost | 10.0.0.1 | 10.0.0.1 |
| _@ansibleNodo | 10.0.0.2 | 10.0.0.1 |

Tras esto, comprobaremos que ambas maquinas sean visibles entre ellas.

- Host de Ansible

```bash
usuario@ansibleNodo:~$ ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.966 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.487 ms
```

- Nodo de Control

```bash
usuario@ansibleNodo:~$ ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=0.503 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=0.438 ms
```

## Configuración Previa

A partir de ahora entraremos como usuario `root` en ambas maquinas.

```bash
sudo su
```

## Instalación de Ansible


## Secure Shell (ssh) 

```bash
nano /etc/ssh/sshd_config
```

![alt text](image.png)

Una vez cambiada la contraseña y modificado el archivo `sshd_config`, reiniciamos el servicio de `ssh`.

```bash
systemctl restart sshd
```

