* Задачи под звездочкой буду решать  по мере появления времени, для развития. Буду дополнять этот фаил.

------
# Fork репозитория 
https://github.com/ne0kk/shvirtd-example-python.git

------
### Задача 0
Уточним версию Docker

![image](https://github.com/user-attachments/assets/ae4dc652-2052-42cc-a88c-4c859630b3dd)

------
### Задача 1
Создадим образ 
![image](https://github.com/user-attachments/assets/32494272-cf07-4a35-ba78-82cf6a02620a)

------
### Задача 2 
(не обратил внимание что задача под звездочкой, потратил время на нее)

Создал regitry в YC

![image](https://github.com/user-attachments/assets/3dc09f21-eceb-4893-acdd-1421fbd2fc00)

Настроил конфиг

![image](https://github.com/user-attachments/assets/6fd8bd39-3967-45e9-b710-67cfc69a7016)

Запушил образ 

![image](https://github.com/user-attachments/assets/c34e8ecb-a122-4b61-a1f4-f6c4e4d55d77)

Провеизвел сканирование


![image](https://github.com/user-attachments/assets/260394bf-c585-4485-a750-c3425d4f2448)

------
### Задача 3

Создал compose.yaml.
Выполнил - docker compose up -d
ВЫполнил запросы с хоста dcoker и основного хоста
![image](https://github.com/user-attachments/assets/d64dea61-5722-422d-9b56-28131c39ee24)

------
### Задача 4

Создал ВМ в YC.

![image](https://github.com/user-attachments/assets/7a063a1b-5b82-4765-ac6c-477ea91e287e)

Создал локльно скрипт для раскатки проекта.

![image](https://github.com/user-attachments/assets/4b7c4cd8-79a4-4a1e-95ef-c3b6afe02010)

После развертывания подключился к https://check-host.net/check-http

![image](https://github.com/user-attachments/assets/a2582a23-26fe-4b2e-a17e-7ca9a697d10f)

select запрос к БД

![image](https://github.com/user-attachments/assets/ed9ada6b-2a6c-4989-982c-1ff41694b3a4)

------
### Задача 5 (*) В ПРОЦЕССЕ
Очень хочу победить. Бился долше всего, но так нет результата, бросил пока. 

Срипт bash 
#!/bin/bash
source /home/user/data.txt
docker pull schnitzler/mysqldump:3.4
docker run \
    --network shvirtd-example-python_backend \
    --rm --entrypoint "" \
    -v `pwd`/backup:/backup \
    --link="db" \
    schnitzler/mysqldump \
    mysqldump -h 172.20.0.10 -u root -pYtReWq4321 "--result-file=/backup/dumps.sql" virtd
Падает с ошибкой 
mysqldump: Got error: 1045: "Plugin caching_sha2_password could not be loaded: Error loading shared library /usr/lib/mariadb/plugin/caching_sha2_password.so: No such file or directory" when trying to connect
![image](https://github.com/user-attachments/assets/d172623c-efd8-4e0a-8dc1-6c8776a2a645)

------
### Задача 6
Пулим образ hashicorp/terraform:lates.

С помощью dive простматриваем слои ищем terraform
dive hashicorp/terraform:latest

![image](https://github.com/user-attachments/assets/5f7f31aa-01fb-425c-b3ec-03af64873f53)

Сохраняем с помощью  docker save
docker save hashicorp/terraform -o terraform.tar

Разархиваруем с помощью tar
tar -xvf terraform.tar

Находим нужный фаил и копируем

![image](https://github.com/user-attachments/assets/63f82293-606d-4a9a-a669-72f6cd7d263a)
![image](https://github.com/user-attachments/assets/9a0d3c89-7b92-4f87-b226-586f9c5d7cf9)

------
### Задача 6.1
Зная расположение файла в контейнере выполняем команду 
docker cp dreamy_lalande:/bin/terraform /home/user02/terraform_cp
![image](https://github.com/user-attachments/assets/8d5a448a-4598-42da-8b8e-6647bee09ecd)
![image](https://github.com/user-attachments/assets/0dd3a2ce-34a1-47ad-9d21-90e64d3f6716)

------
### Задача 6.2 (**) В ПРОЦЕССЕ
Предложите способ извлечь файл из контейнера, используя только команду docker build и любой Dockerfile.
Предоставьте скриншоты действий .

Капал в сторону mount, но как понял там только гна чтение данные, и после удаляются. Пока думаю. 

------
### Задача 7 (***) В вебинаре разбирали, не пробовал, ищу время. 
Запустите ваше python-приложение с помощью runC, не используя docker или containerd.
Предоставьте скриншоты действий .


