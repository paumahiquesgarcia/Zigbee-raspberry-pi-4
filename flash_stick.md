# Flahear USB CC2531 en Linux

## Requisitos

Para poder flashear el USB CC2531 con el firmware de Zigbee seran necesarios los siguientes dispositivos

* <a href="https://es.aliexpress.com/item/32901173622.html?UTABTest=aliabtest276336_383090&_randl_currency=EUR&_randl_shipto=ES&src=google&src=google&albch=shopping&acnt=439-079-4345&slnk=&plac=&mtctp=&albbt=Google_7_shopping&gclsrc=aw.ds&albagn=888888&ds_e_adid=438858099973&ds_e_matchtype=&ds_e_device=c&ds_e_network=u&ds_e_product_group_id=1484120113634&ds_e_product_id=es32901173622&ds_e_product_merchant_id=109107377&ds_e_product_country=ES&ds_e_product_language=es&ds_e_product_channel=online&ds_e_product_store_id=&ds_url_v=2&albcp=10191226472&albag=102259630056&isSmbAutoCall=false&needSmbHouyi=false&gclid=CjwKCAjw14uVBhBEEiwAaufYxzRudGknJfh8MnM6RO0_wqhjWlePU8dZQAJzVhSGku82Kst_OQoyhxoCK1cQAvD_BwE&aff_fcid=c4f473919d134ef3a3cc92d2d17aae9f-1654888026402-05147-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=c4f473919d134ef3a3cc92d2d17aae9f-1654888026402-05147-UneMJZVf&terminal_id=c3651ce96daa41c999f247c9baf4fcbf&OLP=1082700408_f_group0&o_s_id=1082700408&afSmartRedirect=y" target="_blank" rel="noopener noreferrer" title="***Please middle click on mouse to open in new tab***&#013Github Markdown does not support opening new pages (github.com/mojombo/github-flavored-markdown/issues/28)">CC debugger</a>
* <a href="https://es.aliexpress.com/item/1005003636069198.html?UTABTest=aliabtest276336_383090&_randl_currency=EUR&_randl_shipto=ES&src=google&src=google&albch=shopping&acnt=439-079-4345&slnk=&plac=&mtctp=&albbt=Google_7_shopping&gclsrc=aw.ds&albagn=888888&ds_e_adid=597275634909&ds_e_matchtype=&ds_e_device=c&ds_e_network=u&ds_e_product_group_id=296715514933&ds_e_product_id=es1005003636069198&ds_e_product_merchant_id=431200790&ds_e_product_country=ES&ds_e_product_language=es&ds_e_product_channel=online&ds_e_product_store_id=&ds_url_v=2&albcp=17223524136&albag=139444314471&isSmbAutoCall=false&needSmbHouyi=false&gclid=CjwKCAjw14uVBhBEEiwAaufYx5OvFZ_XjKJpl_BuU0KFowhvEDVmXICuN7EiAGLga2vKkaqfYyngyRoCsBAQAvD_BwE&aff_fcid=d051342413cd480397fce1eab26a955f-1654888957535-09173-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=d051342413cd480397fce1eab26a955f-1654888957535-09173-UneMJZVf&terminal_id=c3651ce96daa41c999f247c9baf4fcbf&OLP=1082700408_f_group0&o_s_id=1082700408&afSmartRedirect=y" target="_blank" rel="noopener noreferrer" title="***Please middle click on mouse to open in new tab***&#013Github Markdown does not support opening new pages (github.com/mojombo/github-flavored-markdown/issues/28)">CC2531 downloader cable</a>
* <a href="https://es.aliexpress.com/item/1005003636069198.html?UTABTest=aliabtest276336_383090&_randl_currency=EUR&_randl_shipto=ES&src=google&src=google&albch=shopping&acnt=439-079-4345&slnk=&plac=&mtctp=&albbt=Google_7_shopping&gclsrc=aw.ds&albagn=888888&ds_e_adid=597275634909&ds_e_matchtype=&ds_e_device=c&ds_e_network=u&ds_e_product_group_id=296715514933&ds_e_product_id=es1005003636069198&ds_e_product_merchant_id=431200790&ds_e_product_country=ES&ds_e_product_language=es&ds_e_product_channel=online&ds_e_product_store_id=&ds_url_v=2&albcp=17223524136&albag=139444314471&isSmbAutoCall=false&needSmbHouyi=false&gclid=CjwKCAjw14uVBhBEEiwAaufYx5OvFZ_XjKJpl_BuU0KFowhvEDVmXICuN7EiAGLga2vKkaqfYyngyRoCsBAQAvD_BwE&aff_fcid=d051342413cd480397fce1eab26a955f-1654888957535-09173-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=d051342413cd480397fce1eab26a955f-1654888957535-09173-UneMJZVf&terminal_id=c3651ce96daa41c999f247c9baf4fcbf&OLP=1082700408_f_group0&o_s_id=1082700408&afSmartRedirect=y" target="_blank" rel="noopener noreferrer" title="***Please middle click on mouse to open in new tab***&#013Github Markdown does not support opening new pages (github.com/mojombo/github-flavored-markdown/issues/28)">USB CC2531</a>

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

