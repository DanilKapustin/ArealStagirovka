# Команды Dockerfile

* [FROM](#from)
* [LABEL](#label)
* [ENV](#env)
* [RUN](#run)
* [COPY](#copy)
* [ADD](#add)
* [CMD](#cmd)
* [WORKDIR](#workdir)
* [ARG](#arg)
* [ENTRYPOINT](#entrypoint)
* [VOLUME](#volume)
* [EXPOSE](#expose)





## FROM

### Описание
`Задаёт базовый (родительский) образ.`

### Примеры использования:

`FROM ubuntu:18.04` базовый образ хранится в репозитории ubuntu и включает в себя тег 18.04, уточняющий то, какой именно базовый образ нам нужен



## LABEL

### Описание
`отобразить запущенные процессы`

### Примеры использования:
`LABEL maintainer="jeffmshale@gmail.com"` включает в себя контактные сведения создателя образа

## ENV
### Описание
`Устанавливает постоянные переменные среды`
### Примеры использования:
`ENV ADMIN="jeff" ` после создания контейнера можно пользоваться переменной ADMIN

## RUN
### Описание
`Выполняет команду и создаёт слой образа. Используется для установки в контейнер пакетов`
### Примеры использования:
`RUN apk update && apk upgrade && apk add bash` инструкция сообщает Docker о том, что системе нужно обновить пакеты из базового образа. Вслед за этими двумя командами идёт команда && apk add bash, указывающая на то, что в образ нужно установить bash.

`RUN ["mkdir", "/a_directory"]` использована exec-форма инструкции RUN, в виде RUN ["mkdir", "/a_directory"] для создания директории. При этом, используя инструкцию в такой форме, нужно помнить о необходимости оформления строк с помощью двойных кавычек, как это принято в формате JSON

## COPY
### Описание
`Копирует в контейнер файлы и папки.`

### Примеры использования:
`COPY . ./app` инструкция сообщает Docker о том, что нужно взять файлы и папки из локального контекста сборки и добавить их в текущую рабочую директорию образа. Если целевая директория не существует, эта инструкция её создаст.

`COPY . .` Копируем код из локального контекста в рабочую директорию образа
## ADD
### Описание
`Копирует файлы и папки в контейнер, может распаковывать локальные .tar-файлы`
### Примеры использования:
`ADD https://raw.githubusercontent.com/discdiver/pachy-vid/master/sample_vids/vid1.mp4 \
/my_app_directory` инструкция `ADD` была использована для копирования файла, доступного по URL, в директорию контейнера `my_app_directory`. Надо отметить, однако, что документация Docker не рекомендует использование подобных файлов, полученных по URL, так как удалить их нельзя, и так как они увеличивают размер образа.

## CMD
### Описание
`Описывает команду с аргументами, которую нужно выполнить когда контейнер будет запущен. Аргументы могут быть переопределены при запуске контейнера. В файле может присутствовать лишь одна инструкция CMD`
### Примеры использования:
`CMD ["python", "./my_script.py"]` с помощью этой команды запускается скрипт my_script.py во время выполнения контейнера

## WORKDIR
### Описание
`Задаёт рабочую директорию для следующей инструкции`
### Примеры использования:
`WORKDIR /usr/src/my_app_directory`  Задаём текущую рабочую директорию
## ARG
### Описание
`Задаёт переменные для передачи Docker во время сборки образа`
### Примеры использования:
`ARG my_var=my_default_value` Задаём значение по умолчанию для переменной
## ENTRYPOINT
### Описание
`Предоставляет команду с аргументами для вызова во время выполнения контейнера. Аргументы не переопределяются`
### Примеры использования:
`ENTRYPOINT ["python", "./app/my_script.py", "my_var"]` Настраиваем команду, которая должна быть запущена в контейнере во время его выполнения
## EXPOSE
### Описание
`Указывает на необходимость открыть порт`
### Примеры использования: 
`EXPOSE 8000` Открываем порт 8080
## VOLUME 
### Описание
`Создаёт точку монтирования для работы с постоянным хранилищем`
### Примеры использования:

`VOLUME /my_volume` Создаём том для хранения данных