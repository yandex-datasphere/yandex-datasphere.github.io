---
layout: page
title: "Часто задаваемые технические вопросы"
header:
  image_fullwidth: head.jpg
---

> [Раздел частых технических вопросов в официальной документации](https://cloud.yandex.ru/docs/datasphere/qa/)

## Настройки проекта

**Cколько времени может занимать уменьшение проектного диска?**
: Уменьшение проектного диска достаточно долгий процесс. Он может занимать более 15 минут.

**Как установить кастомную сеть в проекте?**
: Настройка сети [описана в документации](https://cloud.yandex.ru/docs/datasphere/operations/projects/update).


## Настройка окружения

**Почему при попытке установить пакет появляется ошибка с сетью?**
: Если у вас в настройках проекта указана сеть, то либо уберите ее, либо настройте NAT-шлюз и укажите сервисный аккаунт для работы с ним и с самой сетью. Более подробно с настройками проекта вы можете ознакомиться [здесь](https://cloud.yandex.ru/docs/datasphere/operations/projects/update).

**A в DataSphere можно как-то ставить пакеты с помощью apt?**
: Нет, с помощью apt ставить пакеты нельзя. Попробуйте [собрать Docker с нужным окружением](https://cloud.yandex.ru/docs/datasphere/operations/user-images).

**Подскажите, пожалуйста, можно ли в проекте DataSphere создавать conda environment и запускать код с её помощью?**
: Conda не поддерживается DataSphere, но можно [собрать собственное окружение в Docker-образе](https://cloud.yandex.ru/docs/datasphere/operations/user-images).

## Работы с данными

**Как загрузить датасет и пользоваться им в DataSphere?**
: Самый простой способ - это перетащить датасет в jupyterlab в datasphere. 
Еще можно положить данные в S3 и подключить его к проекту, как это сделать, описано [тут](https://cloud.yandex.ru/docs/datasphere/operations/data/connect-to-s3).

**Есть разница подключать бакет S3 непосредственно внутри датасферы, или обращаться к бакету через boto3?**
: При подключении бакета через fuse (внутри датасферы) он будет подмонтирован к проекту как диск, при работе через [boto3/boto3](https://cloud.yandex.ru/docs/storage/tools/boto) вы обращаетесь непосредственно к файлам в бакете из кода. Подключение внутри датасферы удобнее для работы. 

**При создании ресурса Dataset выскакивает ошибка: Execute error: Datasets size limit exceeded: 500GB.**
: С квотами и лимитами можно ознакомиться [в документации](https://cloud.yandex.ru/docs/datasphere/concepts/limits). В данном случае идет речь о квоте на суммарный объём датасетов в сообществе. Увеличить квоту можно через обращение в поддержку.

**Могу ли я загрузить файл на S3 проекта не через ноутбук этого проекта, а через обычный скрипт на стороннем устройстве?**
: Вы можете загрузить файлы в бакет в объектном хранилище сторонними программами или скриптами, а уже потом использовать его из DataSphere. Это может быть Yandex Object Storage или любой другой S3. Ключ нужно получить при его создании. Как это делать описано [в документации](https://cloud.yandex.ru/docs/datasphere/operations/data/connect-to-s3#before-begin).

**Пытаюсь удалить S3 коннектор, пишет что не может так как используется в проекте.**
: Откройте страницу этого S3 Connector и нажмите там кнопку «Deactivate».

**Возможна ли запись файла в яндекс диск?**
: Запись на Яндекс диск можно реализовать с помощью [библиотеки yadisk](https://pypi.org/project/yadisk/)

## Работа в JupyterLab

**Как правильно перейти с g1.1 на c1.4 в режиме Serverless? Появляется ошибка name 'model' is not defined?**
: Переменная model не сериализовалась. Об этом должно было быть сообщение. Как вариант: можно попробовать сохранить в файл и загрузить на c1.4.

**В ноутбуке DataSphere не получается сделать import пакета.**
: Необходимо установить пакет с помощью 
```python
%pip install opencv-python
```
Подробнее описано [тут](https://cloud.yandex.ru/docs/datasphere/operations/projects/install-dependencies)

**Кто успешно поднимал StableDiffusion на DataSphere? Поделитесь опытом, гайдами, советами, пожалуйста.**
: Мы подготовили для вас [практическое руководство](https://cloud.yandex.ru/docs/datasphere/tutorials/stable-diffusion) 

**Как можно делиться Jupyter Notebook, чтобы можно было посмотреть выполненную тетрадку?**
: Есть несколько вариантов
- Можно сохранить ноутбук в виде HTML
- Можно добавить пользователя в сообщество / проект и он сможет зайти и посмотреть

**Добрый день, можно как-то из интерфейса получить график нагрузки GPU?**
: Да, информация о нагрузке CPU, GPU и RAM доступна в визуализации в верхнем правом углу JupyterLab.

**Где можно посмотреть состояние переменных в блокноте?**
: С помощью кода: `dir()`, `locals()`, `globals()`

**При входе в IDE необходимо указать пароль/токен. При попытке работы в ноутбуке открывается страница, где запрашивается "Password or token: ".**
: Необходимо [изменить настройки браузера](https://cloud.yandex.ru/docs/datasphere/qa/#browser)  

**Можно ли поделиться notebook с человеком, не состоящем в проекте/сообществе?**
: Только сохранив файл ноутбука или выгрузив в html и переслать
расшарить можно только в рамках сообщества

**Не удается скачать ноутбук ipynb со своего проекта в Datasphere, качается html страница, на которой требуется ввод пароля.**
: Попробуйте воспользоваться [рекомендациями](https://cloud.yandex.ru/docs/datasphere/qa/#browser) 

**Какая команда в DataSphere разархивирует файл?**
: Есть несколько вариантов:
- Используя стандартные [API Python](https://docs.python.org/3/library/zipfile.html)
- Из bash ячейки с помощью `unzip`.
- С помощью снипета, в меню снипетов

**Как скачать .ipynb-файл? Когда я нажимаю File > Download, скачивается страница ввода токена**
: Проблема с настройками приватности браузера. Попробуйте изменить настройки, как описано в [последнем вопросе здесь](https://cloud.yandex.ru/docs/datasphere/qa/)

## Деплой моделей

**Можно ли сделать ноду из ячейки, внутри которой происходит загрузка из файла уже обученной модели?**
: Диск проекта не подключается к ноде. Если вы хотите принести в ноду файл нужно [собирать Docker](https://cloud.yandex.ru/docs/datasphere/operations/deploy/node-customization). Требования к Docker-образу описаны [здесь](https://cloud.yandex.ru/docs/datasphere/concepts/docker#requirements)

**Можно ли разворачивать сервис c GUI в DataSphere?**
: Нет, в DataSphere можно развернуть сервис, к которому можно обращаться через REST/gRPC.

## Управление бюджетом

**Как понять, за что списываются деньги в сервисах Yandex Cloud**
: Информация об этом можно посмотреть биллинге: `console.cloud.yandex.ru/billing`. Там есть список платежных аккаунтов, а внутри [детализация](https://cloud.yandex.ru/docs/datasphere/operations/community/billing-details)

**Есть пример, как прикинуть бюджет в DataSphere?**
: Пример расчёта [на странице о тарификации](https://cloud.yandex.ru/docs/datasphere/pricing#prices)

**На платной подписке деньги списываются с привязанной карты, или можно зачислить деньги на баланс аккаунта и спишется только это сумма?**
: [Вот тут](https://cloud.yandex.ru/docs/billing/payment/) подробно расписан порядок расчетов в Yandex Cloud

**сколько стоит Dedicated режим?**
: Стоимость зависит от выбранной конфигурации. [Здесь](https://cloud.yandex.ru/docs/datasphere/pricing) можно ознакомиться с тарифами









 

