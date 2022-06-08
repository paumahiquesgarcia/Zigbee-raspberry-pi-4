# Instalación de Docker en raspberry pi 4 B

## Instalación de Docker

1. Para instalar Docker introduciremos este comando:
~~~
curl -sSL https://get.docker.com | sh
~~~
2. Añadiremos el usuario actual al grupo de usuarios docker
~~~
sudo usermod -aG docker ${USER}
~~~
3. Habilitamos Docker para iniciarse al arrancar el sistema
~~~
sudo systemctl enable docker
~~~

## Instalación de Docker-Compose

1. Docker-Compose generalmente se instala con pip3, asi que primero lo instalaremos:
~~~
sudo apt-get install libffi-dev libssl-dev
sudo apt install python3-dev
sudo apt-get install -y python3 python3-pip
~~~
2. Ahora instalaremos Docker-Compose con el siguiente comando:
~~~
sudo pip3 install docker-compose
~~~
## (Opcional) Instalar Portainer

Portainer es una interfaz grafica para gestionar docker de una manera mas simple

1. Para iniciarlo introduciremos este comando:
~~~
sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:linux-arm
~~~
2. Para acceder a Portainer tendras que poner tu ip seguida del puerto 9000, ex: 192.168.0.10:9000, lo que nos llevara a esta pagina
