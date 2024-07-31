# multidomain-zabbix
## Установим Docker и Docker compose по инструкции c [официального сайта](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
### Добавляем официальный GPG-ключ Docker:
```
sudo apt-get update
```
```
sudo apt-get install ca-certificates curl
```
```
sudo install -m 0755 -d /etc/apt/keyrings
```
```
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```
```
sudo chmod a+r /etc/apt/keyrings/docker.asc
```
### Добавляем репозиторий:
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt-get update
```
### Устанавливаем пакеты Docker
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
## Запуск Docker compose
### Создаём и переходим в папку Zabbix
```
mkdir Zabbix
```
```
cd Zabbix
```
### Скачиваем конфигурационный файл
```
sudo wget https://raw.githubusercontent.com/maf1oznic/multidomain-zabbix/main/zabbix-docker-compose.yml
```
### Запускаем контейнеры
```
sudo docker compose -f zabbix-docker-compose.yml up -d
```
### Проверим состояние контейнеров
```
sudo docker ps -a
```
### Веб-интерфейсы должны запуститься на портах 82, 83 и 84. Стандартные данные для входа: Admin:zabbix
### Если видите ошибку "Database error", нужно подождать.
## Для удобства выдачи сертификатов можно использовать Nginx Proxy Manager: [документация](https://nginxproxymanager.com/guide/)
