![](https://github.com/jcorvid509/.resGen/blob/main/_bannerD.png#gh-dark-mode-only)
![](https://github.com/jcorvid509/.resGen/blob/main/_bannerL.png#gh-light-mode-only)

<a href="/README.md"><img src="https://github.com/jcorvid509/.resGen/blob/main/_home.svg" width="30"></a>

---

## [Introducción a Ansible](/Ansible/1.ansible.md)

## [Playbooks](Ansible/2.playbook.md)

## [Despliegue Ansible](Ansible/3.despliegue.md)

## [Valores](Ansible/4.tests.md)

# Despliegues con Ansible

- 📁 [ansible](3.despliegue.md#ansible)
  - 📁 [nginx](3.despliegue.md#nginx)
    - 📁 [goup_vars](4.tests.md#group_vars)
      - 📄 [all](4.tests.md#all)
    - 📁 [inventory](3.despliegue.md#inventory)
      - 📄 [hosts.ini](3.despliegue.md#hostsini)
    - 📄 [main.yml](3.despliegue.md#mainyml)
    - 📁 [roles](3.despliegue.md#roles)
      - 📁 [nginx_install](3.despliegue.md#nginx_install)
        - 📁 [tasks](3.despliegue.md#tasks)
          - 📄 [main.yml](3.despliegue.md#mainyml-1)
      - 📁 [register_var](4.tests.md#register_vartasksmainyml)
        - 📁 tasks
          - 📄 main.yml
      - 📁 [conditions](4.tests.md#conditionstasksmainyml)
        - 📁 tasks
          - 📄 main.yml
      - 📁 [fail_force](4.tests.md#fail_forcetasksmainyml)
        - 📁 tasks
          - 📄 main.yml
      - 📁 [ignore_errors](4.tests.md#ignore_errorstasksmainyml)
        - 📁 tasks
          - 📄 main.yml
      - 📁 [template_var](4.tests.md#template_vartasksmainyml)
        - 📁 tasks
          - 📄 main.yml
        - 📁 templates
          - 📄 index.html.j2
      - 📁 [template_var](4.tests.md#template_bucletasksmainyml)
        - 📁 tasks
          - 📄 main.yml
        - 📁 templates
          - 📄 index.html.j2
