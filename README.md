# Автономный автобус
![image](https://github.com/user-attachments/assets/3e0a7ed6-8d44-48cf-8ec9-bd9146564eb3)


## Краткое описание назначения и применения продукта:

Продукт - автономный автобус с бесконтактной оплатой проезда на основе биометрии.
Автобус сканирует лицо пассажира на входе и проводит оплату после идентификации.

Роли пользователей:

Оператор системы - вводит информацию о маршрутах

Сотрудник депо - проверяет системы автобуса перед выходом на маршрут

Пассажиры - перемещаются в автобусе согласно маршруту.


## Ключевые ценности, ущербы, неприемлемые события

| Ценность | Негативное событие | Оценка ущерба | Комментарий |
| :--- | --- | --- | ---: |
| Люди | из-за успешной атаки автобус попал в аварию и пострадали пассажиры    | Высокий    | Может привести к причинению вреда здоровью или смерти     |
| Автобус | из-за атаки была нарушена штатная работа автобуса     | Средний    | Автобус можно починить     |
| Персональные данные | Неавторизованный доступ к ПДн пассажиров    | Высокий    | Влечет за собой штрафы     |
| Деньги, баланс | При реализаии атаки не произойдет списания баланса со счета клиента | Средний    | Потеря прибыли компании    |

## Контекст

![1 drawio](https://github.com/user-attachments/assets/c7a13317-7d2d-4425-8f3e-bf0e1e1ce0da)

## Функциональные сценарии

![image](https://github.com/user-attachments/assets/2288b58b-52b1-426f-bfab-062690c0a1a5)


## Высокоуровневая архитектура


![2 drawio](https://github.com/user-attachments/assets/8d5b969e-f2f3-4bc9-974c-98b8c5bd6851)


## Описание подсистем

| Название | Назначение |
| :--- | ---: |
| Камеры | Предназначены для считывания лица и наблюдения за окружающей обстановкой |
| Система распознавания лица | Предназначена для принятия видео-потока, распознавания лица и кодирования его в определенный формат  |
| Система контроля оплаты | Формирует запрос к бд в сеть оператора, и получает ответ. Контролирует Турникет |
| Турникет | Предназначен для реализации пропускного контроля |
| Система управления | Самый главный модуль, отвечающий за функционирование всего автобуса |
| Система навигации | Модуль, отвечающий за навигацию в пространстве |
| Система ручного управления | Предоставляет функциональные возможности для взятия ручного управления оператором, при необходимости |
| Сетевой модуль + VPN | Предназначен для защищенной коммуникации с сетью оператора |
| ИС оператора | система для оператора, самая важная система во всей сети |
| ИСПДн | система, предназначенная для обработки, хранения, проверки персональных данных  |


## Расширенные диаграммы функциональных сценариев

![image](https://github.com/user-attachments/assets/c4ce7337-730f-4298-999e-1c8819451a31)
![image](https://github.com/user-attachments/assets/4b14089e-36e0-4eca-8c12-7a0d1ce62d17)

## Цели и предположения безопасности

1) Автобус доджен пускать пассажиров, прошедших идентификацию и оплативших проезд
2) Автобус двигаеться только по аутентичным маршрутам
3) Данные клиентов должны быть защищены от подмены и кражи
4) Автобус прекращает работу в случае серьезной неисправности

## Предположения безопасности
1) Система диагностики - в случае поломки, автобус сходит с маршрута, двери аварийно открываются
2) Система ручного управления - возможен переход на систему ручного управления, в случае необходимости незначительно изменить маршрут (аварии, пробки и тд)
3) Сетевой модуль с поддержкой VPN - обеспечивает целостность и конфиденциальность данных.
4) модуль контроля оплаты - проверяет прошла ли оплата успешно.

## Таблица соотнесения ценностей, неприемлемых событий и целей безопасности

| Ценность | Негативное событие | Оценка ущерба | Цель безопасности |
| :--- | --- | --- | ---: |
| люди | С следствии компрометации ИС оператора и перехода на ручное управление, автобус попал в аварию, пострадали люди | Высокий | Цель 2 |
| Автобус | Автобус неисправен, что привело к возгаранию | Высокий | Цель 4 |
| Персональные данные | Кража базы данных клиентов | Высокий | Цель 3 |
| Деньги, баланс | Пассажир получает услугу не оплатив проезд | Средний | Цель 1 |

## Негативные сценарии

![xLTFJpjL5DtFfxZvkT459loM9ZN4k1OI4ZR6HQ5LcqXBschYhgKHCIMWXaJ30aGsBilGiKE7cNw5-xwHv-JDz7NU568CAvNaqVbptxdtt7lkk-rMhr_lzhy-_2ge7_GxNT4RdPYX6Uf4_zJO388Zl6uTj8xgxRwyqIiyVzB837JoHkez-QZLyInkDSR-Our](https://github.com/user-attachments/assets/d17a01ea-28fe-4b44-b6ee-b8e523cac4d3)

![hLPFQpjL5DtFftZyVXkxg93wMmafHLnhGUX6NCGcQj0cQH85TqsgLebKb81IiBNw1U8qpqmpcSbNkFEDFETs_lTLfRYOD3EzzxnpxZdlJGv6uzPm_Fd9PrxhUDmV6hcHHJ999hAGloH8phm1_jqzxWvQlR5v8LTulX6RdCdYXMcDp5lTVgtYLWBqJyMYRc5](https://github.com/user-attachments/assets/f4b30cab-f923-452e-b91a-7d8fc6c47bc0)

## Политика архитектуры

![3](https://github.com/user-attachments/assets/96e48100-a6f2-4879-9036-6a1185dba91c)

## Таблица доменов безопасности системы

| Домен безопасности | Уровень доверия | Оценка сложности и размера домена | Обоснование |
| :--- | --- | --- | ---: |
| Камеры | Недоверенный | SS | Напрямую цели нарушены быть не могут |
| Система распознавания лица | Доверенный | MM | Компрометация приводит к нарушению цели 1 и 3, так как в этом модуле циркулируют ПДн в виде биометрии |
| Система контроля оплаты | Доверенный | SM | Компрометация приводит к нарушению цели 1, так как можно перехватить и отправить чужой биометрический идентификатор |
| Система управления | Доверенный | CL | Компрометация приводит к нарушению целей 1, 2, 4, потому как это главный модуль, влияние на который отразится на всю систему, единственное, не смогут получить биометрические данные, так как не будет доступа к этому модулю напрямую. |
| Турникет | Доверенный | SS | Компрометация приводит к нарушению цели 1 |
| Система диагностики | Доверенный | SS | Компрометация приводит к нарушению цели 4, так как не сможет провести диагностику штатно |
| Система навигации | Повышающий доверие  | SM | Компрометация приводит к нарушению цели 2 |
| Система ручного управления | Доверенный | ML | Компрометация приводит к нарушению целей 2 и 4 |
| Сетевой модуль + VPN | Повышающий доверие | MS | Компрометация приводит к нарушению цели 3 и 1, так как в случае кражи ключей можно перехватывать био-идентификаторы а потом выдавать себя за другого, а в случае 1 цели можно вывести канал из строя, тем самым проверки не будут проходить и пассажиры не смогут пройти через турникет |
| ИС Оператора | Доверенный | CXL | Компрометация нарушает все цели |
| ИСПДн | Доверпенный | ML | Компрометация нарушает цели 3 и 1 |
| БД клиентов | Доверенный | SM | Компрометация нарушает цели 3 и 1 |
