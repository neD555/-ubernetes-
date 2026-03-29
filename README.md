#### Домашнее задание к занятию «Настройка приложений и управление доступом в Kubernetes».
### Задание 1: Работа с ConfigMaps.
Задача.

Развернуть приложение (nginx + multitool), решить проблему конфигурации через ConfigMap и подключить веб-страницу.

### Шаги выполнения:

1.Создать Deployment с двумя контейнерами.

nginx

multitool

2.Подключить веб-страницу через ConfigMap.

3.Проверить доступность.

### Что сдать на проверку.

Манифесты:

deployment.yaml

configmap-web.yaml

Скриншот вывода curl или браузера.

### Ответ.
<img width="655" height="312" alt="дз1(1)" src="https://github.com/user-attachments/assets/b604db49-5a0a-4401-8819-dc1c82597a87" />

### Задание 2: Настройка HTTPS с Secrets
Задача.

Развернуть приложение с доступом по HTTPS, используя самоподписанный сертификат.

Шаги выполнения:

1.Сгенерировать SSL-сертификат.
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout tls.key -out tls.crt -subj "/CN=myapp.example.com"

2.Создать Secret.

3.Настроить Ingress.

4.Проверить HTTPS-доступ.  

Что сдать на проверку:

Манифесты:

secret-tls.yaml

ingress-tls.yaml

Скриншот вывода:

curl -k

### Ответ.
<img width="585" height="417" alt="дз2(1)" src="https://github.com/user-attachments/assets/3e749be3-dcb6-442d-90c1-2bad4f8aedca" />





