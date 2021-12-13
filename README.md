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
![](https://github.com/murzinvit/screen_1/blob/81aa13189910930fa1442eecc904d50367cc38fe/Kuber_get_configmap_yaml.jpg) </br>
![](https://github.com/murzinvit/screen_1/blob/7e09f7750ae23ebf1d73aa1204bbb2000b691749/Kuber_get_config_map_json.jpg) </br>

### Как выгрузить карту конфигурации и сохранить его в файл?
```
kubectl get configmaps -o json > configmaps.json
kubectl get configmap nginx-config -o yaml > nginx-config.yml
```

### Как удалить карту конфигурации?
```
kubectl delete configmap nginx-config
```

### Как загрузить карту конфигурации из файла?
```
kubectl apply -f nginx-config.yml
```

## Задача 2 (*): Работа с картами конфигураций внутри модуля </br>
Выбрать любимый образ контейнера, подключить карты конфигураций и проверить </br>
их доступность как в виде переменных окружения, так и в виде примонтированного тома </br>

---

### Как оформить ДЗ
В качестве решения прикрепите к ДЗ конфиг файлы для деплоя. Прикрепите скриншоты вывода команды kubectl со списком запущенных объектов каждого типа (pods, deployments, configmaps) или скриншот из самого Kubernetes, что сервисы подняты и работают, а также вывод из CLI.
