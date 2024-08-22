---
id: tworzenieparagonw
aliases:
  - TworzenieParagonów
tags: []
---

# TworzenieParagonów

## Edycja paragonu

1. Otworzyć narzędzie do dekompresji danych paragonu: [dekompress](https://codebeautify.org/gzip-decompress-online)(pamiętać żeby używać tylko angielskich znaków)
2. Po konwersji należy zmienić

   - `ReceiptId` (numer paragonu) na pomniejszony o 1
   - `TransactionNumber` na numer paragonu
   - `ReceiptGuid` - GUID który zawsze musi być unikalny
   - `CustomerNip` - musi znajdować się po receipt guid i przed site info
   - `SiteId` - jedna z trzech wartości opisująca nr sklepu, brana pod uwage przy zapisie paragonu do M4C (4110)

3. W paragonie można również zmienić jego pozycje i inne atrybuty

4. Utworzyć plik `.txt` zawierający zdekompresowane dane

## Ponowne szyfrowanie danych

1. Pobrać folder ze ścieżki np `\\synek\serwis\jnielacny\kompresor_paragony`
2. Należy otworzyć aplilacje `b64gz.exe` oraz wybrać plik ze zdekompresowanymi danymi paragonu. Zostanie utworzony plik `result.txt`
3. Otwieramy docelowy plik txt/xml z paragonem, zawartość DATA podmieniamy na to co znajduje się w pliku result.txt, pozostałe wiersze:

   - SessionGuid - 1b2eafc6-9f31-40b4-c4a5-7fdba7a14d33 - zawsze musi byc unikalny
   - TransactionNumber - 506 - zmieniamy na numer paragonu, taki jak w DATA

## Dodanie paragonu do środowiska z użyciem swaggera

1. Otwieramy [swagger](http://localhost:5999/index.html)
2. Wyszukujemy `/market4cloud-store-sales/{clientId}/v1/sites/{siteId}/receipt`
3. Wypełniamy wymagane propy
   - siteId - np `4110`
   - clientId - np `test`
4. wstawiamy xml

### Przykładowy xml

```
 <?xml version="1.0" encoding="UTF-8"?>
 <SaveReceipt>
 <SessionGuid>1b2eafc6-9f31-6814-c4a5-7fdba7a14d79</SessionGuid>
  <TransactionNumber>681</TransactionNumber>
  <TransactionDate>
    <Year>2024</Year>
    <Month>8</Month>
    <Day>6</Day>
    <Hour>19</Hour>
    <Minute>0</Minute>
    <Second>0</Second>
  </TransactionDate>
  <CashierShiftId>100</CashierShiftId>
  <CompressedReceipt>
    <Data>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</Data>
  </CompressedReceipt>
</SaveReceipt>
```
