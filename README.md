# Информация и примеры по Django

`$ pip3 list` - выводит список установленных пакетов



## Установка виртуального окружения (venv)

`$ sudo apt-get install python3-venv` - устанавливает пакет venv

`$ python3 -m venv env` - устанавливает виртуальное окружение venv в папку env *(внутри папки проекта)*

`$ source env/bin/activate` - активация виртуального окружения *(внутри папки проекта)*

`$ deactivate` - деактивация виртуального окружения



## Установка Django

`$ pip3 install Django` - установка Django (до этого активировать venv)

`$ django-admin` - выводит список доступных команд

`$ django-admin startproject имя` - создаёт проект (появится папка проекта)


**Отладочный сервер:**<br />
`$ python3 путь/manage.py runserver` - запускает отладочный сервер (по умолчанию:  http://127.0.0.1:8000/)<br />
`$ python3 путь/manage.py runserver 4000` - запускает отладочный сервер с 4000 портом<br />
`$ python3 путь/manage.py runserver 1.2.3.4:4000` - запускает отладочный сервер по ip-адресу: 1.2.3.4:4000







************
## Старый конспект - поправить и перенести выше

`$ python3 manage.py startapp приложение` - создаём приложение (модуль)

`$ pip3 install pillow` - нужно для работы модуля models.ImageField

`$ python3 manage.py makemigrations` - создаёт миграции

`$ python3 manage.py sqlmigrate news 0001` - показывает sql запрос

`$ python3 manage.py migrate` - выполняет миграцию

`$ python3 manage.py shell` - интерактивная оболочка Django (аналог команды python3)

`$ quit()` - выйти 


### Админка

`$ python3 manage.py createsuperuser` - создаём суперадмина для админки

`$ pip3 install django-grappelli` - меняем вид админки [django-grappelli](https://django-grappelli.readthedocs.io/en/latest/quickstart.html)
