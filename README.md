# Лабораторная работа №4
### Репозиторий
Сборка осуществляется из этого репозитория  
### Описание конфигурационного файла

```yml
version: 2.1

orbs:
  python: circleci/python@1.2
```
```yml  
jobs:
  build-and-test: 
    docker:
      - image: cimg/python:3.8

 
    steps:
      - add_ssh_keys:
          fingerprints:
            - e5:60:37:47:81:81:25:b5:07:6f:4f:b5:40:d8:27:cd

      - checkout
      - run: pip install -r requirements.txt
      - run: lektor build && lektor deploy
```
```yml      
workflows:
  sample: 
    jobs:
      - build-and-test
```
### Сборка
Сборка завершилась успешно  
![Результат](/build_and_test.jpg)
