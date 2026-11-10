# Ansible server configuration

Playbook устанавливает Docker и Docker Compose на виртуальную машину Ubuntu 24.04 в Yandex Cloud и включает службу Docker.

## Требования

На управляющей машине установите Ansible. На ней также должен находиться SSH-ключ, публичная часть которого добавлена на ВМ.

## Запуск

Скопируйте `inventory.ini.example` в `inventory.ini` и замените `VM_PUBLIC_IP` на публичный IP виртуальной машины.

Проверьте SSH-подключение командой `ansible -i inventory.ini web -m ping`.

Примените playbook командой `ansible-playbook -i inventory.ini site.yml`.

Проверка Docker: `ansible -i inventory.ini web -b -a "docker version"`. Тестовый контейнер: `ansible -i inventory.ini web -b -a "docker run --rm hello-world"`.

Локальный `inventory.ini` исключён из Git. Не добавляйте в репозиторий приватные SSH-ключи.
