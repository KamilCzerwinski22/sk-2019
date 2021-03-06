Ustawianie parametrów sieci ip
------------------------------

* stan interfejsu
    * interfejs up
    * interfejs down
* adresacja
    * dodaj adres
    * zmień adres
    * usuń adres
* routing
    * dodaj trasę default
    * dodaj trasę przez bramę
    * dodaj trasę przez interfejs
    * usuń trasę
    * zmień trasę
    * pobierz trasę dla adresu
* adresacja fizyczna
    * pokaż adresy interfejsów dostępnych w sieci
    * pokaż adresy dla konkretnego interfejsu
     


ip 
-------------------------
| subcommand    |  polecenie   | opis  |
| ------------- |:-------------| :---------------| 
|   ``addr``    |                               | infirmacje o adresacji i własnościach interfejsów |
|               |   ``ip addr``                 | informacja o wszystkich interfejsach              |
|               |   ``ip addr show dev enp0s3`` | informacja o konkretnym interfejsie               |
|   ``link``    |   ``ip link set/show``  | Polecenie służy do zmiany ustawień istniejących interfejsów/wyświetlenie konfiguracji urządzen sieciowych |
|   ``route``   |  ``ip route add/show`` | Zarządzanie tablicami routingu wewnątrz jądra. Można dodawac, modyfikowac, usuwac trasy etc.|
|   ``maddr``   | ``ip maddr add/show/del``   |Służy do wyświetlania i zarządzania rozsyłaniem adresów / np. ``ip maddr show enp0s3`` pokaże info dla enp0s3|
|   ``neigh``   |  ``ip neigh add/del/show/change`` | Polecenie sluży do zarządzania oraz wyświetlania tablicy sąsiedztwa|
|   ``help``    |  ``ip help``| wyświetli dostepne informacje o poleceniu ip|

Zadanie
------------

![zadanie 3](cwiczenia3.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem, 
   * Przetestuj połączenie poleceniem ping (ping z cmd windowsa na 172.16.100.6 i 172.16.100.7 działa, zrobione na 2 centosach, debian odmawiał posłuszeństwa)
![](1.jpg)
![](4.jpg)
![](5.png)
2.
   * Zainstaluj na komputerze ``PC1`` serwer programu ``HTTP CHAT`` dostępnego pod adresem ``https://github.com/jkanclerz/http-chat``
   * Przetestuj komunikację wysyłając wiadomość z komputera ``PC2``, upewnij się czy jest widoczna w konsoli serwera
![](3.jpg)
3.
   * Dodaj do istniejącej sieci komputer ``PC3`` pod kontroloą systemu windows
   * Skonfiguruj ``PC3`` zgodnie z poniższym diagramem
   * Zweryfkuj połączenie kożystając z przeglądarki, odwiedzając graficzny interfejs ``HTTP CHAT`` pod adresem ``http://172.16.100.10:8888`` > u mnie ``http://172.16.100.6:8888``
   
 
   * Przygotuj dokumentację pisemno obrazkową z wykonania zadania w formacie ``markdown`` zamieść ją w serwisie ``github.com`` obok obocnego tematu ``cwiczenia-3``
![](2.jpg)

![zadanie 3.1](cwiczenia3.1.svg) 
