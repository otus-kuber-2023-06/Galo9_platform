# Galo9_platform
Galo9 Platform repository

ДЗ №1

1. Разберитесь почему все pod в namespace kube-system восстановились после удаления.
![изображение](https://github.com/otus-kuber-2023-06/Galo9_platform/assets/139074361/3d9cf49e-6d4b-4b14-ada0-c42634e0a6e0)

Ответ:
1.1. coredns - объект Deploiment. Этот под восстанавливается с помощью RepliceSet.
![изображение](https://github.com/otus-kuber-2023-06/Galo9_platform/assets/139074361/f31dffa7-4642-4047-aa47-27cdb28ab642)

1.2. kube-apiserver-minikube, etcd-minikube, kube-controller-manager-minikube, kube-scheduler-minikube - статические поды, которые управляются kubelet. kubelet следит за тем, чтобы поды были запущены.

1.3. kube-proxy - объект DaemonSet. Этот под автоматически запускается на каждой ноде.

2. Создан Dockerfile, запускающий web-сервер на порту 8000, отдающий содержимое директории /app и доступный по ссылке http://localhost:8000/homework.html

3. Hipster Shop.
3.1. Был склонирован указанный репозиторий и собран собственный образ - galo9/frintend.
   Был запущен под frontend и сгенерирован манифест frontend-pod.yaml.

3.2. Задание со звездочкой.
Под frontend находится в статусе ERROR из-за следующих ошибок:
panic: environment variable "PRODUCT_CATALOG_SERVICE_ADDR" not set
panic: environment variable "CURRENCY_SERVICE_ADDR" not set
panic: environment variable "CART_SERVICE_ADDR" not set
panic: environment variable "RECOMMENDATION_SERVICE_ADDR" not set
panic: environment variable "CHECKOUT_SERVICE_ADDR" not set
panic: environment variable "SHIPPING_SERVICE_ADDR" not set
panic: environment variable "AD_SERVICE_ADDR" not set

В манифесте frontend-pod-healthy.yaml были укаазаны значения для этих компонентов и под запустился.
![изображение](https://github.com/otus-kuber-2023-06/Galo9_platform/assets/139074361/4a84a4be-4769-416b-add1-cd3696521381)
