# Demos do Obradoiro SDR

## Receptor e transmisor FM

Estes son os flowgraphs que construímos paso a paso o primeiro día do obradoiro.

A demo de recepción FM pódese adaptar para o uso co pincho RTL-SDR cambiando únicamente o bloque Source.

Nos flowgraphs de transmisión, hai que cambiar as rutas dos ficheiros `.wav` que usemos como orixe de audio. Ou tamén podedes intentar recoller o sonido do micrófono...

## Receptor ADS-B

Para a recepción do sinal de avións non utilizamos un flowgraph de GNURadio, senon que executamos una aplicación específica deseñada para funcionar cos pinchos RTL-SDR. 

Podedes atopala neste outro repositorio, xunto coas instruccións para poñelo a funcionar:
https://github.com/MalcolmRobb/dump1090

## Transmisor DVB-T

Na demo de DVB-T, o Transport Stream (vídeo MPEG2) que usamos de exemplo pode descargarse da web de Ron Economos:
```
wget http://www.w6rz.net/adv8dvbt23qam64.ts
```

E para recibir o video co pincho DVB-T, cambiando a frecuencia se é preciso:
```
vlc dvb://frequency=509000000
```

O flowgraph inclúe os Sink para o uso co LimeSDR Mini e co HackRF. Só hai que activalos ou desactivalos en cada caso.

Na Wikipedia podedes ler máis sobre cómo funciona o estándar DVB-T (https://en.wikipedia.org/wiki/DVB-T), e se buscades no propio repositorio de GNURadio tamén atoparedes flowgraphs para DVB-T2 e DVB-S2 (satélite).

## Receptor NOAA (APT)

Nesta demo temos que acordarnos de correxir o desvío de frecuencia producido polo efecto Doppler manualmente.

Deixamos temporalmente aquí un ficheiro de captura de exemplo:
https://we.tl/t-jvXGstTl2D

Antes de executar o flowgraph, temos que cambiar a variable `prefix` para indicar o directorio de saída e a ruta do bloque Source para apuntar a un ficheiro de captura. Para convertir o ficheiro `.dat` resultante a `.png` podedes facelo usando ImageMagick:
```
convert -size 2080x909 -depth 8 gray:CAPTURA.dat CAPTURA.png
```

Aquí tamén podedes atopar máis información sobre a modulación das imaxes de NOAA:
https://en.wikipedia.org/wiki/Automatic_picture_transmission