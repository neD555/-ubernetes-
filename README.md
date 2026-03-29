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

### Задание 3: Настройка RBAC.

Задача.

Создать пользователя с ограниченными правами (только просмотр логов и описания подов).

Шаги выполнения:

1.Включите RBAC в microk8s

microk8s enable rbac

2.Создать SSL-сертификат для пользователя.

openssl genrsa -out developer.key 2048

openssl req -new -key developer.key -out developer.csr -subj "/CN={ИМЯ ПОЛЬЗОВАТЕЛЯ}"

openssl x509 -req -in developer.csr -CA {CA серт вашего кластера} -CAkey {CA ключ вашего кластера} -CAcreateserial -out developer.crt -days 365

3.Создать Role (только просмотр логов и описания подов) и RoleBinding

4.Проверить доступ.

### Что сдать на проверку.

Манифесты:

role-pod-reader.yaml

rolebinding-developer.yaml

Команды генерации сертификатов.

Скриншот проверки прав (kubectl get pods --as=developer).

### Ответ.
<img width="586" height="351" alt="дз3(1)" src="https://github.com/user-attachments/assets/5d1b5c69-587e-4de7-8003-23a078008a61" />

Команды:

openssl genrsa -out developer.key 2048

openssl req -new -key developer.key -out developer.csr -subj "/CN=developer"

openssl x509 -req -in developer.csr \
 
  -CA /var/snap/microk8s/current/certs/ca.crt \
 
  -CAkey /var/snap/microk8s/current/certs/ca.key \
  
  -CAcreateserial \
 
  -out developer.crt \
 
  -days 365







