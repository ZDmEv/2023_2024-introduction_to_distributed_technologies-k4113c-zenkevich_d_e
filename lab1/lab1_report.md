University: [ITMO University](https://itmo.ru/ru/) \
Faculty: [FICT](https://fict.itmo.ru) \
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies) \
Year: 2023/2024 \
Group: K4113с \
Author: Zenkevich Dmitrii Evgenyevich \
Lab: Lab1 \
Date of create: 25.10.2023 \
Date of finished: <none>

# Настройка окружения
В первую очередь необходимо установить docker и minikube.
Проверяем что docker и minikube установились с помощью команд:

`` docker --version ``

![Рисунок 1](../lab1/source/docker-version.png)

`` minikube version ``

![Рисунок 2](../lab1/source/minikube-version.png)

Далее скачиваем image докер-контейнера с помощью команды:

`` docker pull vault:1.13.3  ``

Проверяем, что image установился с помощью команды:

`` docker images  ``

![Рисунок 3](../lab1/source/docker-images.png)

# Запуск minikube
Стартуем minikube с помощью команды:

``minikube start``

![Рисунок 4](../lab1/source/minikube-start.png)

# Создание пода
Чтобы создать под применяем манифест с помощью команды:

``minikube kubectl -- apply -f vault-manifest.yaml``

![Рисунок 5](../lab1/source/kubectl-apply.png)

# Создание сервиса
Создадим сервис для доступа к созданному контенеру с помощью команды:

``minikube kubectl -- expose pod vault --type=NodePort --port=8200``

![Рисунок 6](../lab1/source/kubectl-expose.png)

# Доступ к поду
Прокинем порт компьютера в контейнер с помощью команды:

``minikube kubectl -- port-forward service/vault 8200:8200``

![Рисунок 7](../lab1/source/kubectl-port-forward.png)

Попробуем подключиться к контейнеру по адресу:

``http://localhost:8200``

![Рисунок 8](../lab1/source/auth-page.png)

Найдем root-token в логах для аутентификации с помощью команды:

``minikube kubectl -- logs vault``

![Рисунок 9](../lab1/source/root-token.png)

Теперь можно зайти в приложение:

![Рисунок 10](../lab1/source/auth-success-page.png)

# Остановка кластера

Для остановки кластера воспользуемся командой:

``minikube stop``

![Рисунок 10](../lab1/source/minikube-stop.png)

# Диаграмма системы

![Рисунок 12](../lab1/source/system-diagram.png)