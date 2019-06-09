Zadanie 1 Rozwiązanie
---------

## 1. Ustalenie netmaski oraz adresów sieci:
  * dla 5000 urządzeń  - ``/19``  - 255.255.224.0
  * dla 500 urządzeń - ``/23`` - 255.255.254.0
  
  Sieć zaczniemy dzielić od LAN2, ponieważ jest w niej większa ilość hostów.
  
  --------------------------------------------------------
  | Sieć | Adres sieci    | Zakres hostów | Adres rozgłoszeniowy |
  | ----- |:------------- |:-------------| :-------------|
  | ``LAN2`` |   ``172.22.128.0/19``    | ``172.22.128.1 - 172.22.159.254 (8 190 hostów)`` | ``172.22.159.255`` |
  | ``LAN1`` |   ``172.22.160.0/23``    | ``172.22.160.1 - 172.22.161.254 (510 hostów)`` | ``172.22.161.255`` |

## 2. Konfiguracja 
 ### a. PC0
 ### b. PC1
 ### c. PC2
## X. Diagram
