# Flahear USB CC2531 en Linux

## Requisitos

Para poder flashear el USB CC2531 con el firmware de Zigbee seran necesarios los siguientes dispositivos

* [go](http://stackoverflow.com){:target="_blank"}
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

7. Descargamos el firmware <a href="https://github.com/Koenkk/Z-Stack-firmware/raw/master/coordinator/Z-Stack_Home_1.2/bin/default/CC2531_DEFAULT_20211115.zip" target="_blank" rel="noopener noreferrer">CC2531_DEFAULT_20211115.zip<span><svg class="icon outbound" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" focusable="false" x="0px" y="0px" viewBox="0 0 100 100" width="15" height="15"><path fill="currentColor" d="M18.8,85.1h56l0,0c2.2,0,4-1.8,4-4v-32h-8v28h-48v-48h28v-8h-32l0,0c-2.2,0-4,1.8-4,4v56C14.8,83.3,16.6,85.1,18.8,85.1z"></path><polygon fill="currentColor" points="45.7,48.7 51.3,54.3 77.2,28.5 77.2,37.2 85.2,37.2 85.2,14.9 62.8,14.9 62.8,22.9 71.5,22.9"></polygon></svg><!--[--><!--]--></span></a>

8. Flasheamos el Firmware
~~~
sudo ./cc-tool -e -w CC2531ZNP-Prod.hex
~~~

Y ya habriamos terminado de flashear el firmware de Zigbee en el USB CC2531

