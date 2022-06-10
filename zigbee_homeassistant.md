# Configurar Zigbee a traves de Home Assistant
![Imagen GIT](imagenes/zha.png)

## Requisitos

Para seguir esta guia tenemos que tener instalado Home Assistant, aqui tenemos dos guias para poder instalarlo:
* [Instalacion de Home Assistant a traves de consola](homeassistant_consola.md)
* [Instalacion de Home Assistant a traves de Docker](homeassistant_docker.md)

## Configuración

1. Ponemos el controlador Zigbee en la raspberry y reiniciamos Home Assistant
2. Iremos a la interfaz web de Home Assistant y iremos a "Ajustes"

![Imagen GIT](imagenes/zh1.png)

3. Le damos a Dispositivos y servicios

![Imagen GIT](imagenes/zh2.png)

4. Veremos que Home Assistant ha descubierto el controlador y le daremos a "CONFIGURAR"

![Imagen GIT](imagenes/zh3.png)

5. Le daremos a "ENVIAR"

![Imagen GIT](imagenes/zh4.png)

6. Indicaremos en que area tenemos el controlador y le daremos a "TERMINAR"

![Imagen GIT](imagenes/zh5.png)

Y ya tendremos configurado Zigbee en Home Assistant
