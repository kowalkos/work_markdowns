---
id: dodawanie-sklepu-m4c
aliases:
  - Dodawanie sklepu M4C
tags: []
---

# Dodawanie sklepu M4C

1. endpoint => <http://localhost:5999/market4cloud-infrastructure/test/v1/business-units>
2. Dane: clientId = m4c-ui
3. body:
   unitId= numer sklepu który chcemy dodawać, zmiana musi być również w `json queues:[ Topic:'some number']`

```json
{
  "unitId": "1000",
  "businessUnitType": "1",
  "databaseConnections": [
    {
      "connectionStringName": "dev_storespecific_sales_1"
    },
    {
      "connectionStringName": "dev_storespecific_masterdata_1"
    },
    {
      "connectionStringName": "dev_storespecific_promotions_1"
    },
    {
      "connectionStringName": "dev_storespecific_pointofsaleintegration_1"
    },
    {
      "connectionStringName": "dev_storespecific_pricelabels_1"
    },
    {
      "connectionStringName": "dev_storespecific_warehouse_1"
    },
    {
      "connectionStringName": "dev_storespecific_user_1"
    }
  ],
  "queues": [
    {
      "Topic": "market4cloud.1000.developers.common.inbox",
      "Strategy": "InboxConsumingStrategy"
    },
    {
      "Topic": "market4cloud.1000.store-imports",
      "Strategy": "StandardizedMessageConsumingStrategy"
    }
  ]
}
```

4. Dodanie <http://localhost:5999/market4cloud-master-data-common/test/v1/store> clientId jak powyżej body mamy poniżej `code = store`

```json
{
  "code": "1000",
  "store": {
    "name": "Biedronka",
    "postBox": "1",
    "phone": "789789123",
    "status": "1"
  },
  "tax": {
    "taxIdentificationNumberPrefix": "PL",
    "taxIdentificationNumber": "7811692277",
    "eoriNumber": "1",
    "companyName": "Biedronka"
  },
  "address": {
    "country": {
      "name": "Polska",
      "twoLetterCode": "PL"
    },
    "city": "Poznan",
    "postalCode": "11-111",
    "postTown": "string",
    "street": "Poznańska",
    "buildingNumber": "1",
    "flatNumber": "1",
    "gln": "string"
  }
}
```
