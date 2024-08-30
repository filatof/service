# Ansible для развёртывания сервиса

## Описание

Этот Ansible-код развёртывает и управляет сервисом, который работает в Docker-контейнере. С помощью этого кода можно легко изменить версию Docker-образа при деплое.

## Использование

1. Убедитесь, что у вас установлен Ansible.
2. Отредактируйте `playbook.yml`, чтобы указать имя вашего сервиса, Docker-образа и нужную версию.  
    repo_dest: /opt/skillbox-diploma   # Директория куда скачается репозиторий  
    docker_image_name: "skillbox/app"  # Название имиджа  
    docker_image_version: "latest"     # Здесь указываем версию  
    service_name: "my-service"         # Название сервиса  
3. Запустите плейбук:

   ```bash
   ansible-playbook -i <your_inventory_file> playbook.yml