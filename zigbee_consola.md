# Instalación de Zigbee a traves de consola

1. Primero debemos encontrar la localización del apadtador Zigbee, conectalo a la raspberry y ejecuta este comando (en esta guia vamos a asumir que el adaptador esta montado en ttyACM0, pero puede que no sea vuestro caso):
~~~
sudo dmesg
~~~

2. Ahora instalaremos Node.js y algunas dependencias:
~~~
sudo apt-get install -y nodejs npm git make g++ gcc
~~~
3. Clonaremos el repositorio de Zigbee2MQTT y lo moveremos:
~~~
git clone https://github.com/Koenkk/zigbee2mqtt.git
sudo mv zigbee2mqtt /opt/zigbee2mqtt
~~~
4. 
