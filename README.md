# Installation-and-configuration-v2raya
Установка и настройка v2raya
***
1.	Устанавливаем докер, если не установлен
```
bash <(curl -sSL https://get.docker.com)
```
2.	Скачиваем образ
```
docker pull mzz2017/v2raya
```
3.	Запускаем образ (копируем **ВСЕ** строчки **СРАЗУ**, а не по одной). Обратите внимание на строчку V2RAYA_V2RAY_BIN=/usr/local/bin/xray. V2raya поддерживает и xray core и v2ray core, но v2ray core не поддерживает reality. По умолчанию, стоит xray, поэтому оставляем как есть.
```
docker run -d \
  --restart=always \
  --privileged \
  --network=host \
  --name v2raya \
  -e V2RAYA_LOG_FILE=/tmp/v2raya.log \
  -e V2RAYA_V2RAY_BIN=/usr/local/bin/xray \
  -v /lib/modules:/lib/modules:ro \
  -v /etc/resolv.conf:/etc/resolv.conf \
  -v /etc/v2raya:/etc/v2raya \
  mzz2017/v2raya
```
4.	Заходим по адресу http://x.x.x.x:2017, где x.x.x.x – ip адрес ВПС сервера.
5.	Создаем аккаунт. У меня уже создан, поэтому я просто логиниюсь. Если забыли пароль, то придется устанавливать v2raya без докера и сбрасывать пароль командой v2raya --reset-password.
![Screenshot 2024-10-17 at 13-12-44 v2rayA](https://github.com/user-attachments/assets/fc5a2163-4bdf-4373-b19f-5abea80179fa)
