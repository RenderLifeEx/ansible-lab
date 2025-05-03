# Ansible Lab: Node.js Web Server Automation 🚀

![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)

Репозиторий с Ansible-плейбуками для автоматизации развертывания Node.js веб-серверов с полным стеком инструментов.

## 🌟 Основные возможности

- **Автоматическая установка** всего стека для Node.js-разработки
- **Гибкая настройка** окружения под разные проекты
- **Готовые конфиги** для быстрого развертывания

## 🛠️ Устанавливаемые компоненты

| Компонент       | Назначение                          |
|-----------------|-------------------------------------|
| **Node.js**     | Основная среда выполнения (через NVM) |
| **PM2**         | Процесс-менеджер для Node.js        |
| **Docker**      | Контейнеризация приложений          |
| **Nginx**       | Обратный прокси и балансировщик     |
| **NVM**         | Управление версиями Node.js         |

## 📂 Структура репозитория

```bash
ansible-lab/
├── playbooks/
│ ├── base-setup.yml # Базовое окружение
│ ├── lite-setup.yml # Только нода и ...
│ ├── nodejs-setup.yml # Установка Node.js + NVM
│ ├── pm2-setup.yml # Настройка PM2
│ └── docker-setup.yml # Установка Docker
├── templates/
│ ├── nginx/ # Шаблоны Nginx
│ │ └── site.conf.j2 # Для сайтов
├── inventory/ # Файлы инвентаризации
│ ├── production # Для рабочих серверов
│ └── staging # Для тестовых сред
└── vars/ # Переменные
├── common.yml # Общие настройки
└── node_versions.yml # Версии Node.js
```

## 🚀 Быстрый старт

### Запуск базового плейбука на сервере

##### Шаг 1. Подключение по SSH
Подключитесь к серверу, на котором требуется настройка. Например:
```bash
ssh root@99.199.99.99
```

##### Шаг 2. Если на сервере нет Git
Плейбук можно скопировать вручную через scp:

```bash
scp playbooks/base-setup.yml root@99.199.99.99:/root/
```

##### Шаг 3. Установка Ansible (если не установлен)

```bash
sudo apt install -y ansible
ansible --version
```

##### Шаг 4. Запуск плейбука
```bash
ansible-playbook playbooks/base-setup.yml -K -v
ansible-playbook playbooks/base-setup.yml -K -v -tags "pm2start"
```

### Запуск базового плейбука с локальной машины:
Этот способ нецелесообразен при настройке одного сервера, так как требует установки Ansible на вашу локальную систему. Это может занять лишнее время и повлечь за собой установку дополнительных зависимостей, которые не понадобятся в дальнейшем.
```bash
ansible-playbook -i inventory/staging playbooks/base-setup.yml
```

## 🔧 Поддерживаемые версии Node.js

Плейбук поддерживает установку нескольких версий Node.js через NVM с возможностью выбора версии по умолчанию:

```yaml
# vars/node_versions.yml
node_versions:
  - "18"
  - "20"
default_version: "20"
```

## 🌐 Nginx Templates

Готовые конфигурации для:
- Динамических сайтов/приложений

## 🔮 Планы развития

- Автоматизация развертывания Docker-контейнеров
- Интеграция с CI/CD pipelines
- Клонирование git репозиториев тестового проекта

💡 Совет: Для работы с разными окружениями используйте теги:

```bash
ansible-playbook -i inventory/production playbooks/site.yml --tags "nodejs,nginx"
```

### 📚 Лицензия: MIT