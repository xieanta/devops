# Практикум по DevOps

Этот репозиторий содержит практические упражнения по DevOps, охватывающие различные аспекты автоматизации, деплоя и управления инфраструктурой.

## Структура проекта

- **exercise-05**: Упражнение по Ansible
  - Роли: `example_role`
  - Playbook: `postgres.yaml`
  - Используется Vagrant для виртуализации

- **exercise-06**: Упражнение по Ansible
  - Роли: `python-sample-app`
  - Playbook: `app.yml`
  - Используется Vagrant для виртуализации

- **exercise-07**: Упражнение по Docker и Docker Compose
  - Фронтенд: React (Node.js, yarn)
  - Бэкенд: Go
  - Деплой: Docker Compose

- **exercise-08**: Упражнение по Kubernetes
  - Манифесты в `.deploy/k8s/manifests`
  - Используется Kind для локального Kubernetes

- **exercise-09**: Упражнение по Kubernetes
  - Манифесты в `.deploy/k8s/manifests`
  - Используется Kind для локального Kubernetes

- **exercise-10**: Упражнение по Helm
  - Helm-чарты для фронтенда и бэкенда
  - Используется Kind для локального Kubernetes

- **exercise-11**: Упражнение по GitLab CI/CD
  - Фронтенд: React (Node.js, yarn)
  - Бэкенд: Go
  - Деплой: GitLab CI/CD, Kubernetes

## Технологии

- **Ansible**: Автоматизация конфигурации и деплоя
- **Docker**: Контейнеризация приложений
- **Docker Compose**: Оркестрация контейнеров
- **Kubernetes**: Управление контейнерами
- **Helm**: Управление пакетами в Kubernetes
- **GitLab CI/CD**: Непрерывная интеграция и доставка
- **Vagrant**: Виртуализация для локальной разработки
- **Kind**: Локальный Kubernetes

## Задачи

Каждое упражнение направлено на решение конкретных задач:

- **exercise-05**: Настройка и деплой PostgreSQL с помощью Ansible
- **exercise-06**: Деплой Python-приложения с помощью Ansible
- **exercise-07**: Контейнеризация и деплой фронтенда и бэкенда с помощью Docker Compose
- **exercise-08**: Деплой приложения в Kubernetes
- **exercise-09**: Деплой приложения в Kubernetes с использованием манифестов
- **exercise-10**: Деплой приложения в Kubernetes с использованием Helm
- **exercise-11**: Настройка CI/CD с помощью GitLab для деплоя в Kubernetes

## Запуск

Для запуска каждого упражнения следуйте инструкциям в соответствующей папке.