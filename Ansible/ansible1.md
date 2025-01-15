# Ansible

> Tecnologia open source que permite aprovisionar sistemas

## Añadir repositorio Ansible

``` cmd
sudo add-apt-repository ppa:ansible/ansible
```

## Actualizar sistema

``` cmd
sudo apt-get update -y
```

## Instalar Ansible

``` cmd
sudo apt install ansible -y
```

## Cambiar dirección ip ubuntu

Primero comprobamos el nombre del archivo de configuración de red:

``` cmd
ls -la /etc/netplan
```

Conociendo el nombre del archivo lo editamos:

``` cmd
sudo nano /etc/netplan/01-network-manager-all.yaml
```