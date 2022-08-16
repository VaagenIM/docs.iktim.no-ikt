---
title: 01. Dataformater
aliases: [Dataformater,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Database
  - JSON
  - CSV
  - SQL
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:12
---
# Dataformater
Når vi sender mye data mellom maskiner, bruker man ofte et eget format som er egnet for større mengder data. En av de vanligste formatene som er brukt, er [[JSON]].

## JSON
Forklaring kommer! I Python bruker vi blant annet JSON formatet når vi lager [[02 Dictionaries]].

```json
{  
  "users": [  
    {  
      "userId": 1,  
      "firstName": "Krish",  
      "lastName": "Lee",  
      "phoneNumber": "123456",  
      "emailAddress": "krish.lee@learningcontainer.com"  
    },  
    {  
      "userId": 2,  
      "firstName": "racks",  
      "lastName": "jacson",  
      "phoneNumber": "123456",  
      "emailAddress": "racks.jacson@learningcontainer.com"  
    },  
    {  
      "userId": 3,  
      "firstName": "denial",  
      "lastName": "roast",  
      "phoneNumber": "33333333",  
      "emailAddress": "denial.roast@learningcontainer.com"  
    },  
    {  
      "userId": 4,  
      "firstName": "devid",  
      "lastName": "neo",  
      "phoneNumber": "222222222",  
      "emailAddress": "devid.neo@learningcontainer.com"  
    },  
    {  
      "userId": 5,  
      "firstName": "jone",  
      "lastName": "mac",  
      "phoneNumber": "111111111",  
      "emailAddress": "jone.mac@learningcontainer.com"  
    }  
  ]  
}
```
Eksempel fra https://www.learningcontainer.com/sample-json-file/

## CSV
CSV står for Comma-separated-values. Enkelt å greit så brukes CSV til å lagre verdier som maskiner klarer å lese. 

Største ulempen med CSV er at det ikke er lett for mennesker å lese, men CSV er meget plassbesparende. Her må maskinen vite på forhånd, altså forhåndsbestemme, hvilken verdi som tilhører hvor. I eksempelet til JSON så har vi 5 verdier, som ser slik ut:
- userID
- firstName
- lastName
- phoneNumber
- emailAddress

I CSV vil filen se slik ut:
```
1,Krish,Lee,123456,krish.lee@learningcontainer.com,
2,racks,jacson,123456,racks.jacson@learningcontainer.com,
3,denial,roast,33333333,denial.roast@learningcontainer.com,
osv..
```