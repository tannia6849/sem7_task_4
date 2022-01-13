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
            - 12:f8:7e:78:61:b4:bf:e2:de:24:15:96:4e:d4:72:53

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
