# Домашнее задание

- Напишите workflow, который:
  - Собирает докер образ из Dockerfile.multi (дз 10)
  - Загружает его в GitHub registry (ghcr.io)
  - Имя репозитория должно браться из дефолтной переменной GITHUB_REPOSITORY_OWNER
  - Токен с правами для создания packages должен браться из секрета ACTION_TOKEN
  - Тег для докер образа должен браться из переменной github.sha (GITHUB_SHA)
  - Так же докер образу должен присваиваться тег latest
  - Должна быть возможность запускать workflow без комита.

# Полезные ссылки

- [Документация GitHub Actions](https://docs.github.com/en/actions/quickstart)
