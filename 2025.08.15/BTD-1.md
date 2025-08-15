
Note there are two signal types for BTD-1 - the first is unvalidated, the second enforses the BTD-1 json schema
# Payload definitions
## Pre-notification Payload 


The technical definition can be found [here](https://github.com/border-trade-demonstrators/btd-1/blob/main/isn-btd-1.edn) and a description of the fields is below.

| Field name | Description | Data type | Optionality | Notes |
| --- | --- | --- | --- | --- |
CHED Numbers|A set of CHED identifiers|CHED-P or CHED-D|Optional||
cnCodes|Classification of the goods reference |String |Optional ||
Commodity Description|Plain text description of goods |String|Required|
Country Of Origin|Country goods/sample originated from|ISO3166 (E.G. GB)|Required||
Exporter EORI|Exporter registration number |String|Optional ||
Importer EORI|Importer registration number |String|Optional ||
Location|Location of where goods are loaded|String |Optional ||
Mode|The goods movement mode|Enumeration (only RORO supported in this pilot)|Required||
Unit Identification|A list of identifiers and identifier types (as key/value pairs) for an incoming unit.|May be multiples from a set of identifiers (e.g. container number trailer registration number/VRN/ TRN etc)|Required||
Trailer registration number|Registration number of the trailer|String (e.g. WGM033P)|Required||

Note for the purpose of this pilot signal we have agreed to use the metadata "start" item is being used to hold an ETA for the movement.

Here is example of the JSON that would be used to publish a pre-notification signal to the API

``` json
{
  "h": "event",
  "name": "chicken and beef (movement ref: 955R)",
  "start": "2024-08-27T09:00:00Z",
  "summary": "moving to PortA with ETA 2024-08-28T09:00:00Z",
  "category": [
    "pre-notification",
    "isn@btd-1.info-sharing.network"
  ],
  "payload": {
    "chedNumbers": [
      "CHEDP.GB.2024.1234567"
    ],
    "cnCodes": [
      "1602"
    ],
    "commodityDescription": "Other prepared or preserved meat",
    "countryOfOrigin": "PL",
    "exporterEORI": "PL12300000004358Z",
    "importerEORI": "GB123012792073",
    "location": "Rolpek 2 (50.9457, 16.3523)",
    "mode": "RORO",
    "unitIdentification": {
      "trailerRegistrationNumber": "WGM1234P"
    }
  }
}
```
