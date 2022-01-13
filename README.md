# Лабораторная работа №4
### Репозиторий
Сборка осуществляется из этого репозитория  
### Описание конфигурационного файла
В начале файла указывается версия (2, 2.0 или 2.1)
```yml
version: 2.1
```
orbs - включение написанной конфигурации.   
```yml 
orbs:
  python: circleci/python@1.2
```
jobs - рабочий процесс, который состоит из нескольких заданий с уникальными именами.  
```yml  
jobs:
  build-and-test: 
    docker:
      - image: cimg/python:3.8

    # последовательность шагов
    steps:
      # подключение к репозиторию гитхаба с правами записи
      - add_ssh_keys:
          fingerprints:
            - e5:60:37:47:81:81:25:b5:07:6f:4f:b5:40:d8:27:cd

      - checkout
      # установка зависимостей 
      - run: pip install -r requirements.txt
      - run: lektor build && lektor deploy
```
Запуск jobs
```yml      
workflows:
  sample: 
    jobs:
      - build-and-test
```
### Сборка
Сборка завершилась успешно  
![Результат](/build_and_test.jpg)
