# Dickobrazz Portainer стек

[![AI Capable](https://img.shields.io/badge/AI-Capable-brightgreen?style=flat&logo=openai&logoColor=white)](https://github.com/mairwunnx-infra/dickobrazz)
[![Docker](https://img.shields.io/badge/Docker-Available-2496ED?style=flat&logo=docker&logoColor=white)](https://github.com/mairwunnx-infra/dickobrazz/pkgs/container/dickobrazz-bot)
[![MongoDB](https://img.shields.io/badge/MongoDB-8.2-47A248?style=flat&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Redis](https://img.shields.io/badge/Redis-8.4-DC382D?style=flat&logo=redis&logoColor=white)](https://redis.io/)

Dickobrazz стек для production/test окружений в инфраструктуре сервера.

В `docker-compose.yaml` описаны:
- **bot/server** сервисы для production и test режимов;
- отдельные **MongoDB/Redis** инстансы и named volumes для изоляции данных;
- **backup** контейнеры только для production томов.

Кастомные образы собираются из upstream-образов и получают конфигурацию через встроенный `config.yaml`:
- `docker-specs/Dockerfile.dickobrazz-bot`
- `docker-specs/Dockerfile.dickobrazz-bot-test`
- `docker-specs/Dockerfile.dickobrazz-server`
- `docker-specs/Dockerfile.dickobrazz-server-test`

Автосборка и публикация в GHCR настраивается workflow-файлом `.github/workflows/build-dickobrazz-images.yml`.

> Примечание: все внутренние сервисы работают внутри сети `infra` и не публикуют порты наружу.

### Связные ссылки:

- [Infra Zygote](https://github.com/mairwunnx-infra/zygote) - Зигота/основа инфраструктуры, которую я использую для своего сервера.
- [Infra Xi Manager](https://github.com/mairwunnx-infra/ximanager) - Portainer стек для проекта Xi Manager.
- [Infra Ingress](https://github.com/mairwunnx-infra/ingress) - Portainer стек для входящего трафика.
- [Infra VS Code](https://github.com/mairwunnx-infra/vscode) - Portainer стек для VS Code.
- [Infra GitLab](https://github.com/mairwunnx-infra/gitlab) - Portainer стек для GitLab.
- [Infra Jenkins](https://github.com/mairwunnx-infra/jenkins) - Portainer стек для Jenkins.

---

<img src="./media.png" alt="Русская сила" width="500">

🇷🇺 **Сделано в России с любовью.** ❤️

> 🫡 Made by Pavel Erokhin (Павел Ерохин), aka mairwunnx.
