# Flahear USB CC2531 en Linux

## Requisitos

Para poder flashear el USB CC2531 con el firmware de Zigbee seran necesarios los siguientes dispositivos

* 
* CC2531 downloader cable

## Flash

1. Instalaremos cc-tool
~~~
sudo apt-get -y install cc-tool
~~~

2. Ahora instalaremos sus dependencias, dependiendo de vuestra versión de Linux puede que necesites instalar unas o otras:
  * Ubuntu/Debian
  ~~~
  sudo apt-get -y libusb-1.0-0-dev, libboost-all-dev, autoconf, libtool
  ~~~
  * Fedora
  ~~~
  sudo apt-get -y dh-autoreconf, boost-devel, libusb1-devel, gcc-c++
  ~~~
  * Archlinux
  ~~~
  sudo apt-get -y dh-autoreconf, libusb, boost
  ~~~
  * Raspbian
  ~~~
  sudo apt-get -y dh-autoreconf, libusb-1.0-0-dev, libboost-all-dev
  ~~~
  
3. Armaremos cc-tool
~~~
git clone https://github.com/dashesy/cc-tool.git
cd cc-tool
./bootstrap
./configure
make
~~~

4. Conectaremos el CC debugger al Downloader cable CC2531, y el Downloader cable CC2531 al USB CC2531

5. Conectaremos el USB CC2531 y el CC Debugger al PC via USB

6. Si la luz en el CC debugger es roja, presiona el boton de reset en el CC debugger. La luz deberia volverse verde
<p align="center">
  <img width="460" src="https://www.zigbee2mqtt.io/assets/img/connected.843d662a.jpg">
</p>

7. Descargamos el firmware <a href="https://github.com/Koenkk/Z-Stack-firmware/raw/master/coordinator/Z-Stack_Home_1.2/bin/default/CC2531_DEFAULT_20211115.zip" target="_blank" >CC2531_DEFAULT_20211115.zip</a>

8. Flasheamos el Firmware
~~~
sudo ./cc-tool -e -w CC2531ZNP-Prod.hex
~~~

Y ya habriamos terminado de flashear el firmware de Zigbee en el USB CC2531

