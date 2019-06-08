Struktura adresu IP
-------------------

```192.168.100.192```
```255.255.255.0```

Adres sieci
-----------

1. Ip i maska sieci na BIN
2. Operacja AND na obu
3. Zamiana na DEC

Adres rozgłoszeniowy
-----------

1. Na masce sieci w BIN robimy operacje NOT
2. Konwercja maski do DEC
3. Dodanie do adresu sieci negacji maski w DEC

lub

1. Obliczenie adresu sieci
2. Negacja maski sieci
3. Binarna suma maski i adresu sieci


Podział na równą ilość podsieci
-------------------------------

```2^S >= n```

Chcemy 7 -> 2^3 >= 7

Maska -> 255.255.255.11100000 -> 255.255.255.224 -> /27

Liczba hostów - 2^(32-maska)-2

Wprowadzenie
------------

------------------------------
| dziesiętnie |  binarnie   | 
| --------- |:-------------| 
| ``10``  | 00001010 | 
| ``92``  | 01011100 | 
| ``37``  | 00100101 | 
| ``240`` | 11110000 | 
| ``192`` | 11000000 | 
| ``255`` | 11111111 | 
| ``128`` | 10000000 | 
| ``168`` | 10101000 | 


------------------------------
| binarnie |  dziesiętnie   | 
| --------- |:-------------| 
| ``00100000``  | 32 | 
| ``11111000``  | 248 | 
| ``10100000``  | 160 | 
| ``00110000`` | 48 | 
| ``10101100`` | 172 | 
| ``01000000`` | 64 | 
| ``11111100`` | 252 | 
| ``01100010`` | 98 | 
 
Notacja CIDR
------------
 
------------------------------
| maska |  /(X) x - liczba bitów   | 
| --------- |:-------------| 
| ``255.255.255.0``   | /24 | 
| ``255.128.0.0``     | /9 | 
| ``255.255.252.0``   | /22 | 
| ``255.255.254.0``   | /23 | 
| ``255.255.255.240`` | /28 | 
| ``255.240.0.0``     | /12 | 

------------------------------
| CIDR |  Maska   | 
| --------- |:-------------| 
| ``/8``    | 255.0.0.0 | 
| ``/20``   | 255.255.240.0 | 
| ``/30``   | 255.255.255.252 | 
| ``/16``   | 255.255.0.0 | 
| ``/27``   | 255.255.255.224 | 
| ``/11``   | 255.224.0.0 | 


Liczba hostów
-------------

------------------------------
| sieć |  liczba   | 
| --------- |:-------------| 
| ``10.0.0.0/8``    | 16777214 | 
| ``172.16.0.0/16``   | 65534 | 
| ``192.168.1.0/24``   | 254 | 
| ``192.168.1.0/27``   | 30 | 
| ``192.168.1.0/29``   | 6 | 
| ``192.168.1.0/31``   | 0 | 

* liczba 0 w masce?


Parametry na podstawie adresu
-----------------------------

Mając dany adres hosta i maskę znajdź:
  * adres sieci
  * początkowy adres hosta w sieci
  * liczbę hostów w zadanej podsieci ```2^(32 bity - bity maski maska) - 2 (siec i broadcast)```
  * końcowy zakres adresu hosta w sieci
  * adres rozgłoszeniowy
  
  ------------------------------
| Parametr |  wartość   | 
| --------- |:-------------| 
| ``ip``    | 192.168.1.145 | 
| ``maska``   | 255.255.255.128 | 
| ``adres sieci``   | 192.168.1.128 |
| ``liczba hostów``   | 126 |
| ``host - min``   | 192.168.1.129 | 
| ``host - max``   | 192.168.1.254 | 
| ``broadcast``   | 192.168.1.255 | 
 
Zadanie
------------

0. Znajdz wszystkie parametry sieci dla hosta o adresie 172.16.128.64 / 16
  
------------------------------
| Parametr |  wartość   | 
| --------- |:-------------| 
| ``ip``    | 172.16.128.64 | 
| ``maska``   | 255.255.0.0 | 
| ``adres sieci``   | 172.16.0.0 |
| ``liczba hostów``   | 65 534‬ |
| ``host - min``   | 172.16.0.1 | 
| ``host - max``   | 172.16.255.254 | 
| ``broadcast``   | 172.16.255.255 | 

1.
  * Podziel sieć ```192.168.1.0``` na 16 równych podsieci
  
  ``2^4 >= 16``    ``14*16+16(adres sieci)+16(adres rozgłoszeniowy) = 256``
  
----------------------------------------------------------
| Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| --------- |:-------------|  :---------------|
| ``192.168.1.0``    | 192.168.1.1 - 192.168.1.14 (14 hostów) | 192.168.1.15 |
| ``192.168.1.16``   | 192.168.1.17 - 192.168.1.30 (14 hostów) | 192.168.1.31 |
| ``192.168.1.32``   | 192.168.1.33 - 192.168.1.46 (14 hostów) | 192.168.1.47 |
| ``192.168.1.48``   | 192.168.1.49 - 192.168.1.62 (14 hostów) | 192.168.1.63 |
| ``192.168.1.64``   | 192.168.1.65 - 192.168.1.78 (14 hostów) | 192.168.1.79 |
| ``192.168.1.80``   | 192.168.1.81 - 192.168.1.94 (14 hostów) | 192.168.1.95 |
| ``192.168.1.96``   | 192.168.1.97 - 192.168.1.110 (14 hostów) | 192.168.1.111 |
| ``192.168.1.112``   | 192.168.1.113 - 192.168.1.126 (14 hostów) | 192.168.1.127 |
| ``192.168.1.128``   | 192.168.1.129 - 192.168.1.142 (14 hostów) | 192.168.1.143 |
| ``192.168.1.144``   | 192.168.1.145 - 192.168.1.158 (14 hostów) | 192.168.1.159 |
| ``192.168.1.160``   | 192.168.1.161 - 192.168.1.174 (14 hostów) | 192.168.1.175 |
| ``192.168.1.176``   | 192.168.1.177 - 192.168.1.190 (14 hostów) | 192.168.1.191 |
| ``192.168.1.192``   | 192.168.1.193 - 192.168.1.206 (14 hostów) | 192.168.1.207 |
| ``192.168.1.208``   | 192.168.1.209 - 192.168.1.222 (14 hostów) | 192.168.1.223 |
| ``192.168.1.224``   | 192.168.1.225 - 192.168.1.238 (14 hostów) | 192.168.1.239 |
| ``192.168.1.240``   | 192.168.1.241 - 192.168.1.254 (14 hostów) | 192.168.1.255 |



2. 
  * Podziel sieć ``/16`` na 6 równych podsieci.
  ``2^3=8, tworzymy 8 podsieci ponieważ 6 nie jest potęgą 2. Utworzymy 6 sieci, 2 będą nieuzywane``
  

  ----------------------------------------------------------
| Adres sieci | zakres hostów | Adres Rozgłoszeniowy |
| --------- |:-------------| :---------------|
| ``172.16.0.0`` | 172.16.0.1 - 172.16.31.254 (8190 hostów) | 172.16.31.255 |
| ``172.16.32.0`` | 172.16.32.1 - 172.16.63.254 (8190 hostów) | 172.16.63.255 |
| ``172.16.64.0`` | 172.16.64.1 - 172.16.95.254 (8190 hostów) | 172.16.95.255 |
| ``172.16.96.0`` | 172.16.96.1 - 172.16.127.254 (8190 hostów) | 172.16.127.255 |
| ``172.16.128.0`` | 172.16.128.1 - 172.16.159.254 (8190 hostów) | 172.16.159.255 |
| ``172.16.160.0`` | 172.16.160.1 - 172.16.191.254 (8190 hostów) | 172.16.191.255 |

3. 
  * Podziel sieć ``192.168.1.0/24``, tak aby każda podsieć miała 11 użytkowników.
  
  2^h-2 >= liczba uzytkowników, czyli w tym wypadku h=4 bo 2^4-2(16) >= 11. Nie da sie podzielić idealnie na 11 użytkowników, więc podzielimy na najbliższą większą liczbę czyli na podsieci zawierające po 14 użytkowników (16 - adres sieci - adres rozgłoszeniowy = 14).
  Maska dla nowych podsieci będzie wynosiła 28 bo maska+h, czyli 24+4=28.
  Takich podsieci będzie można utworzyć maksymalinie 16, bo 2^h = 2^4 = 16
  
  ----------------------------------------------------------
| Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| --------- |:-------------|  :---------------|
| ``192.168.1.0/28``    | 192.168.1.1 - 192.168.1.14 (14 hostów) | 192.168.1.15 |
| ``192.168.1.16/28``   | 192.168.1.17 - 192.168.1.30 (14 hostów) | 192.168.1.31 |
| ``192.168.1.32/28``   | 192.168.1.33 - 192.168.1.46 (14 hostów) | 192.168.1.47 |
| ``192.168.1.48/28``   | 192.168.1.49 - 192.168.1.62 (14 hostów) | 192.168.1.63 |
| ``192.168.1.64/28``   | 192.168.1.65 - 192.168.1.78 (14 hostów) | 192.168.1.79 |
| ``192.168.1.80/28``   | 192.168.1.81 - 192.168.1.94 (14 hostów) | 192.168.1.95 |
| ``192.168.1.96/28``   | 192.168.1.97 - 192.168.1.110 (14 hostów) | 192.168.1.111 |
| ``192.168.1.112/28``   | 192.168.1.113 - 192.168.1.126 (14 hostów) | 192.168.1.127 |
| ``192.168.1.128/28``   | 192.168.1.129 - 192.168.1.142 (14 hostów) | 192.168.1.143 |
| ``192.168.1.144/28``   | 192.168.1.145 - 192.168.1.158 (14 hostów) | 192.168.1.159 |
| ``192.168.1.160/28``   | 192.168.1.161 - 192.168.1.174 (14 hostów) | 192.168.1.175 |
| ``192.168.1.176/28``   | 192.168.1.177 - 192.168.1.190 (14 hostów) | 192.168.1.191 |
| ``192.168.1.192/28``   | 192.168.1.193 - 192.168.1.206 (14 hostów) | 192.168.1.207 |
| ``192.168.1.208/28``   | 192.168.1.209 - 192.168.1.222 (14 hostów) | 192.168.1.223 |
| ``192.168.1.224/28``   | 192.168.1.225 - 192.168.1.238 (14 hostów) | 192.168.1.239 |
| ``192.168.1.240/28``  | 192.168.1.241 - 192.168.1.254 (14 hostów) | 192.168.1.255 |
4. 
  * Podziel sieć ``10.0.0.0/8`` na 5 podsieci. 
    * Podsieć A ma posiadać 100 000 użytkowników,
    
    chcemy mieć w sieci A 100k użytkowników, a więc 2^h-2 >= 100k. H w tym wypadku będzie wynosiło 17, bo 2^17-2 = 131 070.
    32-17 = 15, czyli maska dla sieci A będzie ``/15``, a więc:
   ----------------------------------------------------------
| Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| --------- |:-------------|  :---------------|
| ``10.0.0.0/15`` | 10.0.0.1 - 10.1.255.254 (131 070 hostów) | 10.1.255.255 |


* B – 10 000 użytkowników,
    
    a więc 2^h-2 > 10k. H w tym przypadku będzie wynosiło 14, bo 2^14-2 = ‭16 382‬. 32-14 = 18, czyli maska dla sieci B będzie ``/18``.
    Adres sieci będzie kolejnym w kolejności adresem po broadcast'ie poprzedniej sieci, czyli skoro tam adres rozgłoszeniowy wynosił 10.1.255.255, adres sieci B będzie wynosił 10.2.0.0.
    
    ----------------------------------------------------------
| Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| --------- |:-------------|  :---------------|
| ``10.2.0.0/18``    | 10.2.0.1 - 10.2.63.254 (16 382 hostów) | 10.2.63.255 | 
    * C – 3 000 użytkowników,
    a więc 2^h-2 > 3k, czyli H wynosi 12, a maska sieci będzie wynosiła ``/20``. Analogicznie do poprzednich obliczam broadcast, zakres i adres sieci:
    
    ----------------------------------------------------------
| Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| --------- |:-------------|  :---------------|
| ``10.2.64.0/20``    | 10.2.64.1 - 10.2.79.254 (4 094 hostów) | 10.2.79.255 |


   * D – 500 użytkowników,
   a więc 2^h-2 > 500, czyli H wynosi 9, a maska ``/23``. Analogicznie:
   
   ----------------------------------------------------------
| Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| --------- |:-------------|  :---------------|
| ``10.2.80.0/23``    | 10.2.80.1 - 10.2.81.254 (510 hostów) | 10.2.81.255 |


   * E – 2 użytkowników,
   a więc 2^h-2 > 2, czyli H wynosi 2, a maska sieci będzie wynosiła ``/30``. Analogicznie:
    
    ----------------------------------------------------------
| Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| --------- |:-------------|  :---------------|
| ``10.2.82.0/30``    | 10.2.82.1 - 10.2.82.2 (2 hostów) | 10.2.82.3 |
    
``żeby sprawdzić kolejny adres sieci trzeba maske zamienić na binarny, i zależnie od oktetu i miejsca w którym znajduje się ostatnia jedynka dopasowywać. np jeśli przy ostatniej 1 w binarnym jest 16 i znajduje się ona w 3 oktecie, a nasz adres to 10.0.0.0, to adres kolejnej podsieci będzie 10.0.16.0``
