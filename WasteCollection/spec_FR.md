Entité : WasteCollection  
=======================
  

[Licence ouverte] (https://github.com/smart-data-models//dataModel.WasteManagement/blob/master/WasteCollection/LICENSE.md)  

[document généré automatiquement] (https://docs.google.com/presentation/d/e/2PACX-1vTs-Ng5dIAwkg91oTTUdt8ua7woBXhPnwavZ0FxgR8BsAI_Ek3C5q97Nd94HS8KhP-r_quD4H0fgyt3/pub?start=false&loop=false&delayms=3000#slide=id.gb715ace035_0_60)  

Description globale : **Un ramassage de conteneur à déchets**  

version : 0.1.0  


## Liste des propriétés  


- `RFID_chip`: Donne l'ID de la puce RFID du conteneur.
- `annotations`: Annotations sur l'élément  
- `binId`: Id de la poubelle  
- `binCollectDatetime`: Date et heure complète de la collecte du container
- `description`: Une description de cet article  
- `fillingLevel`: Niveau de remplissage du conteneur  
- `fillingWeight`: Poid de remplissage du conteneur  
- `id`: Identifiant unique de l'entité  
- `license_plate`: Donne le numéro de la plaque d'immatriculation du véhicule. Identique à : Champ 'license_plate' du GTFS Realtime message-VehicleDescriptor (https://developers.google.com/transit/gtfs-realtime/reference#message-vehicledescriptor)  
- `wasteDumpsterId`: ID de la benne effecuant la collecte du conteneur.
- `location`: Référence Geojson à l'élément. Il peut s'agir d'un point, d'une ligne, d'un polygone, d'un point multiple, d'une ligne multiple ou d'un polygone multiple.  
- `name`: Le nom de cet élément.  
- `seeAlso`: liste d'uri pointant vers des ressources supplémentaires sur l'élément  
- `serialNumber`: Numéro de série du conteneur.  
- `source`: Une séquence de caractères donnant la source originale des données de l'entité sous forme d'URL. Il est recommandé d'utiliser le nom de domaine entièrement qualifié du fournisseur source ou l'URL de l'objet source.  
- `loaderGarbageSide`: Equipement de levé utilisé.  
  

Propriétés requises  
- `id`  
- `location`  
- `type`  

## Description des propriétés du modèle de données  

Classés par ordre alphabétique (cliquez pour plus de détails)  
<details><summary><strong>full yaml details</strong></summary>    

```yaml  
WasteCollection:
  description: 'A waste collection'
  properties:
    RFID_chip:
      description: 'Gives the ID of the RFID chip.'
      type: string
      x-ngsi:
        model: https://schema.org/Text
        type: Property
    annotations:
      description: 'Annotations about the item'
      items:
        type: string
      type: array
      x-ngsi:
        model: https://schema.org/Text
        type: Property
    binId:
      description: 'Id of the waste carrying bin'
      type: string
      x-ngsi:
        model: https://schema.org/Text
        type: Property
    binCollectDatetime:
      description: 'Date and time when the bin was collected'
      format: date-time
      type: string
      x-ngsi:
        model: https://schema.org/Text
        type: Property
    description:
      description: 'A description of this item'
      type: string
      x-ngsi:
        type: Property
    fillingLevel:
      description: 'Filling level of the container'
      maximum: 1
      minimum: 0
      type: number
      x-ngsi:
        model: https://schema.org/Number
        type: Property
    fillingWeight:
      description: 'Filling level of the container'
      minimum: 0
      type: number
      x-ngsi:
        model: https://schema.org/Number
        type: Property
    id:
      anyOf: &wastecollection_-_properties_-_owner_-_items_-_anyof
        - description: 'Property. Identifier format of any NGSI entity'
          maxLength: 256
          minLength: 1
          pattern: ^[\w\-\.\{\}\$\+\*\[\]`|~^@!,:\\]+$
          type: string
        - description: 'Property. Identifier format of any NGSI entity'
          format: uri
          type: string
      description: 'Unique identifier of the entity'
      x-ngsi:
        type: Property
    license_plate:
      description: "Gives the License Plate number of the vehicle. SameAs: 'license_plate' field from GTFS Realtime message-VehicleDescriptor (https://developers.google.com/transit/gtfs-realtime/reference#message-vehicledescriptor)"
      type: string
      x-ngsi:
        model: https://schema.org/Text
        type: Property
    wasteDumpsterId:
      description: "Id of the waste dumpster"
      type: string
      x-ngsi:
        model: https://schema.org/Text
        type: Property
    location:
      description: 'Geojson reference to the item. It can be Point, LineString, Polygon, MultiPoint, MultiLineString or MultiPolygon'
      oneOf:
        - description: 'Geoproperty. Geojson reference to the item. Point'
          properties:
            bbox:
              items:
                type: number
              minItems: 4
              type: array
            coordinates:
              items:
                type: number
              minItems: 2
              type: array
            type:
              enum:
                - Point
              type: string
          required:
            - type
            - coordinates
          title: 'GeoJSON Point'
          type: object
        - description: 'Geoproperty. Geojson reference to the item. LineString'
          properties:
            bbox:
              items:
                type: number
              minItems: 4
              type: array
            coordinates:
              items:
                items:
                  type: number
                minItems: 2
                type: array
              minItems: 2
              type: array
            type:
              enum:
                - LineString
              type: string
          required:
            - type
            - coordinates
          title: 'GeoJSON LineString'
          type: object
        - description: 'Geoproperty. Geojson reference to the item. Polygon'
          properties:
            bbox:
              items:
                type: number
              minItems: 4
              type: array
            coordinates:
              items:
                items:
                  items:
                    type: number
                  minItems: 2
                  type: array
                minItems: 4
                type: array
              type: array
            type:
              enum:
                - Polygon
              type: string
          required:
            - type
            - coordinates
          title: 'GeoJSON Polygon'
          type: object
        - description: 'Geoproperty. Geojson reference to the item. MultiPoint'
          properties:
            bbox:
              items:
                type: number
              minItems: 4
              type: array
            coordinates:
              items:
                items:
                  type: number
                minItems: 2
                type: array
              type: array
            type:
              enum:
                - MultiPoint
              type: string
          required:
            - type
            - coordinates
          title: 'GeoJSON MultiPoint'
          type: object
        - description: 'Geoproperty. Geojson reference to the item. MultiLineString'
          properties:
            bbox:
              items:
                type: number
              minItems: 4
              type: array
            coordinates:
              items:
                items:
                  items:
                    type: number
                  minItems: 2
                  type: array
                minItems: 2
                type: array
              type: array
            type:
              enum:
                - MultiLineString
              type: string
          required:
            - type
            - coordinates
          title: 'GeoJSON MultiLineString'
          type: object
        - description: 'Geoproperty. Geojson reference to the item. MultiLineString'
          properties:
            bbox:
              items:
                type: number
              minItems: 4
              type: array
            coordinates:
              items:
                items:
                  items:
                    items:
                      type: number
                    minItems: 2
                    type: array
                  minItems: 4
                  type: array
                type: array
              type: array
            type:
              enum:
                - MultiPolygon
              type: string
          required:
            - type
            - coordinates
          title: 'GeoJSON MultiPolygon'
          type: object
      x-ngsi:
        type: Geoproperty
    name:
      description: 'The name of this item.'
      type: string
      x-ngsi:
        type: Property
    seeAlso:
      description: 'list of uri pointing to additional resources about the item'
      oneOf:
        - items:
            format: uri
            type: string
          minItems: 1
          type: array
        - format: uri
          type: string
      x-ngsi:
        type: Property
    serialNumber:
      description: 'Serial number of the container.'
      type: string
      x-ngsi:
        model: https://schema.org/serialNumber
        type: Property
    source:
      description: 'A sequence of characters giving the original source of the entity data as a URL. Recommended to be the fully qualified domain name of the source provider, or the URL to the source object.'
      type: string
      x-ngsi:
        type: Property
    loaderGarbageSide:
      description: 'Side of the loader garbage operated the container'
      enum:
        - backLeft
        - rearLeft
        - frontLeft
        - backRight
        - rearRight
        - frontRight
        - frontFull
        - backFull
      type: string
      x-ngsi:
        type: Property
    
  required:
    - id
    - wasteDumpsterId
    - fillingWeight
    - binCollectDatetime
  type: object
  x-derived-from: ""
  x-disclaimer: 'Redistribution and use in source and binary forms, with or without modification, are permitted  provided that the license conditions are met. Copyleft (c) 2021 Contributors to Smart Data Models Program'
  x-license-url: https://github.com/smart-data-models/dataModel.WasteManagement/blob/master/WasteCollection/LICENSE.md
  x-model-schema: https://smart-data-models.github.io/dataModel.WasteManagement/WasteCollection/schema.json
  x-model-tags: ""
  x-version: 0.1.0  
```  
</details>    

## Exemples de charges utiles  

#### WasteCollection NGSI-v2 valeurs-clés Exemple  

Voici un exemple de WasteCollection au format JSON-LD en tant que valeurs-clés. Ceci est compatible avec NGSI-v2 lorsque l'on utilise `options=keyValues` et renvoie les données contextuelles d'une entité individuelle.  

```json  

{  
  "id": "urn:ngsi-ld:Wastecollection:1021:AAWD",  
  "type": "WasteCollection",  
  "location": {  
    "coordinates": [  
      -8.768460000000001,  
      42.60214472222222  
    ],  
    "type": "Point"  
  },  
  "binCollectDatetime": "2021-06-11T06:51:02+05:30",  
  "license_plate": "KA23F2345", 
  "wasteDumpsterId":"XG58441-S" ,
  "RFID_chip": "65478158",  
  "fillingWeight": 32,  
  "binId": 12, 
  "loaderGarbageSide": "backRight" 
}  
```  

#### WasteCollection NGSI-v2 normalisé Exemple  

Voici un exemple de WasteCollection au format JSON-LD tel que normalisé. Ce format est compatible avec la norme NGSI-v2 lorsqu'il n'utilise pas d'options et renvoie les données contextuelles d'une entité individuelle.  

```json  

{  
  "id": "urn:ngsi-ld:Wastecollection:1021:AAWD",  
  "type": "WasteCollection",  
  "location": {  
    "type": "geo:json",  
    "value": {  
      "coordinates": [  
        -8.768460000000001,  
        42.60214472222222  
      ],  
      "type": "Point"  
    }  
  },  
  "binCollectDatetime": {  
    "type": "DateTime",  
    "value": "2021-06-11T06:51:02+05:30"  
  },  
  "license_plate": {  
    "type": "Text",  
    "value": "KA23F2345"  
  },  
  "RFID_chip": {  
    "type": "Text",  
    "value": "65478158"  
  },  
  "wasteDumpsterId": {  
    "type": "string",  
    "value": "XG58441-S" 
  },  
  "binRecommendedLoad": {  
    "type": "number",  
    "value": 30  
  },  
  "binId": {  
    "type": "Text",  
    "value": "12"  
  },  
  "fillingWeight": {  
    "type": "number",  
    "value": 32  
  },  
  "loaderGarbageSide": {  
    "type": "Text",  
    "value": "backRight"  
  }  
}  
```  

#### Valeurs-clés NGSI-LD du WasteCollection Exemple  

Voici un exemple de WasteCollection au format JSON-LD en tant que valeurs-clés. Ceci est compatible avec NGSI-LD lorsque vous utilisez `options=keyValues` et renvoie les données contextuelles d'une entité individuelle.  

```json  

{  
  "id": "urn:ngsi-ld:Wastecollection:1021:AAWD",  
  "@context": [  
    "iudx:WmgmtCol",  
    "https://smartdatamodels.org/context.jsonld"  
  ],  
  "type": "WasteCollection",  
  "location": {  
    "coordinates": [  
      -8.768460000000001,  
      42.60214472222222  
    ],  
    "type": "Point"  
  },  
  "binCollectDatetime": "2021-06-11T06:51:02+05:30",  
  "license_plate": "KA23F2345", 
  "wasteDumpsterId":"XG58441-S" ,
  "RFID_chip": "65478158",  
  "fillingWeight": 32,  
  "binId": 12, 
  "loaderGarbageSide": "backRight" 
}  
```  

#### WasteCollection NGSI-LD normalisé Exemple  

Voici un exemple de WasteCollection au format JSON-LD tel que normalisé. Ce format est compatible avec NGSI-LD lorsqu'il n'utilise pas d'options et renvoie les données contextuelles d'une entité individuelle.  

```json  

{  
  "id": "urn:ngsi-ld:wastecollection:1021:AAWD",  
  "type": "WasteCollection",  
  "location": {  
    "type": "Geoproperty",  
    "value": {  
      "coordinates": [  
        -8.768460000000001,  
        42.60214472222222  
      ],  
      "type": "Point"  
    }  
  },  
  "binCollectDatetime": {  
    "type": "Property",  
    "value": {  
      "@type": "DateTime",  
      "@value": "2021-06-11T06:51:02+05:30"  
    }  
  },  
  "license_plate": {  
    "type": "Property",  
    "value": "KA23F2345"  
  }, 
  "wasteDumpsterId": {  
    "type": "Property",  
    "value": "XG58441-S"  
  },    
  "RFID_chip": {  
    "type": "Property",  
    "value": "65478158"  
  },  
  "fillingWeight": {  
    "type": "Property",  
    "value": 32 
  },  
  "binId": {  
    "type": "Property",  
    "value": "12"  
  },  
  "loaderGarbageSide": {  
    "type": "Property",  
    "value": "backRight" 
  },  
   "@context": [  
    "iudx:WmgmtCol",  
    "https://smartdatamodels.org/context.jsonld"  
  ]
}  
```  
Voir [FAQ 10](https://smartdatamodels.org/index.php/faqs/) pour obtenir une réponse sur la façon de traiter les unités de magnitude