# «Сетевое взаимодействие в K8S. Часть 1» 


### Задание 1 

*Создать Deployment и обеспечить доступ к контейнерам приложения по разным портам из другого Pod внутри кластера*

*Создать Deployment приложения, состоящего из двух контейнеров (nginx и multitool), с количеством реплик 3 шт.*

*Создать Service, который обеспечит доступ внутри кластера до контейнеров приложения из п.1 по порту 9001 — nginx 80, по 9002 — multitool 8080.*

*Создать отдельный Pod с приложением multitool и убедиться с помощью curl, что из пода есть доступ до приложения из п.1 по разным портам в разные контейнеры.*

*Продемонстрировать доступ с помощью curl по доменному имени сервиса.*

**Предоставить манифесты Deployment и Service в решении, а также скриншоты или вывод команды п.4.*


Создаем новый Pod.

![](img/1.png)

![](img/2.png)


Пишем манифест Deployment приложения, состоящего из двух контейнеров (nginx и multitool).
Количество реплик 3 шт.

![](img/3.png)

Применяем манифест и проверяем результат: 

![](img/4.png)


Пишем манифест Service, который обеспечит доступ внутри кластера до контейнеров приложения из п.1 по порту 9001 — nginx 80,по 9002 — multitool 8080. 


![](img/5.png)


Применяем манифест и проверяем результат: 

![](img/6.png)


Пишем манифест отдельного Pod, с приложением multitool и запускаем его: 

![](img/7.png)

![](img/8.png)

Проверяем адреса запущенных подов: 

![](img/9.png)

Из пода multitool проверяем доступность приложений в подах по одному из IP адресов: 

![](img/10.png)

С помощью curl проверяем доступность подов по доменному имени сервиса:


![](img/11.png)

![](img/12.png)

### Задание 2

*Создать Service и обеспечить доступ к приложениям снаружи кластера*

*Создать отдельный Service приложения из Задания 1 с возможностью доступа снаружи кластера к nginx, используя тип NodePort.*

*Продемонстрировать доступ с помощью браузера или curl с локального компьютера.*

*Предоставить манифест и Service в решении, а также скриншоты или вывод команды п.2.*

Создадим отдельный Service приложения из Задания 1, с возможностью доступа снаружи кластера к nginx, используя тип NodePort:

![](img/14.png)

Проверяем, доступны ли приложения из подов по внешним портам: 


![](img/15.png)

![](img/16.png)

Ссылка на манифесты:

https://github.com/dmistus/Kubernetes_04/tree/main/src