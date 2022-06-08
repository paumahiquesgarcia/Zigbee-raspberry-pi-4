# Instalación de Zigbee a traves de docker

## Requisitos

Para poder seguir esta guia tenemos que tener instalados socker y docker-compose, puede instalarlos siguiendo esta otra guia:

[Instalacion de docker en una raspberry pi 4](docker.md)

## Instalación y configuración

1. Primero debemos encontrar la localización del apadtador Zigbee, conectalo a la raspberry y ejecuta este comando (en esta guia vamos a asumir que el adaptador esta montado en ttyACM0, pero puede que no sea vuestro caso):
~~~
sudo dmesg
~~~
2. Crearemos una carpeta donde guardaremos el proyecto:
~~~
mkdir docker
cd docker
~~~
3. Crearemos el archivo "docker-compose.yaml" que definira como sera nuestro contenedor:
~~~
touch docker-compose.yaml
~~~
4. Ahora lo editaremos y le añadiremos las siguientes lineas:
~~~
version: '3.8'
services:
  mqtt:
    image: eclipse-mosquitto:2.0
    restart: unless-stopped
    volumes:
      - "./mosquitto-data:/mosquitto"
    ports:
      - "1883:1883"
      - "9001:9001"
    command: "mosquitto -c /mosquitto-no-auth.conf"

  zigbee2mqtt:
    container_name: zigbee2mqtt
    restart: unless-stopped
    image: koenkk/zigbee2mqtt
    volumes:
      - ./zigbee2mqtt-data:/app/data
      - /run/udev:/run/udev:ro
    ports:
      - 8080:8080
    environment:
      - TZ=Europe/Berlin
    devices:
      - /dev/ttyUSB0:/dev/ttyACM0
 ~~~
 5. Ahora crearemos la carpeta "zigbee2mqtt-data" y dentro de ella el archivo de configuración de Zigbee2MQTT:
 ~~~
 mkdir zigbee2mqtt-data
 touch zigbee2mqtt-data/configuration.yaml
 ~~~
 6. Añadiremos las siguientes lineas al archivo de configuración de Zigbee2MQTT:
 ~~~
 # Deja que se unan nuevos dispositivos a la red Zigbee
permit_join: true
# Docker-Compose hace el servidor mqtt disponible usando el hostname "mqtt" 
mqtt:
  base_topic: zigbee2mqtt
  server: mqtt://mqtt
# Zigbee Adapter path
serial:
  port: /dev/ttyUSB0
# Activa la pagina web de Zigbee
frontend:
  port: 8080
# Permite a Zigbee2MQTT generar una nueva contraseña de red al primer inicio
advanced:
  network_key: GENERATE
 ~~~
 7. 
 
