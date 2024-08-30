# Ansible для развёртывания сервиса

## Описание

Этот Ansible-код развёртывает и управляет сервисом, который работает в Docker-контейнере. С помощью этого кода можно легко изменить версию Docker-образа при деплое.

## Использование

1. Убедитесь, что у вас установлен Ansible.
2. Отредактируйте `playbook.yml`, чтобы указать имя вашего сервиса, Docker-образа и нужную версию.  
    _repo_dest: /opt/skillbox-diploma_   # Директория куда скачается репозиторий  
    _docker_image_name: "skillbox/app"_  # Название имиджа  
    _docker_image_version: "latest"_     # Здесь указываем версию  
    _service_name: "my-service"_         # Название сервиса  
3. Запустите плейбук:

   ```bash
   ansible-playbook -i <your_inventory_file> playbook.yml