## Домашнее задание к занятию "14.3 Карты конфигураций" </br>
### Задача 1: Работа с картами конфигураций через утилиту kubectl в установленном minikube </br>
Выполните приведённые команды в консоли. Получите вывод команд. Сохраните задачу 1 как справочный материал. </br>

### Как создать карту конфигураций?
```
kubectl create configmap nginx-config --from-file=nginx.conf
kubectl create configmap domain --from-literal=name=netology.ru
```
![config_map](https://github.com/murzinvit/screen_1/blob/581e6513f7410ebfbb738bf8092f82661c034fd0/Kuber_config_map_create.jpg) </br>

### Как просмотреть список карт конфигураций?
```
kubectl get configmaps
kubectl get configmap
```
![get_config](https://github.com/murzinvit/screen_1/blob/ae4fdd313f6996087f6c3c16500536d8b57874e1/Kuber_get_config_.jpg) </br>

### Как просмотреть карту конфигурации?
```
kubectl get configmap nginx-config
kubectl describe configmap domain
```
![conf_map](https://github.com/murzinvit/screen_1/blob/4d5ba71474da7622ba6ae6150481fdd120250756/Kuber_describe_conf_map.jpg) </br>

### Как получить информацию в формате YAML и/или JSON?
```
kubectl get configmap nginx-config -o yaml
kubectl get configmap domain -o json
```
![](https://github.com/murzinvit/screen_1/blob/5fa0881cf7f90fc2918d2b9040116601296cbf48/Kuber_get_config_map_json_yaml.jpg) </br>

### Как выгрузить карту конфигурации и сохранить его в файл?
```
kubectl get configmaps -o json > configmaps.json
kubectl get configmap nginx-config -o yaml > nginx-config.yml
```
![download_yaml](https://github.com/murzinvit/screen_1/blob/e3c1510aba56bc109d4b5bbc4900c0491bee24ca/Kuber_configmap_download_yaml.jpg) </br>

### Как удалить карту конфигурации?
```
kubectl delete configmap nginx-config
```
![delete_configmap](https://github.com/murzinvit/screen_1/blob/9bb22f19f18e24123188103283d8d347add571fe/Kuber_delete_configmap.jpg) </br>

### Как загрузить карту конфигурации из файла?
```
kubectl apply -f nginx-config.yml
```
![](https://github.com/murzinvit/screen_1/blob/d80d22d7b2d2c73b434ecb16c7276a7664eb1ef9/Kuber_create_configmap_from_yaml.jpg) </br>

## Задача 2 (*): Работа с картами конфигураций внутри модуля </br>
Выбрать любимый образ контейнера, подключить карты конфигураций и проверить </br>
их доступность как в виде переменных окружения, так и в виде примонтированного тома </br>

YAML для деплоя configmap + nginx + service NodePort:  </br> 
[nginx-pod.yaml](https://github.com/murzinvit/14.3_configmap/blob/bec703ffe954f890c279020695c021fba519d451/nginx-pod.yaml) </br>
![](https://github.com/murzinvit/screen_1/blob/eaada1ec3a5425be13703d82552defc0e822d459/Kuber_get_configmap_po.jpg) </br>

---
### Создание ConfigMap из файла: </br>
Для пода с mysql: </br>
Создать configmap из файла: `kubectl create configmap mysql-config --from-file=mysql.cnf` [mysql.cnf](https://github.com/murzinvit/14.3_configmap/blob/db5546285578c689e864e28d6c0ea98a1f79b35b/mysql.cnf) </br>
Выгрузить configmap в yaml: `kubectl get configmap mysql-config -o yaml > mysql-config.yml`[mysql-config.yml](https://github.com/murzinvit/14.3_configmap/blob/db5546285578c689e864e28d6c0ea98a1f79b35b/mysql-config.yml) </br>
После выгрузки у далить `creationTimestamp: "2021-12-15T17:09:43Z"` выгруженного mysql-config.yml </br>
Создать configmap из выгруженного yaml: `kubectl apply -f mysql-config.yml`[mysql-config.yml](https://github.com/murzinvit/14.3_configmap/blob/db5546285578c689e864e28d6c0ea98a1f79b35b/mysql-config.yml) </br>

### Для пода с nginx: </br>




---

### Как оформить ДЗ
В качестве решения прикрепите к ДЗ конфиг файлы для деплоя. Прикрепите скриншоты вывода команды kubectl со списком запущенных объектов каждого типа (pods, deployments, configmaps) или скриншот из самого Kubernetes, что сервисы подняты и работают, а также вывод из CLI.
