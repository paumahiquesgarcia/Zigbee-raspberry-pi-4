# Instalar Home Assistant a traves de consola

# Instalación

1. Instalaremos las dependencias:
~~~
sudo apt-get install -y python3 python3-dev python3-venv python3-pip libffi-dev libssl-dev libjpeg-dev zlib1g-dev autoconf build-essential libopenjp2-7 libtiff5 libturbojpeg0-dev tzdata
~~~
2. Crearemos un usuario llamado "homeassistant" cuya funcion sera mantener operativo Home Assistant
~~~
sudo useradd -rm homeassistant -G dialout,gpio,i2c
~~~

## Crear Entorno Virtual

1. Crearemos un directorio para la instalacion de Home Assistant y cambiaremos el propietario al usuario "homeassistant"
~~~
sudo mkdir /srv/homeassistant
sudo chown homeassistant:homeassistant /srv/homeassistant
~~~
2. El siguiente paso es crear el entorno virtual, esto lo haremos desde la cuenta "homeassistant"
~~~
sudo -u homeassistant -H -s
cd /srv/homeassistant
python3 -m venv .
source bin/activate
~~~
3. Ahora que tenemos activado el entorno virtual, instalaremos un paquete de python:
~~~
python3 -m pip install wheel
~~~
