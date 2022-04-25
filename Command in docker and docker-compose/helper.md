# Команды docker

* [pull](#pull)
* [push](#push)
* [login](#login)
* [images](#images)
* [ps](#ps)
* [tag](#tag)
* [rmi](#rmi)
* [rm](#rm)
* [system prune](#system-prune)
* [build](#build)
* [run](#run)




## pull

### Описание
`Загрузить образ из регистра`

### Примеры использования:

`docker pull wallarm/node` Скачать образ из репозитория 



## push

### Описание
`Загрузить образ в репозиторий`

### Примеры использования:
`docker push example.com:5000/my_image` загружает образ в репозиторий example.com:5000/my_image

## login
### Описание
`Позволяет логинится в приватные репозитории`
### Примеры использования:
`docker login`  потребуется ввести логин и пароль.

## images
### Описание
`Список образов, доступных локально`
### Примеры использования:
`docker images` Список образов в вашей системе 

## ps
### Описание
`Список контейнеров`

    Ключ -a покажет в том числе остановленные, а ключ -s — его размер. т.е. сколько фактически, сейчас, в рантайме, этот контейнер занимает места на диске
### Примеры использования:
`docker ps` показать список работающих контейнеров

`docker -a` показать список всех контейнеров

## tag
### Описание
`Переименовать образ`

    docker tag <existing image name> <new image name>
### Примеры использования:
`docker tag helloWirld helloWorld` Переименует образ helloWirld в helloWorld

## rmi
### Описание
`Удалить образ`

    docker rmi <image>

## rm
### Описание
`Удалить контейнер`

    docker rm <container>

## system prune
### Описание
`Удалить все остановленные контейнеры`
### Примеры использования:
`docker system prune`

## build
### Описание
`Собрать образ`
### Примеры использования:
`docker build . -t my-first-image` собрать образ в текущей папке и назвать его my-first-image

## run
### Описание
`Запустить образ`

    -it на самом деле являются двумя аргументами -i и -t. Docker позволяет задавать последовательно идущие аргументы без параметров опустив пробел и тире.

        Аргумент -i обозначает то, что клиент docker подключит ваш ввод к контейнеру.

        А ргумент -t обозначает то, что для исполнения контейнера будет выделен псевдотерминал.

    Аргумент -p <локальный порт>:<порт контейнера>/<протокол> пробрасывает(размечает) порты. Если не указывать протокол, будет использоваться TCP. Если нужно разметить несколько портов, нужно указать аргумент -p несколько раз. Например:

### Примеры использования:
`docker run -it -p 8000:8000 my-first-image` запустить образ с подключенным вводом к контейнеру и с выделением псевдотерминала, на порте 8000 с именем my-first-image

`docker run -it -p "80:8000/tcp" -p "5000:5000/udp" my-first-image` запустить образ с подключенным вводом к контейнеру и с выделением псевдотерминала, разметить порт контейнера 8000 к локальному порту 80 по протоколу tcp и порт 5000 к 5000 по протоколу udp, с именем my-first-image


# Команды docker-compose

* [up](#up)
* [down](#down)
* [start](#start)
* [stop](#stop)

## up
### Описание
`Развёртывает сервисы веб-приложений и создаёт из docker-образа новые контейнеры, а также сети, тома и все конфигурации, указанные в файле Docker Compose.`

### Примеры использования:
`docker-compose up` Запускает целевую конфигурацию, но в режиме расширенного вывода и без возврата к подсказке терминала. 

`docker-compose up -d` Использование флага -d аналогично нажатию Ctrl+Z: такая команда отделяет контейнер от консоли и продолжает его работу в фоновом режиме, а также выводит на экран новое имя контейнера.

## down
### Описание
`Останавливает все сервисы, связанные с определённой конфигурацией Docker Compose. Она НЕ удаляет ни контейнеры, ни связанные с ними внутренние тома и сети`

### Примеры использования:
`docker-compose down` Останавливает все сервисы

## start
### Описание
`Запускает любые остановленные сервисы в соответствии с параметрами остановленной конфигурации, указанными в том же файле Docker Compose.`
### Примеры использования:
`docker-compose start` Запускает любые остановленные сервисы в соответствии с параметрами остановленной конфигурации.

## stop
### Описание
`Останавливает все сервисы, связанные с определённой конфигурацией Docker Compose. В отличие от команды stop, она также удаляет все контейнеры и внутренние сети, связанные с этими сервисами — но НЕ указанные внутри тома.`
### Примеры использования:
`docker-compose down` Список образов в вашей системе 