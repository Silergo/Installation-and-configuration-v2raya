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
5.	Создаем аккаунт. У меня уже создан, поэтому я просто логиниюсь. Если забыли пароль, то придется устанавливать v2raya без докера и сбрасывать пароль командой ```v2raya --reset-password```
![Screenshot 2024-10-17 at 13-12-44 v2rayA](https://github.com/user-attachments/assets/fc5a2163-4bdf-4373-b19f-5abea80179fa)
6.	Копируем из панели 3x-ui настройки сервера
![5346](https://github.com/user-attachments/assets/10e5b8c1-456e-42d1-87c1-8bb9dd17d936)
7.	Импортируем эти настройка в v2raya
![5347](https://github.com/user-attachments/assets/670f4ada-a91a-418c-9268-0090f1bc7fc4)
8.	Проверяем, что прокси работает. Кнопка *PING* – пинг до самого прокси, кнопка *HTTP* (самое важное) – пинг до сайта **ЧЕРЕЗ** прокси сервер. Если при нажатии на HTTP, вы видите зеленые циферки, значит прокси рабочий и живой, если написано "NOT STABLE", значит в 3x-ui панели выбраны настройки прокси, которые не поддерживаются v2ray.
![5348](https://github.com/user-attachments/assets/993800e2-f3e8-4536-9b53-8dc181d0689a)
9.	Выбираем (кнопка *Connect*) и ЗАПУСКАЕМ (кнопка *Ready*) прокси.
![5349](https://github.com/user-attachments/assets/dbc0d94d-4c34-40dd-b412-c1df8769b4f6)
Строчка должна посинеть, и красная кнопка сменится синей с надписью "Running".
![5350](https://github.com/user-attachments/assets/6ddb5dac-aac8-4fb3-9fe6-a187cb097a5c)
11.	Все, осталось включить прокси в винде. Выбирать можно любой порт (сокс – 20170 или http – 20171). Если с одним портом не работает (хотя должно работать с любым), попробуйте с другим. Ip адрес, соответственно, указываете ВПСки, где установлена v2raya.
![5351](https://github.com/user-attachments/assets/78393cf9-7b82-4bd1-9caa-c1a704cf2b44)
