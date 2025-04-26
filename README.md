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
│ ├── nodejs-setup.yml # Установка Node.js + NVM
│ ├── pm2-setup.yml # Настройка PM2
│ └── docker-setup.yml # Установка Docker
├── templates/
│ ├── nginx/ # Шаблоны Nginx
│ │ ├── node-app.conf.j2 # Для Node.js приложений
│ │ └── static-site.conf.j2 # Для статических сайтов
│ └── nodejs/ # Шаблоны для Node.js
├── inventory/ # Файлы инвентаризации
│ ├── production # Для рабочих серверов
│ └── staging # Для тестовых сред
└── vars/ # Переменные
├── common.yml # Общие настройки
└── node_versions.yml # Версии Node.js
```

## 🚀 Быстрый старт

1. Клонируйте репозиторий:
```bash
git clone git@github.com:RenderLifeEx/ansible-lab.git
cd ansible-lab
```

2. Запустите базовый плейбук:

```bash
ansible-playbook -i inventory/staging playbooks/base-setup.yml
```

##  Поддерживаемые версии Node.js

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

- Node.js приложений (с балансировкой)
- Статических сайтов
- SSL/TLS termination
- WebSocket-приложений

## 🔮 Планы развития

- Добавить поддержку кластерного режима PM2
- Автоматизация развертывания Docker-контейнеров
- Интеграция с CI/CD pipelines
- Поддержка мониторинга (Prometheus + Grafana)

💡 Совет: Для работы с разными окружениями используйте теги:

```bash
ansible-playbook -i inventory/production playbooks/site.yml --tags "nodejs,nginx"
```

### 📚 Лицензия: MIT