# Информация и примеры по Django

`$ pip3 list` - выводит список установленных пакетов

## venv (виртуальное окружение)

`$ sudo apt-get install python3-venv` - устанавливает пакет venv

`$ python3 -m venv venv` - устанавливает вирьуальное окружение venv *(внутри папки проекта)*

`$ source venv/bin/activate` - активация виртуального окружения *(внутри папки проекта)*

`$ deactivate` - деактивация виртуального окружения

## Django

`$ pip3 install Django` - установка Django (до этого активировать venv)

`$ django-admin` - выводит список доступных команд






************
## Старый конспект - поправить и перенести выше

`$ django-admin startproject имя` - запускаем проект (появится папка проекта)

`$ python3 путь/manage.py runserver` - запускаем отладочный сервер

`$ python3 путь/manage.py runserver 4000` - запускаем отладочный сервер с 4000 портом (вместо 8000 по умолчанию)

`$ python3 путь/manage.py runserver 1.2.3.4:4000` - запускаем отладочный сервер по ip-адресу: 1.2.3.4:4000

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




******************************

`$ django-admin startproject имя`

`$ python3 путь/manage.py runserver`

`$ python3 manage.py startapp приложение`

`$ python3 manage.py makemigrations app`

`$ python3 manage.py sqlmigrate app 0001`

`$ python3 manage.py migrate`

