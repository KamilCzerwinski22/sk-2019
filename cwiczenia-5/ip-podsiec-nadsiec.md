Podsieci i nadsieci IP
----------------------

adresacja
-----------------------------------------------------
| PC     |  interfejs   | adres  |
| --------- |:-------------| :---------------| 
| ``PC1``   | enp0s3 | 192.168.100.1/24     |
| ``PC-R-1``| enp0s3 | 192.168.100.1/24      |
| ``PC-R-1``| enp0s8 | 192.168.200.1/24    |
| ``PC-R-2``| enp0s3 | 192.168.200.2/24     |
| ``PC-R-2``| enp0s8 | 192.168.0.1/24     |
| ``PC-R-2``| enp0s9 |      |
| ``PC-R-2``| enp0s10 |      |
| ``PC2``| enp0s3 | 192.168.0.22/24     |

routing
-------

| destination | trasa | interfejs  |
| --------- |:-------------| :---------------| 
| ``PC1``     |  | |
| ``default`` | 192.168.100.1 | enp0s3 ``ip route add default via 192.168.100.1`` |
| ``PC-R-1``  |  |        |
| ``192.168.100.0/24`` | 192.168.100.1  | enp0s3      |
| ``192.168.200.0/24`` | 192.168.200.1  | enp0s8      |
| ``192.168.0.0/24`` | 192.168.200.2  | enp0s8      |
| ``192.168.0.64/27`` N| 192.168.200.2  | enp0s8      |
| ``192.168.0.128/27`` N| 192.168.200.2  | enp0s8      |
| ``192.168.0.192/27`` N| 192.168.200.2  | enp0s8      |
| ``PC-R-2``  | ? |       |
| ``192.168.200.0/24`` | 192.168.200.2  | enp0s3      |
| ``192.168.100.0/24`` | 192.168.200.1  | enp0s3      |
| ``192.168.0.64/27`` | 192.168.0.65  | enp0s8      |
| ``192.168.0.128/27`` | 192.168.0.129  | enp0s9      |
| ``192.168.0.192/27`` | 192.168.0.193 | enp0s10      |

nano /etc/network/interfaces
auto enp0s3
iface enp0s3 inet static
  address 192.168.100.1
  netmask 255.255.255.0

auto en0s8
  iface enp0s8 inet static
  address 192.168.200.1
  netmask 255.255.255.0
  up ip route add 192.168.0.0/24 via 192.168.200.2
  down ip route del 192.168.0.0/24
  
  ``do ćwiczen 2``
  

Zadanie
------------

![zadanie 5](over_network.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem
   * W pierwszej kolejności przygotuj ``PC1``, ``PC-R-1``, ``PC-R-2``, ``PC-2``
   * Do konfiguracji wykorzystaj dane z tabeli powyżej
   * Rozszerz istniejącą konfigurację dzieląc istnijącą sieć dla ``PC2`` na 3 podsieci zgodnie z diagramem
   * Przetestuj połączenie pomiędzy wszystkimi elementami sieci ``PC1->PC2`` ``PC1->PC4``
   * Zapewnij permanentną konfigurację, dodając odpowiednie wpisy w plikach konfiguracji

Zadanie do domu
---------------

1. Wykorzystując program dia oraz ikony CISCO
  * Przygotuj diagram powyższej sieci uwzględniając urządzenia tj:
    * ROUTER
    * SWITCH
    * PC
  * Uzupełnij diagram o adresację sieci oraz poszczególnych urządzeń
  
![zadanie do domu 5](diagram_network.svg)
  
