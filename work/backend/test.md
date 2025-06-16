---
id: "241504"
aliases:
  - "241504"
tags: []
---

# 241504

czym jest kolektor a czym procesor?

zasada ogólna
Drukarka jest podpięta pod jakieś urządzenie, np stacja robocza. żeby kolektor odbierał dane z drukarki fiskalnej to musi mieć ta drukarka urządzenie nadrzędne (kasa), ip oraz numer unikatowy.

Wymagane jest utworzenie stacji roboczą, drukarke fiskalną (adres ip ).

kolektor pobiera wszystkie dane binarne wydruków fiskalnych z drukarek po IP-ikach,

Jak kolektor pobierze to leci info do kafki o tym co i kiedy zostało pobrane `public const string FiscalPrinterDataCollectingResultTopic = "fiscal-printer-data-collecting-result";`

procesor gdy wykryje dany topic to procesuje nowe i nie przeprocesowane wiadomości

source dir ranges to ile informacji bazowo z drukarki

dir_ranges to co zostało pobrane

processed_ranges to ile informacji które zostały przeprocesowane

wszystkie informacje to przychodzą jako json

dodawanie urządzenia:
Przez UI:

1. lokalizacje ->lokalizacje
2. dodaj nową lokalizacje ->uzupełnij
3. sprzet i oprogramowanie ->urządzenia -> urządzenia
4. nowe urządzenie (stacja robocza) -> uzupełnic dane (aktywne)
5. nowe urządzenie (drukarka fiskalna) ->uzupoełnić dane (model nmp Posnet Thermal HX) -> konfiguracja sieciowa -> powiązane urządzenia (urządzenie nadrzędne to sklep z pkt 1) -> cechy -> numer unikatowy drukarki

komunikaty obługiowane przez procesor ProcessingResultSectionTypes

PosnetPop

CO ZROBIĆ
znaleźć paragon który ma raport donacji
jak się znajdzie to znaleźć

jak to działa
serwisant zrobił raport online
drukuje się na drukarce zmiany konfiguracji serwera

paragnag :)

jak zrobić tabelki????
paragony to jedna tabelka dociągane są informacje o płatnościach
płatności do jednej tabelki
dodać też tabelke na donacje osobna (jest częścią płatności/paragonu)

do ProcessingResultSectionTypes dodać 2 nowe sekcje

- raporty donacji
- płatność

zrobić wszystkie sekcje

Jak brać dane z folderu na potrzeby procesora
postawienie drukarki fiscalnej:
docker stop FSPServer
docker rm FSPServer
docker run -d --name FSPServer -p 2121:21/UDP -v C:\FSP:/var/ftp docker.forcom.com.pl/perspectiv/fsp-server:latest

zmienić uip w drukarce

Musi być folder FSP dokładnie tak jak w ścieżce u góry czyli C:\FSP

odpalenie kafki
docker stop kafka
docker rm kafka
docker run -d --name kafka -it -p 9092:9092 -e KAFKA_ADVERTISED_HOST_NAME=10.60.6.72 -e KAFKA_ADVERTISED_PORT=9092 docker.forcom.com.pl/kafka_forcom
