# Развертывание и управление Docker-сервисом с помощью Ansible

Этот Ansible-код развёртывает и управляет сервисом, который работает в Docker-контейнере. С помощью этого кода можно легко изменить версию Docker-образа при деплое.

## Содержание

- [Предварительные требования](#предварительные-требования)
- [Настройка переменных](#настройка-переменных)
- [Получение IP адреса сервера](#получение-ip-адреса-сервера)
- [Настройка Ansible](#настройка-ansible)
- [Запуск Ansible Playbook](#запуск-ansible-playbook)
- [Лицензия](#лицензия)

## Предварительные требования

Перед началом работы убедитесь, что на вашем компьютере установлены следующие инструменты:

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- Доступ к репозиторию с инфраструктурным кодом на [GitHub](https://github.com/filatof/infra.git)

## Настройка переменных

Перед использованием Ansible необходимо задать следующие переменные в плейбуке:

- `repo_url`: URL репозитория с кодом вашего приложения.
- `repo_dest`: Путь, по которому будет клонирован репозиторий на сервере.
- `docker_image_name`: Имя Docker-образа, который будет использоваться.
- `docker_image_version`: Версия Docker-образа.
- `service_name`: Имя сервиса для systemd.

Пример настройки переменных:

```yaml
vars:
  repo_url: "https://github.com/bhavenger/skillbox-diploma.git"
  repo_dest: "/opt/skillbox-diploma"
  docker_image_name: "skillbox/app"
  docker_image_version: "latest"
  service_name: "my-service"  

 ## Получение IP адреса сервера

	1.	Для развертывания инфраструктуры воспользуйтесь репозиторием infra.
	2.	После развертывания инфраструктуры, получите IP-адрес сервера. Это можно сделать через интерфейс Yandex Cloud или используя вывод Terraform.  

   ## Настройка Ansible

	В файле hosts укажите IP-адрес сервера, на котором будет разворачиваться Docker-приложение. Пример файла hosts:
  
   ```ini
   [servers]
   server ansible_host=<IP-адрес вашего сервера>  

   Замените <IP-адрес вашего сервера> на реальный IP-адрес, полученный на предыдущем шаге.  

   Запустите плейбук:

   ```bash
   ansible-playbook -i <your_inventory_file> playbook.yml