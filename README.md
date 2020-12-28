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

`$ django-admin startproject <name>` - создаёт проект (появится папка проекта)


**Отладочный сервер:**

`$ python3 путь/manage.py runserver` - запускает отладочный сервер (по умолчанию:  http://127.0.0.1:8000/)<br />
`$ python3 путь/manage.py runserver 4000` - запускает отладочный сервер с 4000 портом<br />
`$ python3 путь/manage.py runserver 1.2.3.4:4000` - запускает отладочный сервер по ip-адресу: 1.2.3.4:4000



## Создание нового приложения в Django

`$ python3 manage.py startapp <name>` - создаём приложение (модуль)`

После его нужно зарегистрировать в файле **settings.py** в списке **INSTALLED_APPS** (`'<name>.<file>.<Class>'`), например:

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog.apps.NewsConfig',
]
```



## Контроллеры (views) и маршруты (urls)

Создаём контроллер в виде функции в файле **views.py**:

``` Python3
from django.shortcuts import render
from django.http import HttpResponse


def index(request):
    return HttpResponse('Hello world!')
```

Добавляем его в список адресов в файле **urls.py** в список **urlpatterns**:

``` Python3
from news.views import index

urlpatterns = [
    path('admin/', admin.site.urls),
    path('blog/', index),
]
```

Пометить папку проекта **Mark Directory as -> Suorce Root**, чтобы пути работали верно.

Со временем станет слишком много view'х, поэтому правильнее использовать **include**:

``` Python3
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('blog/', include('blog.urls')),
]
```

Файл **urls.py** нужно создать в модуле (приложении):

``` Python3
from django.urls import path

from .views import index, test

urlpatterns = [
    path('', index),
    path('test/', test)
]
```



## Модели (models)

Пример файла **models.py**:

``` Python3
from django.db import models


class Blog(models.Model):
    title = models.CharField(max_length=150)
    content = models.TextField(blank=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    photo = models.ImageField(upload_to='photos/%Y/%m/%d/')
    is_published = models.BooleanField(default=True)
```

`max_length=150` - максимальное количество символов.<br />
`blank=True` - не обязательно к заполнению, по умолчанию все обязательны.<br />
`auto_now_add=True` - автоматически подставляет текущее время, один раз при создании.<br />
`auto_now=True` - автоматически подставляет текущее время, каждый раз при сохранении.<br />
`upload_to='photos/%Y/%m/%d/'` - папка в которую будут загружаться фотографии.<br />
`default=True` - по-умолчанию - None



## Миграции (migrations)

`$ pip3 install pillow` - нужно для работы модуля models.ImageField

`$ python3 manage.py makemigrations` - создаёт миграции (в папке *migrations* появится соответствующий файл)

`$ python3 manage.py sqlmigrate blog 0001` - показывает sql запрос

`$ python3 manage.py migrate` - выполняет миграцию


### Указываем Django куда загружать файлы

В файле **settings.py** внизу добавляем:

``` Python3
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
MEDIA_URL = '/media/'
```

В файле **settings.py** `DEBUG = True` - для отладочного режима.

Для отладочного режима в файл **urls.py** добавить:

``` Python3
from django.conf import settings
from django.conf.urls.static import static


if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA__ROOT)
```









************
## Старый конспект - поправить и перенести выше

`$ python3 manage.py shell` - интерактивная оболочка Django (аналог команды python3)

`$ quit()` - выйти 


### Админка

`$ python3 manage.py createsuperuser` - создаём суперадмина для админки

`$ pip3 install django-grappelli` - меняем вид админки [django-grappelli](https://django-grappelli.readthedocs.io/en/latest/quickstart.html)
