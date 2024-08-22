---
id: stawianierodowiska
aliases:
  - Stawianie_Środowiska
  - Stawianie Środowiska
tags: []
---

# Stawianie Środowiska

## Wymagania

Należy zapoznać się z [Konfiguracją lokalnego środowiska](https://confluence.forcom.com.pl/display/M4/M4C+-+How+to+start+M4C+in+local+environment)

Zalecane jest żeby [m4cLauncher.zip](https://confluence.forcom.com.pl/download/attachments/61115572/m4cLauncher.zip?version=11&modificationDate=1722001783484&api=v2) został wypakowany w lokalizacji naszego lokalnego repozytorium M4C (W tym przypadku może zostać pominięty krok Update M4C z [Konfiguracją lokalnego środowiska](https://confluence.forcom.com.pl/display/M4/M4C+-+How+to+start+M4C+in+local+environment))

### Dla wersji M4C v6 należy nadmienić następujące konfiguracje

- należy podmienić zawartość pliku `m4c-docker-compose.yaml`, który bedzie zawarty w [m4cLauncher.zip] na zawartość tak samo nazwanego pliku przypiętego do tej dokumentacji
- należy podmienić zawartość pliku `sources/Configuration/Forcom.Market4Cloud.Configuration/Configuration/configuration.yaml` na zawartość tak samo nazwanego pliku przypiętego do tej dokumentacji

### Dla wersji M4C > 0.6 nie trzeba wykonywać powyższych kroków

### Stawianie środowiska

1. Należy wykonać wyczyszczenie builda dla aktualnego repozytorium
2. Z konsoli w lokalizacji Root repozytorium (jeśli wypakowaliśmy tutaj [m4cLauncher.zip]) należy wywołać polecenie `python m4cServices.py [start|stop|restart]`
3. Należy wybudować solucje M4C
4. Z konsoli w lokalizacji Root repozytorium należy wywołać polecenie `python m4cLauncher.py` lub uruchomić aplikacje z poziomu wybranego IDE
