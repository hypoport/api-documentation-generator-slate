# BS Vorgänge API v2.12

BS Vorgänge API v2.12

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Mit dieser API können die Vorgänge aus der Europace Plattform ausgelesen werden.

Base URLs:

* <a href="https://baufismart.api.europace.de/">https://baufismart.api.europace.de/</a>

Email: <a href="mailto:helpdesk@europace2.de">Europace AG</a> Web: <a href="www.europace2.de">Europace AG</a> 

## Authentication

- oAuth2 authentication. 

    - Flow: password

    - Token URL = [https://api.europace.de/login](https://api.europace.de/login)

|Scope|Scope Description|
|---|---|
|API|Authorisation Scope für die gesamte API.|

<h1 id="vorg-nge-api-vorg-nge">Vorgänge</h1>

Dieser Endpunkt repräsentiert die Vertriebssicht.

### getVorgaenge

<a id="opIdgetVorgaenge"></a>

> Code samples

```shell
## You can also use wget
curl -X GET https://baufismart.api.europace.de/v2/vorgaenge \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /v2/vorgaenge`

*alle sichtbaren Vorgänge*

<h3 id="getvorgaenge-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|datenKontext|query|string|false|Datenkontext|
|aenderungSeit|query|string|false|aenderungSeit|
|aenderungBis|query|string|false|aenderungBis|
|sort|query|string|false|Sortierung der Vorgänge, aufsteigend oder absteigend|
|page|query|integer(int32)|false|page|
|limit|query|integer(int32)|false|limit|

##### Enumerated Values

|Parameter|Value|
|---|---|
|datenKontext|ECHT_GESCHAEFT|
|datenKontext|TEST_MODUS|

> Example responses

> 200 Response

```json
{
  "vorgaenge": [
    {
      "datenKontext": "TEST_MODUS",
      "externeVorgangsNummer": "string",
      "letzteAenderung": "2020-02-24T11:55:47Z",
      "letztesEreignis": "2020-02-24T11:55:47Z",
      "vorgangsNummer": "string",
      "_links": {
        "self": {
          "href": "string",
          "type": "string"
        }
      }
    }
  ],
  "_links": {
    "next": {
      "href": "string",
      "type": "string"
    },
    "prev": {
      "href": "string",
      "type": "string"
    },
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}
```

<h3 id="getvorgaenge-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Vorgaenge](#schemavorgaenge)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[Error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[Error](#schemaerror)|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Method Not Allowed|[Error](#schemaerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)|
|502|[Bad Gateway](https://tools.ietf.org/html/rfc7231#section-6.6.3)|Bad Gateway|[Error](#schemaerror)|
|504|[Gateway Time-out](https://tools.ietf.org/html/rfc7231#section-6.6.5)|Gateway Timeout|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### getVorgang

<a id="opIdgetVorgang"></a>

> Code samples

```shell
## You can also use wget
curl -X GET https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer} \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /v2/vorgaenge/{vorgangsNummer}`

*einen Vorgang abrufen*

Als Parameter wird die Vorgangsnummer verwendet, die aus BaufiSmart erzeugt wurde.

<h3 id="getvorgang-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|Nummer des Vorgangs|

> Example responses

> 200 Response

```json
{
  "antraege": [
    {
      "angebot": {
        "absicherungen": [
          {
            "abgesicherteRisiken": [
              {
                "abgesichertesRisiko": "TODESFALL",
                "auszahlungsBetrag": 0,
                "auszahlungsTurnus": "EINMALIG",
                "praemienAnteil": 0
              }
            ],
            "gesamtPraemie": 0,
            "praemienZahlungsweise": "EINMALIG",
            "tarifBezeichnung": "string",
            "tarifKennung": "string",
            "versichertePersonId": "string",
            "versicherungsArt": "string",
            "versicherungsNummer": "string",
            "versicherungsZeitraum": {
              "beginn": "2020-02-24",
              "dauerInMonaten": 0,
              "ende": "2020-02-24"
            }
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "angebotsHinweisFuerAntragsteller": "string",
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "gesamtLaufzeitInJahren": 0,
            "id": "string",
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparPhase": {
              "guthabenBeiZuteilung": 0,
              "sparBeitragMonatlich": 0,
              "sparPhaseInJahren": 0
            },
            "tarif": "string",
            "tilgungsPhase": {
              "bausparDarlehenSumme": 0,
              "sollZinsNachZuteilung": 0,
              "tilgungsBeitragMonatlich": 0,
              "tilgungsPhaseInJahren": 0
            },
            "typ": "string",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "beleihungsRechnung": {
          "beleihungsAuslauf": 0,
          "beleihungsWerte": [
            {
              "beleihungsWert": 0,
              "immobilie": {
                "id": "string"
              }
            }
          ],
          "beleihungsWerteSumme": 0,
          "produktAnbieter": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          }
        },
        "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
        "darlehen": [
          {
            "auszahlungsBetrag": 0,
            "auszahlungsDatum": "2020-02-24",
            "auszahlungsKurs": 0,
            "bereitstellung": {
              "bereitstellungsZins": 0,
              "bereitstellungsZinsFreieZeitInMonaten": 0
            },
            "darlehensBetrag": 0,
            "darlehensTyp": "ANNUITAETEN_DARLEHEN",
            "detailsZurVerwendung": "string",
            "effektivZins": 0,
            "effektivZinsRelevanteKosten": {
              "beratungsHonorar": 0,
              "grundbuchKosten": 0,
              "sonstigeKosten": 0,
              "tilgungsErsatzProduktKosten": 0,
              "wohnGebaeudeVersicherungsKosten": 0,
              "zinsabsicherungsKosten": 0,
              "zusatzSicherheitsKosten": 0
            },
            "forwardPeriodeInMonaten": 0,
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "konditionWurdeManuellAngepasst": true,
            "konditionsAnpassungsBegruendung": "string",
            "laufZeitInJahren": 0,
            "laufzeitInMonaten": 0,
            "maximaleLaufzeitInMonaten": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "rateMonatlich": 123.34,
            "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
            "sollZins": 2.05,
            "tilgung": {
              "anfaenglicheTilgung": 0,
              "sonderTilgungJaehrlich": 0,
              "tilgungsBeginnAm": "2020-02-24",
              "tilgungsErsatz": {
                "id": "string",
                "typ": "string"
              }
            },
            "tilgungsFreieAnlaufJahre": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
            "zinsBindung": {
              "endetAm": "2020-02-24",
              "jahre": 0,
              "monate": 0,
              "restschuldNachZinsBindungsEnde": 0
            },
            "zinsZahlungsBeginnAm": "2020-02-24"
          }
        ],
        "erzeugtAm": "2020-02-24T11:55:47Z",
        "kennung": "string",
        "machbarkeitsStatus": "MACHBAR",
        "meldungen": [
          {
            "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
            "kreditEntscheider": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "text": "string"
          }
        ],
        "pruefungsErgebnisse": [
          {
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "weitereAngaben": "string"
          }
        ],
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "ansprechpartner": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "antragsNummer": "string",
      "beratung": {
        "art": "PRAESENZ_GESCHAEFT",
        "hinweisFuerProduktAnbieter": "string",
        "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
      },
      "datenKontext": "TEST_MODUS",
      "dokumente": [
        {
          "art": "string",
          "href": "string",
          "name": "string",
          "titel": "string",
          "type": "string"
        }
      ],
      "kreditSachbearbeiter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "status": {
        "ablehnungsgrund": "FINANZIELLE_SITUATION",
        "antragsteller": "BEANTRAGT",
        "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
        "produktAnbieter": "NICHT_BEARBEITET"
      },
      "vermittler": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "zeitpunktDerAnnahme": "2020-02-24T11:55:47Z",
      "zugrundeliegendeDaten": {
        "bankverbindung": {
          "bic": "string",
          "iban": "string",
          "id": "string",
          "kontoinhaberIds": [
            "string"
          ],
          "kontoinhaberName": "string",
          "kreditinstitut": "string"
        },
        "finanzierungsObjekt": {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "verwendenAls": "ABLOESEN",
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "keinBaulandFlaecheInQm": 0,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        },
        "haushalte": [
          {
            "antragsteller": [
              {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "arbeitserlaubnis": false,
                "arbeitserlaubnisBefristetBis": "2020-02-24",
                "aufenthaltsTitel": "VISUM",
                "aufenthaltsTitelBefristetBis": "2020-02-24",
                "beschaeftigung": {
                  "anzahlGehaelterProJahr": 0,
                  "arbeitgeber": "string",
                  "arbeitgeberInDeutschlandAnsaessig": false,
                  "arbeitgeberLand": {
                    "isoCountryCode": "string",
                    "name": "string"
                  },
                  "art": "ANGESTELLTER",
                  "befristungsStatus": "BEFRISTET",
                  "beruf": "string",
                  "beschaeftigtSeit": "2020-02-24",
                  "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
                  "einkommenNettoJaehrlich": 0,
                  "einkommenNettoMonatlich": 0,
                  "firma": "string",
                  "inProbezeit": false,
                  "situationNachRenteneintritt": {
                    "gesetzlicheRenteMonatlich": 0,
                    "privateRenteMonatlich": 0,
                    "rentenBeginn": "2020-02-24",
                    "sonstigesEinkommenMonatlich": 0
                  },
                  "taetigkeit": "ALTENPFLEGER"
                },
                "bruttoVorjahresEinkommen": 0,
                "email": "max.mustermann@test.de",
                "externeAntragstellerId": "string",
                "familienstand": "GESCHIEDEN",
                "geburtsdatum": "2020-02-24",
                "geburtsort": "string",
                "guetertrennungVereinbartWennVerheiratet": false,
                "id": "string",
                "inDeutschlandSeit": "2020-02-24",
                "legitimationsDaten": {
                  "ausstellendeBehoerde": "string",
                  "ausstellungsdatum": "2020-02-24",
                  "ausweisArt": "PERSONALAUSWEIS",
                  "ausweisArtBeiAndererAusweis": "string",
                  "ausweisNummer": "string"
                },
                "nachname": "string",
                "schufaErgebnis": {
                  "antragstellerUnbekannt": false,
                  "inManuellerNachbehandlung": false,
                  "score": "string"
                },
                "staatsangehoerigkeit": {
                  "isoCountryCode": "string",
                  "name": "string"
                },
                "steuerId": "string",
                "telefonnummer": "string",
                "telefonnummerVorwahl": "string",
                "titel": [
                  "DOKTOR"
                ],
                "titelDoktor": true,
                "titelProfessor": true,
                "vorAnschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "vorname": "string",
                "weitereKontaktMoeglichkeiten": "string",
                "wohnhaftSeit": "2020-02-24"
              }
            ],
            "anzahlErwachseneImHaushalt": 0,
            "anzahlKinderNichtImHaushalt": 0,
            "bestehendeImmobilien": [
              {
                "adresse": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "autostellplaetze": [
                  {
                    "mieteinnahmenMonatlich": 0,
                    "typ": "STELLPLATZ"
                  }
                ],
                "bestehendeDarlehen": [
                  {
                    "abzuloesendeRestschuld": 0,
                    "aktuelleRestschuldWennNichtAbzuloesen": 0,
                    "darlehensArt": "BAUSPARDARLEHEN",
                    "darlehensBetrag": 0,
                    "darlehensGeber": {},
                    "darlehensKontonummer": "string",
                    "eingetrageneGrundschuld": 0,
                    "grundschuldArt": "BRIEF_GRUNDSCHULD",
                    "id": "string",
                    "laufzeitEnde": "2020-02-24",
                    "rateMonatlich": 0,
                    "sollZins": 0,
                    "sondertilgungZumZinsBindungsEnde": 0,
                    "zinsBindungEndetAm": "2020-02-24"
                  }
                ],
                "bewirtschaftungsKostenJaehrlich": 0,
                "bodenRichtwert": 0,
                "bundesland": "BADEN_WUERTTEMBERG",
                "effektivZinsErhoehendeKosten": {
                  "anpassen": true,
                  "grundbuchEintragungsKostenEinmalig": 0,
                  "sonstigeKostenBezeichnung": "string",
                  "sonstigeKostenEinmalig": 0,
                  "wohnGebaeudeVersicherungsKostenJaehrlich": 0
                },
                "erbbaurecht": {
                  "erbbaurecht": true,
                  "erbbauzinsJaehrlich": 0,
                  "grundstuecksEigentuemer": "ANDERE",
                  "laufzeitBisJahr": "string"
                },
                "gebaeude": {
                  "anzahlDerGewerbeeinheiten": 0,
                  "anzahlDerWohneinheitenImGebaeude": 0,
                  "anzahlVollgeschosse": 0,
                  "aufbauFinanzierung": true,
                  "aufzugVorhanden": true,
                  "ausstattung": "EINFACH",
                  "baujahr": "2016",
                  "bauweise": "FACHWERK_MIT_STROH_LEHM",
                  "bezeichnungWohneinheit": "string",
                  "dachgeschossAusbau": "FLACHDACH",
                  "einliegerwohnungVorhanden": true,
                  "geschossLage": "UNTERGESCHOSS",
                  "gewerbeflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "hausAnordnung": "FREISTEHEND",
                  "hausTyp": "DOPPELHAUSHAELFTE",
                  "istFertighaus": true,
                  "kellerausbau": "AUSGEBAUT",
                  "kubatur": 0,
                  "miteigentumsAnteil": {
                    "anteil": 0,
                    "gesamt": 0
                  },
                  "modernisierungsAngaben": {
                    "badWc": true,
                    "bodenWandTreppe": true,
                    "dach": true,
                    "fenster": true,
                    "heizungZentral": true,
                    "modernisierungsGrad": "GERING",
                    "modernisierungsJahr": "string",
                    "raumaufteilung": true,
                    "stromAbwasserHeizkoerper": true,
                    "waermedaemmung": true,
                    "wurdeModernisiert": true
                  },
                  "unterkellerung": "NICHT_UNTERKELLERT",
                  "wohnflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "zustand": "SEHR_GUT"
                },
                "grundbuchAngabe": {
                  "anmerkungen": "string",
                  "bandUndBlatt": "string",
                  "flurstuecke": [
                    {}
                  ],
                  "ort": "string",
                  "rechteInAbteilung2": {
                    "beschreibung": "string",
                    "betrag": 0,
                    "vorhanden": true
                  }
                },
                "grundstueck": {
                  "groesse": 0,
                  "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
                },
                "id": "string",
                "immobilienEinsatz": "KEIN_EINSATZ",
                "keinBaulandFlaecheInQm": 0,
                "keineBestehendenDarlehenVorhanden": true,
                "marktueblicherKaufpreisProQm": 0,
                "marktwert": 0,
                "maximalEinzusetzenderBetragWennVerkauf": 0,
                "objektArt": "GRUNDSTUECK",
                "vergleichsmieteFuerGewerbeflaecheProQm": 0,
                "vergleichsmieteFuerWohnflaecheProQm": 0,
                "verkehrswert": 0,
                "vorlaeufigerVerkehrswert": 0,
                "wohnlage": "GEHOBEN"
              }
            ],
            "id": "string",
            "kfzAnzahl": 0,
            "kinder": [
              {
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kindergeldWirdBezogen": true,
                "name": "string",
                "unterhaltsEinnahmenBetragMonatlich": 0
              }
            ],
            "lebenshaltungsKostenMonatlich": 0,
            "obligo": {
              "vermoegenOderVerbindlichkeiten": [
                {
                  "aktuellerWert": 0,
                  "anrechnungFuerBlankoAnteil": 0,
                  "bezeichner": "string",
                  "kontonummer": "string",
                  "vermoegensTyp": "VERMOEGEN"
                }
              ]
            },
            "positionen": {
              "bankUndSparguthaben": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zinsertragJaehrlich": 0,
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "bausparvertraege": [
                {
                  "abschlussGebuehr": 0,
                  "aktuellerWert": 0,
                  "bausparSumme": 0,
                  "einmalzahlung": 0,
                  "ertrag": 0,
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "produktAnbieter": {
                    "anrede": "FRAU",
                    "anschrift": {},
                    "email": "string",
                    "externePartnerId": "string",
                    "externerKreditSachbearbeiterId": "string",
                    "fax": "string",
                    "firmenNameZusatz": "string",
                    "firmierung": "string",
                    "geburtsdatum": "2020-02-24",
                    "id": "string",
                    "kreditsachbearbeiter": true,
                    "mobilTelefon": "string",
                    "nachname": "string",
                    "partnerId": "string",
                    "produktAnbieterId": "string",
                    "telefonnummer": "string",
                    "vertriebsOrganisation": {},
                    "vorname": "string",
                    "webseite": "string"
                  },
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeitragMonatlich": 0,
                  "tarif": "string",
                  "typ": "string",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "vertragsBeginn": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0,
                  "zuteilungsDatum": "2020-02-24"
                }
              ],
              "ehegattenUnterhalt": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "einkuenfteAusNebentaetigkeit": [
                {
                  "beginnDerNebentaetigkeit": "2020-02-24",
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "kindergeld": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "lebensUndRentenVersicherungen": [
                {
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "praemieMonatlich": 0,
                  "rueckkaufsWertAktuell": 0,
                  "tarif": "string",
                  "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "versicherungsGesellschaft": "string",
                  "versicherungsSumme": 0,
                  "vertragsBeginn": "2020-02-24",
                  "vertragsEnde": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "mietAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "entfallenMitFinanzierung": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateDarlehen": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateKrankenversicherung": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "ratenkredite": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeEinnahmen": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVerbindlichkeiten": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVermoegen": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "sparplaene": [
                {
                  "aktuellerWert": 0,
                  "beitragMonatlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "unbefristeteZusatzRenten": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "unterhaltsVerpflichtungen": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "variableEinkuenfte": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "versicherungsAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "wertpapiere": [
                {
                  "aktuellerWert": 0,
                  "dividendenJaehrlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ]
            }
          }
        ],
        "vorhaben": {
          "absicherungswunsch": {
            "id": "string",
            "versicherungsWuensche": [
              {
                "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
                "id": "string",
                "praemienZahlungsweise": "EINMALIG",
                "risikoAbsicherungsWuensche": [
                  {
                    "abzusicherndesRisiko": "TODESFALL",
                    "versicherteRate": 0,
                    "versicherungsSumme": 0
                  }
                ],
                "versichertePersonId": "string",
                "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
                "versicherungsBeginn": "2020-02-24",
                "versicherungsDauerInMonaten": 0
              }
            ]
          },
          "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
          "externeBausparAngebote": [
            {
              "abschlussGebuehr": 0,
              "angebotsHinweisFuerAntragsteller": "string",
              "bausparSumme": 0,
              "einmalzahlung": 0,
              "id": "string",
              "produktAnbieter": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparPhase": {
                "guthabenBeiZuteilung": 0,
                "sparBeitragMonatlich": 0,
                "sparPhaseInJahren": 0
              },
              "tarif": "string",
              "tilgungsPhase": {
                "bausparDarlehenSumme": 0,
                "sollZinsNachZuteilung": 0,
                "tilgungsBeitragMonatlich": 0,
                "tilgungsPhaseInJahren": 0
              },
              "typ": "string",
              "vertragsBeginn": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zuteilungsDatum": "2020-02-24"
            }
          ],
          "finanzbedarf": {
            "anzahlTeilzahlungen": 0,
            "aussenAnlagen": 0,
            "bauNebenkosten": 0,
            "beratungsHonorar": 0,
            "bereitsBeglichen": 0,
            "erschliessung": 0,
            "grunderwerbsteuer": 0,
            "grundstueckBereitsBezahlt": true,
            "grundstuecksKaufpreis": 0,
            "herstellung": 0,
            "kapitalBeschaffung": 0,
            "kapitalWirdBeschafft": true,
            "kaufpreis": 0,
            "maklergebuehr": 0,
            "mobiliar": 0,
            "modernisieren": true,
            "modernisierung": 0,
            "notargebuehr": 0,
            "renovierung": 0,
            "sonstigeKosten": 0,
            "zusaetzlichesKapital": 0
          },
          "finanzierungswunsch": {
            "bausparWuensche": [
              {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              }
            ],
            "darlehensWuensche": [
              {
                "annuitaetenDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "forwardDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "id": "string",
                "kfwDarlehen": {
                  "darlehensBetrag": 0,
                  "kfwEndfaellig": "NEIN",
                  "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
                  "kfwProgramm": "PROGRAMM_124",
                  "laufzeitInJahren": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "tilgungsfreieAnlaufjahre": 0,
                  "zinsBindungInJahren": 0
                },
                "privatDarlehen": {
                  "darlehensBetrag": 0,
                  "laufzeitInMonaten": 0,
                  "provision": 0
                },
                "variablesDarlehen": {
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  }
                },
                "zwischenFinanzierung": {
                  "darlehensBetrag": 0,
                  "detailsZurVerwendung": "string",
                  "maximaleLaufzeitInMonaten": 0,
                  "provision": 0,
                  "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
                }
              }
            ],
            "id": "string"
          },
          "id": "string",
          "nachfinanzierung": true,
          "nachrangigeExterneDarlehen": [
            {
              "darlehensBetrag": 0,
              "darlehensGeber": "string",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "typ": "ARBEITGEBERDARLEHEN",
              "zinsBindung": {
                "endetAm": "2020-02-24",
                "jahre": 0,
                "monate": 0,
                "restschuldNachZinsBindungsEnde": 0
              }
            }
          ],
          "praeferenzen": {
            "bereitstellungsZinsFreieZeit": {
              "darlehenBenoetigtInMonaten": 0,
              "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
              "zusatzlicheKommentare": "string"
            },
            "bestandteileDerFinanzierung": {
              "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
              "zusatzlicheKommentare": "string"
            },
            "hoeheDerRate": {
              "betrag": 0,
              "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
              "zusatzlicheKommentare": "string"
            },
            "laufzeit": {
              "bisZumJahr": "2016",
              "bisZurRenteImJahr": "2016",
              "inJahren": 0,
              "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
              "zusatzlicheKommentare": "string"
            },
            "sondertilgung": {
              "betragEinmalig": 0,
              "betragJaehrlich": 0,
              "praeferenzAuswahl": "JAEHRLICH",
              "zusatzlicheKommentare": "string"
            },
            "tilgungsSatzWechsel": {
              "mindestensBenoetigt": 0,
              "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
              "zusatzlicheKommentare": "string"
            },
            "weiterePraeferenz": "string",
            "zeitlicherRahmen": {
              "finanzierungszusageBis": "2020-02-24",
              "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
              "zusatzlicheKommentare": "string"
            },
            "zinsBindung": {
              "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
              "zinsBindungBisJahren": 0,
              "zinsBindungVonJahren": 0,
              "zinsBindungZwischenJahren": 0,
              "zusatzlicheKommentare": "string"
            }
          },
          "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
        }
      },
      "_links": {
        "self": {
          "href": "string",
          "type": "string"
        }
      }
    }
  ],
  "archivierung": {
    "grund": "VORGANG_ERFOLGREICH_ABGESCHLOSSEN",
    "kommentar": "string"
  },
  "aufbewahrungBis": "2020-02-24",
  "bankverbindung": {
    "bic": "string",
    "iban": "string",
    "id": "string",
    "kontoinhaberIds": [
      "string"
    ],
    "kontoinhaberName": "string",
    "kreditinstitut": "string"
  },
  "datenKontext": "TEST_MODUS",
  "erstelltAm": "2020-02-24",
  "externeVorgangsNummer": "string",
  "finanzierungsObjekt": {
    "adresse": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "autostellplaetze": [
      {
        "mieteinnahmenMonatlich": 0,
        "typ": "STELLPLATZ"
      }
    ],
    "bestehendeDarlehen": [
      {
        "abzuloesendeRestschuld": 0,
        "aktuelleRestschuldWennNichtAbzuloesen": 0,
        "darlehensArt": "BAUSPARDARLEHEN",
        "darlehensBetrag": 0,
        "darlehensGeber": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "darlehensKontonummer": "string",
        "eingetrageneGrundschuld": 0,
        "grundschuldArt": "BRIEF_GRUNDSCHULD",
        "id": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "sollZins": 0,
        "sondertilgungZumZinsBindungsEnde": 0,
        "verwendenAls": "ABLOESEN",
        "zinsBindungEndetAm": "2020-02-24"
      }
    ],
    "bewirtschaftungsKostenJaehrlich": 0,
    "bodenRichtwert": 0,
    "bundesland": "BADEN_WUERTTEMBERG",
    "effektivZinsErhoehendeKosten": {
      "anpassen": true,
      "grundbuchEintragungsKostenEinmalig": 0,
      "sonstigeKostenBezeichnung": "string",
      "sonstigeKostenEinmalig": 0,
      "wohnGebaeudeVersicherungsKostenJaehrlich": 0
    },
    "erbbaurecht": {
      "erbbaurecht": true,
      "erbbauzinsJaehrlich": 0,
      "grundstuecksEigentuemer": "ANDERE",
      "laufzeitBisJahr": "string"
    },
    "gebaeude": {
      "anzahlDerGewerbeeinheiten": 0,
      "anzahlDerWohneinheitenImGebaeude": 0,
      "anzahlVollgeschosse": 0,
      "aufbauFinanzierung": true,
      "aufzugVorhanden": true,
      "ausstattung": "EINFACH",
      "baujahr": "2016",
      "bauweise": "FACHWERK_MIT_STROH_LEHM",
      "bezeichnungWohneinheit": "string",
      "dachgeschossAusbau": "FLACHDACH",
      "einliegerwohnungVorhanden": true,
      "geschossLage": "UNTERGESCHOSS",
      "gewerbeflaeche": {
        "gesamtGroesse": 0,
        "vermietungsInformationen": {
          "mieteinnahmenNettoKaltMonatlich": 0,
          "nutzungsArt": "EIGENGENUTZT",
          "vermieteteFlaeche": 0
        }
      },
      "hausAnordnung": "FREISTEHEND",
      "hausTyp": "DOPPELHAUSHAELFTE",
      "istFertighaus": true,
      "kellerausbau": "AUSGEBAUT",
      "kubatur": 0,
      "miteigentumsAnteil": {
        "anteil": 0,
        "gesamt": 0
      },
      "modernisierungsAngaben": {
        "badWc": true,
        "bodenWandTreppe": true,
        "dach": true,
        "fenster": true,
        "heizungZentral": true,
        "modernisierungsGrad": "GERING",
        "modernisierungsJahr": "string",
        "raumaufteilung": true,
        "stromAbwasserHeizkoerper": true,
        "waermedaemmung": true,
        "wurdeModernisiert": true
      },
      "unterkellerung": "NICHT_UNTERKELLERT",
      "wohnflaeche": {
        "gesamtGroesse": 0,
        "vermietungsInformationen": {
          "mieteinnahmenNettoKaltMonatlich": 0,
          "nutzungsArt": "EIGENGENUTZT",
          "vermieteteFlaeche": 0
        }
      },
      "zustand": "SEHR_GUT"
    },
    "grundbuchAngabe": {
      "anmerkungen": "string",
      "bandUndBlatt": "string",
      "flurstuecke": [
        {
          "anteil": {
            "anteil": 0,
            "gesamt": 0
          },
          "flur": "string",
          "flurstuecksNummer": "string",
          "groesse": 0
        }
      ],
      "ort": "string",
      "rechteInAbteilung2": {
        "beschreibung": "string",
        "betrag": 0,
        "vorhanden": true
      }
    },
    "grundstueck": {
      "groesse": 0,
      "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
    },
    "id": "string",
    "keinBaulandFlaecheInQm": 0,
    "marktueblicherKaufpreisProQm": 0,
    "marktwert": 0,
    "objektArt": "GRUNDSTUECK",
    "vergleichsmieteFuerGewerbeflaecheProQm": 0,
    "vergleichsmieteFuerWohnflaecheProQm": 0,
    "verkehrswert": 0,
    "vorlaeufigerVerkehrswert": 0,
    "wohnlage": "GEHOBEN"
  },
  "geschlossenAm": "2020-02-24",
  "haushalte": [
    {
      "antragsteller": [
        {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "arbeitserlaubnis": false,
          "arbeitserlaubnisBefristetBis": "2020-02-24",
          "aufenthaltsTitel": "VISUM",
          "aufenthaltsTitelBefristetBis": "2020-02-24",
          "beschaeftigung": {
            "anzahlGehaelterProJahr": 0,
            "arbeitgeber": "string",
            "arbeitgeberInDeutschlandAnsaessig": false,
            "arbeitgeberLand": {
              "isoCountryCode": "string",
              "name": "string"
            },
            "art": "ANGESTELLTER",
            "befristungsStatus": "BEFRISTET",
            "beruf": "string",
            "beschaeftigtSeit": "2020-02-24",
            "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
            "einkommenNettoJaehrlich": 0,
            "einkommenNettoMonatlich": 0,
            "firma": "string",
            "inProbezeit": false,
            "situationNachRenteneintritt": {
              "gesetzlicheRenteMonatlich": 0,
              "privateRenteMonatlich": 0,
              "rentenBeginn": "2020-02-24",
              "sonstigesEinkommenMonatlich": 0
            },
            "taetigkeit": "ALTENPFLEGER"
          },
          "bruttoVorjahresEinkommen": 0,
          "email": "max.mustermann@test.de",
          "externeAntragstellerId": "string",
          "familienstand": "GESCHIEDEN",
          "geburtsdatum": "2020-02-24",
          "geburtsort": "string",
          "guetertrennungVereinbartWennVerheiratet": false,
          "id": "string",
          "inDeutschlandSeit": "2020-02-24",
          "legitimationsDaten": {
            "ausstellendeBehoerde": "string",
            "ausstellungsdatum": "2020-02-24",
            "ausweisArt": "PERSONALAUSWEIS",
            "ausweisArtBeiAndererAusweis": "string",
            "ausweisNummer": "string"
          },
          "nachname": "string",
          "schufaErgebnis": {
            "antragstellerUnbekannt": false,
            "inManuellerNachbehandlung": false,
            "score": "string"
          },
          "staatsangehoerigkeit": {
            "isoCountryCode": "string",
            "name": "string"
          },
          "steuerId": "string",
          "telefonnummer": "string",
          "telefonnummerVorwahl": "string",
          "titel": [
            "DOKTOR"
          ],
          "titelDoktor": true,
          "titelProfessor": true,
          "vorAnschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "vorname": "string",
          "weitereKontaktMoeglichkeiten": "string",
          "wohnhaftSeit": "2020-02-24"
        }
      ],
      "anzahlErwachseneImHaushalt": 0,
      "anzahlKinderNichtImHaushalt": 0,
      "bestehendeImmobilien": [
        {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "immobilienEinsatz": "KEIN_EINSATZ",
          "keinBaulandFlaecheInQm": 0,
          "keineBestehendenDarlehenVorhanden": true,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "maximalEinzusetzenderBetragWennVerkauf": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        }
      ],
      "id": "string",
      "kfzAnzahl": 0,
      "kinder": [
        {
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kindergeldWirdBezogen": true,
          "name": "string",
          "unterhaltsEinnahmenBetragMonatlich": 0
        }
      ],
      "lebenshaltungsKostenMonatlich": 0,
      "obligo": {
        "vermoegenOderVerbindlichkeiten": [
          {
            "aktuellerWert": 0,
            "anrechnungFuerBlankoAnteil": 0,
            "bezeichner": "string",
            "kontonummer": "string",
            "vermoegensTyp": "VERMOEGEN"
          }
        ]
      },
      "positionen": {
        "bankUndSparguthaben": [
          {
            "aktuellerWert": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zinsertragJaehrlich": 0,
            "zukuenftigeEinnahmen": 0
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "aktuellerWert": 0,
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "ertrag": 0,
            "id": "string",
            "maximalAufzuloesenderBetrag": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeitragMonatlich": 0,
            "tarif": "string",
            "typ": "string",
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "ehegattenUnterhalt": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "einkuenfteAusNebentaetigkeit": [
          {
            "beginnDerNebentaetigkeit": "2020-02-24",
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "kindergeld": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "lebensUndRentenVersicherungen": [
          {
            "id": "string",
            "maximalAufzuloesenderBetrag": 0,
            "praemieMonatlich": 0,
            "rueckkaufsWertAktuell": 0,
            "tarif": "string",
            "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "versicherungsGesellschaft": "string",
            "versicherungsSumme": 0,
            "vertragsBeginn": "2020-02-24",
            "vertragsEnde": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "mietAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "entfallenMitFinanzierung": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "privateDarlehen": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "privateKrankenversicherung": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "ratenkredite": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeEinnahmen": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeVerbindlichkeiten": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeVermoegen": [
          {
            "aktuellerWert": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zukuenftigeEinnahmen": 0
          }
        ],
        "sparplaene": [
          {
            "aktuellerWert": 0,
            "beitragMonatlich": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0
          }
        ],
        "unbefristeteZusatzRenten": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "unterhaltsVerpflichtungen": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "variableEinkuenfte": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "versicherungsAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "wertpapiere": [
          {
            "aktuellerWert": 0,
            "dividendenJaehrlich": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0
          }
        ]
      }
    }
  ],
  "importQuelle": "string",
  "kundenBetreuer": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "leadTracking": {
    "kampagne": "string",
    "keyword": "string",
    "kundenBetreuerBenachrichtigen": true,
    "trackingId": "string"
  },
  "letztesEreignis": "2020-02-24T11:55:47Z",
  "phase": "string",
  "prioritaet": "NIEDRIG",
  "status": "string",
  "tippGeber": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "vorgangsBearbeiter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "vorgangsNummer": "string",
  "vorhaben": {
    "absicherungswunsch": {
      "id": "string",
      "versicherungsWuensche": [
        {
          "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
          "id": "string",
          "praemienZahlungsweise": "EINMALIG",
          "risikoAbsicherungsWuensche": [
            {
              "abzusicherndesRisiko": "TODESFALL",
              "versicherteRate": 0,
              "versicherungsSumme": 0
            }
          ],
          "versichertePersonId": "string",
          "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
          "versicherungsBeginn": "2020-02-24",
          "versicherungsDauerInMonaten": 0
        }
      ]
    },
    "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
    "externeBausparAngebote": [
      {
        "abschlussGebuehr": 0,
        "angebotsHinweisFuerAntragsteller": "string",
        "bausparSumme": 0,
        "einmalzahlung": 0,
        "id": "string",
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparPhase": {
          "guthabenBeiZuteilung": 0,
          "sparBeitragMonatlich": 0,
          "sparPhaseInJahren": 0
        },
        "tarif": "string",
        "tilgungsPhase": {
          "bausparDarlehenSumme": 0,
          "sollZinsNachZuteilung": 0,
          "tilgungsBeitragMonatlich": 0,
          "tilgungsPhaseInJahren": 0
        },
        "typ": "string",
        "vertragsBeginn": "2020-02-24",
        "vertragsNummer": "string",
        "verwaltungsgebuehrenJaehrlich": 0,
        "zuteilungsDatum": "2020-02-24"
      }
    ],
    "finanzbedarf": {
      "anzahlTeilzahlungen": 0,
      "aussenAnlagen": 0,
      "bauNebenkosten": 0,
      "beratungsHonorar": 0,
      "bereitsBeglichen": 0,
      "erschliessung": 0,
      "grunderwerbsteuer": 0,
      "grundstueckBereitsBezahlt": true,
      "grundstuecksKaufpreis": 0,
      "herstellung": 0,
      "kapitalBeschaffung": 0,
      "kapitalWirdBeschafft": true,
      "kaufpreis": 0,
      "maklergebuehr": 0,
      "mobiliar": 0,
      "modernisieren": true,
      "modernisierung": 0,
      "notargebuehr": 0,
      "renovierung": 0,
      "sonstigeKosten": 0,
      "zusaetzlichesKapital": 0
    },
    "finanzierungswunsch": {
      "bausparWuensche": [
        {
          "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
          "bausparSummeAbsolut": 0,
          "bausparSummeRelativ": 0,
          "bausparTarif": [
            {
              "id": "string",
              "kurzName": "string",
              "langName": "string",
              "produktAnbieter": "string",
              "riesterFoerderung": true,
              "status": "AKTIV"
            }
          ],
          "bausparTarife": [
            "string"
          ],
          "id": "string",
          "sonderZahlungEinmalig": 0,
          "sonderZahlungen": [
            {
              "anzahl": 0,
              "betrag": 0,
              "termin": "2020-02-24",
              "zahlweise": "EINMALIG"
            }
          ],
          "sparBeginn": "2020-02-24",
          "sparBeitragMonatlichAbsolut": 0,
          "sparBeitragMonatlichRelativ": 0,
          "tilgungsBeitragMonatlich": 0,
          "vertragsPartnerIds": [
            "string"
          ],
          "verwendung": "ZINS_ABSICHERUNG",
          "zuteilungsDatum": "2020-02-24"
        }
      ],
      "darlehensWuensche": [
        {
          "annuitaetenDarlehen": {
            "auszahlungsDatum": "2020-02-24",
            "bereitstellungsZinsFreieZeitInMonaten": 0,
            "darlehensBetrag": 0,
            "provision": 0,
            "sondertilgungOptionalJaehrlich": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "zinsBindungInJahren": 0
          },
          "forwardDarlehen": {
            "auszahlungsDatum": "2020-02-24",
            "bereitstellungsZinsFreieZeitInMonaten": 0,
            "darlehensBetrag": 0,
            "provision": 0,
            "sondertilgungOptionalJaehrlich": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "zinsBindungInJahren": 0
          },
          "id": "string",
          "kfwDarlehen": {
            "darlehensBetrag": 0,
            "kfwEndfaellig": "NEIN",
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "laufzeitInJahren": 0,
            "provision": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "tilgungsfreieAnlaufjahre": 0,
            "zinsBindungInJahren": 0
          },
          "privatDarlehen": {
            "darlehensBetrag": 0,
            "laufzeitInMonaten": 0,
            "provision": 0
          },
          "variablesDarlehen": {
            "darlehensBetrag": 0,
            "provision": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            }
          },
          "zwischenFinanzierung": {
            "darlehensBetrag": 0,
            "detailsZurVerwendung": "string",
            "maximaleLaufzeitInMonaten": 0,
            "provision": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
          }
        }
      ],
      "id": "string"
    },
    "id": "string",
    "nachfinanzierung": true,
    "nachrangigeExterneDarlehen": [
      {
        "darlehensBetrag": 0,
        "darlehensGeber": "string",
        "id": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "typ": "ARBEITGEBERDARLEHEN",
        "zinsBindung": {
          "endetAm": "2020-02-24",
          "jahre": 0,
          "monate": 0,
          "restschuldNachZinsBindungsEnde": 0
        }
      }
    ],
    "praeferenzen": {
      "bereitstellungsZinsFreieZeit": {
        "darlehenBenoetigtInMonaten": 0,
        "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
        "zusatzlicheKommentare": "string"
      },
      "bestandteileDerFinanzierung": {
        "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
        "zusatzlicheKommentare": "string"
      },
      "hoeheDerRate": {
        "betrag": 0,
        "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
        "zusatzlicheKommentare": "string"
      },
      "laufzeit": {
        "bisZumJahr": "2016",
        "bisZurRenteImJahr": "2016",
        "inJahren": 0,
        "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
        "zusatzlicheKommentare": "string"
      },
      "sondertilgung": {
        "betragEinmalig": 0,
        "betragJaehrlich": 0,
        "praeferenzAuswahl": "JAEHRLICH",
        "zusatzlicheKommentare": "string"
      },
      "tilgungsSatzWechsel": {
        "mindestensBenoetigt": 0,
        "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
        "zusatzlicheKommentare": "string"
      },
      "weiterePraeferenz": "string",
      "zeitlicherRahmen": {
        "finanzierungszusageBis": "2020-02-24",
        "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
        "zusatzlicheKommentare": "string"
      },
      "zinsBindung": {
        "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
        "zinsBindungBisJahren": 0,
        "zinsBindungVonJahren": 0,
        "zinsBindungZwischenJahren": 0,
        "zusatzlicheKommentare": "string"
      }
    },
    "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
  },
  "_links": {
    "antraege": {
      "href": "string",
      "type": "string"
    },
    "ereignisse": {
      "href": "string",
      "type": "string"
    },
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}
```

<h3 id="getvorgang-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Vorgang](#schemavorgang)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[Error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[Error](#schemaerror)|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Method Not Allowed|[Error](#schemaerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)|
|502|[Bad Gateway](https://tools.ietf.org/html/rfc7231#section-6.6.3)|Bad Gateway|[Error](#schemaerror)|
|504|[Gateway Time-out](https://tools.ietf.org/html/rfc7231#section-6.6.5)|Gateway Timeout|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### updateVorgang

<a id="opIdupdateVorgang"></a>

> Code samples

```shell
## You can also use wget
curl -X PATCH https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer} \
  -H 'Content-Type: application/json-patch+json' \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Content-Type':'application/json-patch+json',
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`PATCH /v2/vorgaenge/{vorgangsNummer}`

*Änderung von Metadaten an einem bestehenden Vorgang*

> Body parameter

```json
[
  {
    "from": "string",
    "op": "add",
    "path": "string",
    "value": {}
  }
]
```

<h3 id="updatevorgang-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|
|body|body|array[object]|true|patchOperations|

> Example responses

> 200 Response

```json
{
  "antraege": [
    {
      "angebot": {
        "absicherungen": [
          {
            "abgesicherteRisiken": [
              {
                "abgesichertesRisiko": "TODESFALL",
                "auszahlungsBetrag": 0,
                "auszahlungsTurnus": "EINMALIG",
                "praemienAnteil": 0
              }
            ],
            "gesamtPraemie": 0,
            "praemienZahlungsweise": "EINMALIG",
            "tarifBezeichnung": "string",
            "tarifKennung": "string",
            "versichertePersonId": "string",
            "versicherungsArt": "string",
            "versicherungsNummer": "string",
            "versicherungsZeitraum": {
              "beginn": "2020-02-24",
              "dauerInMonaten": 0,
              "ende": "2020-02-24"
            }
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "angebotsHinweisFuerAntragsteller": "string",
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "gesamtLaufzeitInJahren": 0,
            "id": "string",
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparPhase": {
              "guthabenBeiZuteilung": 0,
              "sparBeitragMonatlich": 0,
              "sparPhaseInJahren": 0
            },
            "tarif": "string",
            "tilgungsPhase": {
              "bausparDarlehenSumme": 0,
              "sollZinsNachZuteilung": 0,
              "tilgungsBeitragMonatlich": 0,
              "tilgungsPhaseInJahren": 0
            },
            "typ": "string",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "beleihungsRechnung": {
          "beleihungsAuslauf": 0,
          "beleihungsWerte": [
            {
              "beleihungsWert": 0,
              "immobilie": {
                "id": "string"
              }
            }
          ],
          "beleihungsWerteSumme": 0,
          "produktAnbieter": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          }
        },
        "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
        "darlehen": [
          {
            "auszahlungsBetrag": 0,
            "auszahlungsDatum": "2020-02-24",
            "auszahlungsKurs": 0,
            "bereitstellung": {
              "bereitstellungsZins": 0,
              "bereitstellungsZinsFreieZeitInMonaten": 0
            },
            "darlehensBetrag": 0,
            "darlehensTyp": "ANNUITAETEN_DARLEHEN",
            "detailsZurVerwendung": "string",
            "effektivZins": 0,
            "effektivZinsRelevanteKosten": {
              "beratungsHonorar": 0,
              "grundbuchKosten": 0,
              "sonstigeKosten": 0,
              "tilgungsErsatzProduktKosten": 0,
              "wohnGebaeudeVersicherungsKosten": 0,
              "zinsabsicherungsKosten": 0,
              "zusatzSicherheitsKosten": 0
            },
            "forwardPeriodeInMonaten": 0,
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "konditionWurdeManuellAngepasst": true,
            "konditionsAnpassungsBegruendung": "string",
            "laufZeitInJahren": 0,
            "laufzeitInMonaten": 0,
            "maximaleLaufzeitInMonaten": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "rateMonatlich": 123.34,
            "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
            "sollZins": 2.05,
            "tilgung": {
              "anfaenglicheTilgung": 0,
              "sonderTilgungJaehrlich": 0,
              "tilgungsBeginnAm": "2020-02-24",
              "tilgungsErsatz": {
                "id": "string",
                "typ": "string"
              }
            },
            "tilgungsFreieAnlaufJahre": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
            "zinsBindung": {
              "endetAm": "2020-02-24",
              "jahre": 0,
              "monate": 0,
              "restschuldNachZinsBindungsEnde": 0
            },
            "zinsZahlungsBeginnAm": "2020-02-24"
          }
        ],
        "erzeugtAm": "2020-02-24T11:55:47Z",
        "kennung": "string",
        "machbarkeitsStatus": "MACHBAR",
        "meldungen": [
          {
            "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
            "kreditEntscheider": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "text": "string"
          }
        ],
        "pruefungsErgebnisse": [
          {
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "weitereAngaben": "string"
          }
        ],
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "ansprechpartner": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "antragsNummer": "string",
      "beratung": {
        "art": "PRAESENZ_GESCHAEFT",
        "hinweisFuerProduktAnbieter": "string",
        "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
      },
      "datenKontext": "TEST_MODUS",
      "dokumente": [
        {
          "art": "string",
          "href": "string",
          "name": "string",
          "titel": "string",
          "type": "string"
        }
      ],
      "kreditSachbearbeiter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "status": {
        "ablehnungsgrund": "FINANZIELLE_SITUATION",
        "antragsteller": "BEANTRAGT",
        "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
        "produktAnbieter": "NICHT_BEARBEITET"
      },
      "vermittler": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "zeitpunktDerAnnahme": "2020-02-24T11:55:47Z",
      "zugrundeliegendeDaten": {
        "bankverbindung": {
          "bic": "string",
          "iban": "string",
          "id": "string",
          "kontoinhaberIds": [
            "string"
          ],
          "kontoinhaberName": "string",
          "kreditinstitut": "string"
        },
        "finanzierungsObjekt": {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "verwendenAls": "ABLOESEN",
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "keinBaulandFlaecheInQm": 0,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        },
        "haushalte": [
          {
            "antragsteller": [
              {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "arbeitserlaubnis": false,
                "arbeitserlaubnisBefristetBis": "2020-02-24",
                "aufenthaltsTitel": "VISUM",
                "aufenthaltsTitelBefristetBis": "2020-02-24",
                "beschaeftigung": {
                  "anzahlGehaelterProJahr": 0,
                  "arbeitgeber": "string",
                  "arbeitgeberInDeutschlandAnsaessig": false,
                  "arbeitgeberLand": {
                    "isoCountryCode": "string",
                    "name": "string"
                  },
                  "art": "ANGESTELLTER",
                  "befristungsStatus": "BEFRISTET",
                  "beruf": "string",
                  "beschaeftigtSeit": "2020-02-24",
                  "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
                  "einkommenNettoJaehrlich": 0,
                  "einkommenNettoMonatlich": 0,
                  "firma": "string",
                  "inProbezeit": false,
                  "situationNachRenteneintritt": {
                    "gesetzlicheRenteMonatlich": 0,
                    "privateRenteMonatlich": 0,
                    "rentenBeginn": "2020-02-24",
                    "sonstigesEinkommenMonatlich": 0
                  },
                  "taetigkeit": "ALTENPFLEGER"
                },
                "bruttoVorjahresEinkommen": 0,
                "email": "max.mustermann@test.de",
                "externeAntragstellerId": "string",
                "familienstand": "GESCHIEDEN",
                "geburtsdatum": "2020-02-24",
                "geburtsort": "string",
                "guetertrennungVereinbartWennVerheiratet": false,
                "id": "string",
                "inDeutschlandSeit": "2020-02-24",
                "legitimationsDaten": {
                  "ausstellendeBehoerde": "string",
                  "ausstellungsdatum": "2020-02-24",
                  "ausweisArt": "PERSONALAUSWEIS",
                  "ausweisArtBeiAndererAusweis": "string",
                  "ausweisNummer": "string"
                },
                "nachname": "string",
                "schufaErgebnis": {
                  "antragstellerUnbekannt": false,
                  "inManuellerNachbehandlung": false,
                  "score": "string"
                },
                "staatsangehoerigkeit": {
                  "isoCountryCode": "string",
                  "name": "string"
                },
                "steuerId": "string",
                "telefonnummer": "string",
                "telefonnummerVorwahl": "string",
                "titel": [
                  "DOKTOR"
                ],
                "titelDoktor": true,
                "titelProfessor": true,
                "vorAnschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "vorname": "string",
                "weitereKontaktMoeglichkeiten": "string",
                "wohnhaftSeit": "2020-02-24"
              }
            ],
            "anzahlErwachseneImHaushalt": 0,
            "anzahlKinderNichtImHaushalt": 0,
            "bestehendeImmobilien": [
              {
                "adresse": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "autostellplaetze": [
                  {
                    "mieteinnahmenMonatlich": 0,
                    "typ": "STELLPLATZ"
                  }
                ],
                "bestehendeDarlehen": [
                  {
                    "abzuloesendeRestschuld": 0,
                    "aktuelleRestschuldWennNichtAbzuloesen": 0,
                    "darlehensArt": "BAUSPARDARLEHEN",
                    "darlehensBetrag": 0,
                    "darlehensGeber": {},
                    "darlehensKontonummer": "string",
                    "eingetrageneGrundschuld": 0,
                    "grundschuldArt": "BRIEF_GRUNDSCHULD",
                    "id": "string",
                    "laufzeitEnde": "2020-02-24",
                    "rateMonatlich": 0,
                    "sollZins": 0,
                    "sondertilgungZumZinsBindungsEnde": 0,
                    "zinsBindungEndetAm": "2020-02-24"
                  }
                ],
                "bewirtschaftungsKostenJaehrlich": 0,
                "bodenRichtwert": 0,
                "bundesland": "BADEN_WUERTTEMBERG",
                "effektivZinsErhoehendeKosten": {
                  "anpassen": true,
                  "grundbuchEintragungsKostenEinmalig": 0,
                  "sonstigeKostenBezeichnung": "string",
                  "sonstigeKostenEinmalig": 0,
                  "wohnGebaeudeVersicherungsKostenJaehrlich": 0
                },
                "erbbaurecht": {
                  "erbbaurecht": true,
                  "erbbauzinsJaehrlich": 0,
                  "grundstuecksEigentuemer": "ANDERE",
                  "laufzeitBisJahr": "string"
                },
                "gebaeude": {
                  "anzahlDerGewerbeeinheiten": 0,
                  "anzahlDerWohneinheitenImGebaeude": 0,
                  "anzahlVollgeschosse": 0,
                  "aufbauFinanzierung": true,
                  "aufzugVorhanden": true,
                  "ausstattung": "EINFACH",
                  "baujahr": "2016",
                  "bauweise": "FACHWERK_MIT_STROH_LEHM",
                  "bezeichnungWohneinheit": "string",
                  "dachgeschossAusbau": "FLACHDACH",
                  "einliegerwohnungVorhanden": true,
                  "geschossLage": "UNTERGESCHOSS",
                  "gewerbeflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "hausAnordnung": "FREISTEHEND",
                  "hausTyp": "DOPPELHAUSHAELFTE",
                  "istFertighaus": true,
                  "kellerausbau": "AUSGEBAUT",
                  "kubatur": 0,
                  "miteigentumsAnteil": {
                    "anteil": 0,
                    "gesamt": 0
                  },
                  "modernisierungsAngaben": {
                    "badWc": true,
                    "bodenWandTreppe": true,
                    "dach": true,
                    "fenster": true,
                    "heizungZentral": true,
                    "modernisierungsGrad": "GERING",
                    "modernisierungsJahr": "string",
                    "raumaufteilung": true,
                    "stromAbwasserHeizkoerper": true,
                    "waermedaemmung": true,
                    "wurdeModernisiert": true
                  },
                  "unterkellerung": "NICHT_UNTERKELLERT",
                  "wohnflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "zustand": "SEHR_GUT"
                },
                "grundbuchAngabe": {
                  "anmerkungen": "string",
                  "bandUndBlatt": "string",
                  "flurstuecke": [
                    {}
                  ],
                  "ort": "string",
                  "rechteInAbteilung2": {
                    "beschreibung": "string",
                    "betrag": 0,
                    "vorhanden": true
                  }
                },
                "grundstueck": {
                  "groesse": 0,
                  "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
                },
                "id": "string",
                "immobilienEinsatz": "KEIN_EINSATZ",
                "keinBaulandFlaecheInQm": 0,
                "keineBestehendenDarlehenVorhanden": true,
                "marktueblicherKaufpreisProQm": 0,
                "marktwert": 0,
                "maximalEinzusetzenderBetragWennVerkauf": 0,
                "objektArt": "GRUNDSTUECK",
                "vergleichsmieteFuerGewerbeflaecheProQm": 0,
                "vergleichsmieteFuerWohnflaecheProQm": 0,
                "verkehrswert": 0,
                "vorlaeufigerVerkehrswert": 0,
                "wohnlage": "GEHOBEN"
              }
            ],
            "id": "string",
            "kfzAnzahl": 0,
            "kinder": [
              {
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kindergeldWirdBezogen": true,
                "name": "string",
                "unterhaltsEinnahmenBetragMonatlich": 0
              }
            ],
            "lebenshaltungsKostenMonatlich": 0,
            "obligo": {
              "vermoegenOderVerbindlichkeiten": [
                {
                  "aktuellerWert": 0,
                  "anrechnungFuerBlankoAnteil": 0,
                  "bezeichner": "string",
                  "kontonummer": "string",
                  "vermoegensTyp": "VERMOEGEN"
                }
              ]
            },
            "positionen": {
              "bankUndSparguthaben": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zinsertragJaehrlich": 0,
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "bausparvertraege": [
                {
                  "abschlussGebuehr": 0,
                  "aktuellerWert": 0,
                  "bausparSumme": 0,
                  "einmalzahlung": 0,
                  "ertrag": 0,
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "produktAnbieter": {
                    "anrede": "FRAU",
                    "anschrift": {},
                    "email": "string",
                    "externePartnerId": "string",
                    "externerKreditSachbearbeiterId": "string",
                    "fax": "string",
                    "firmenNameZusatz": "string",
                    "firmierung": "string",
                    "geburtsdatum": "2020-02-24",
                    "id": "string",
                    "kreditsachbearbeiter": true,
                    "mobilTelefon": "string",
                    "nachname": "string",
                    "partnerId": "string",
                    "produktAnbieterId": "string",
                    "telefonnummer": "string",
                    "vertriebsOrganisation": {},
                    "vorname": "string",
                    "webseite": "string"
                  },
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeitragMonatlich": 0,
                  "tarif": "string",
                  "typ": "string",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "vertragsBeginn": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0,
                  "zuteilungsDatum": "2020-02-24"
                }
              ],
              "ehegattenUnterhalt": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "einkuenfteAusNebentaetigkeit": [
                {
                  "beginnDerNebentaetigkeit": "2020-02-24",
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "kindergeld": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "lebensUndRentenVersicherungen": [
                {
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "praemieMonatlich": 0,
                  "rueckkaufsWertAktuell": 0,
                  "tarif": "string",
                  "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "versicherungsGesellschaft": "string",
                  "versicherungsSumme": 0,
                  "vertragsBeginn": "2020-02-24",
                  "vertragsEnde": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "mietAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "entfallenMitFinanzierung": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateDarlehen": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateKrankenversicherung": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "ratenkredite": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeEinnahmen": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVerbindlichkeiten": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVermoegen": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "sparplaene": [
                {
                  "aktuellerWert": 0,
                  "beitragMonatlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "unbefristeteZusatzRenten": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "unterhaltsVerpflichtungen": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "variableEinkuenfte": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "versicherungsAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "wertpapiere": [
                {
                  "aktuellerWert": 0,
                  "dividendenJaehrlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ]
            }
          }
        ],
        "vorhaben": {
          "absicherungswunsch": {
            "id": "string",
            "versicherungsWuensche": [
              {
                "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
                "id": "string",
                "praemienZahlungsweise": "EINMALIG",
                "risikoAbsicherungsWuensche": [
                  {
                    "abzusicherndesRisiko": "TODESFALL",
                    "versicherteRate": 0,
                    "versicherungsSumme": 0
                  }
                ],
                "versichertePersonId": "string",
                "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
                "versicherungsBeginn": "2020-02-24",
                "versicherungsDauerInMonaten": 0
              }
            ]
          },
          "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
          "externeBausparAngebote": [
            {
              "abschlussGebuehr": 0,
              "angebotsHinweisFuerAntragsteller": "string",
              "bausparSumme": 0,
              "einmalzahlung": 0,
              "id": "string",
              "produktAnbieter": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparPhase": {
                "guthabenBeiZuteilung": 0,
                "sparBeitragMonatlich": 0,
                "sparPhaseInJahren": 0
              },
              "tarif": "string",
              "tilgungsPhase": {
                "bausparDarlehenSumme": 0,
                "sollZinsNachZuteilung": 0,
                "tilgungsBeitragMonatlich": 0,
                "tilgungsPhaseInJahren": 0
              },
              "typ": "string",
              "vertragsBeginn": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zuteilungsDatum": "2020-02-24"
            }
          ],
          "finanzbedarf": {
            "anzahlTeilzahlungen": 0,
            "aussenAnlagen": 0,
            "bauNebenkosten": 0,
            "beratungsHonorar": 0,
            "bereitsBeglichen": 0,
            "erschliessung": 0,
            "grunderwerbsteuer": 0,
            "grundstueckBereitsBezahlt": true,
            "grundstuecksKaufpreis": 0,
            "herstellung": 0,
            "kapitalBeschaffung": 0,
            "kapitalWirdBeschafft": true,
            "kaufpreis": 0,
            "maklergebuehr": 0,
            "mobiliar": 0,
            "modernisieren": true,
            "modernisierung": 0,
            "notargebuehr": 0,
            "renovierung": 0,
            "sonstigeKosten": 0,
            "zusaetzlichesKapital": 0
          },
          "finanzierungswunsch": {
            "bausparWuensche": [
              {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              }
            ],
            "darlehensWuensche": [
              {
                "annuitaetenDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "forwardDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "id": "string",
                "kfwDarlehen": {
                  "darlehensBetrag": 0,
                  "kfwEndfaellig": "NEIN",
                  "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
                  "kfwProgramm": "PROGRAMM_124",
                  "laufzeitInJahren": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "tilgungsfreieAnlaufjahre": 0,
                  "zinsBindungInJahren": 0
                },
                "privatDarlehen": {
                  "darlehensBetrag": 0,
                  "laufzeitInMonaten": 0,
                  "provision": 0
                },
                "variablesDarlehen": {
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  }
                },
                "zwischenFinanzierung": {
                  "darlehensBetrag": 0,
                  "detailsZurVerwendung": "string",
                  "maximaleLaufzeitInMonaten": 0,
                  "provision": 0,
                  "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
                }
              }
            ],
            "id": "string"
          },
          "id": "string",
          "nachfinanzierung": true,
          "nachrangigeExterneDarlehen": [
            {
              "darlehensBetrag": 0,
              "darlehensGeber": "string",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "typ": "ARBEITGEBERDARLEHEN",
              "zinsBindung": {
                "endetAm": "2020-02-24",
                "jahre": 0,
                "monate": 0,
                "restschuldNachZinsBindungsEnde": 0
              }
            }
          ],
          "praeferenzen": {
            "bereitstellungsZinsFreieZeit": {
              "darlehenBenoetigtInMonaten": 0,
              "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
              "zusatzlicheKommentare": "string"
            },
            "bestandteileDerFinanzierung": {
              "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
              "zusatzlicheKommentare": "string"
            },
            "hoeheDerRate": {
              "betrag": 0,
              "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
              "zusatzlicheKommentare": "string"
            },
            "laufzeit": {
              "bisZumJahr": "2016",
              "bisZurRenteImJahr": "2016",
              "inJahren": 0,
              "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
              "zusatzlicheKommentare": "string"
            },
            "sondertilgung": {
              "betragEinmalig": 0,
              "betragJaehrlich": 0,
              "praeferenzAuswahl": "JAEHRLICH",
              "zusatzlicheKommentare": "string"
            },
            "tilgungsSatzWechsel": {
              "mindestensBenoetigt": 0,
              "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
              "zusatzlicheKommentare": "string"
            },
            "weiterePraeferenz": "string",
            "zeitlicherRahmen": {
              "finanzierungszusageBis": "2020-02-24",
              "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
              "zusatzlicheKommentare": "string"
            },
            "zinsBindung": {
              "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
              "zinsBindungBisJahren": 0,
              "zinsBindungVonJahren": 0,
              "zinsBindungZwischenJahren": 0,
              "zusatzlicheKommentare": "string"
            }
          },
          "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
        }
      },
      "_links": {
        "self": {
          "href": "string",
          "type": "string"
        }
      }
    }
  ],
  "archivierung": {
    "grund": "VORGANG_ERFOLGREICH_ABGESCHLOSSEN",
    "kommentar": "string"
  },
  "aufbewahrungBis": "2020-02-24",
  "bankverbindung": {
    "bic": "string",
    "iban": "string",
    "id": "string",
    "kontoinhaberIds": [
      "string"
    ],
    "kontoinhaberName": "string",
    "kreditinstitut": "string"
  },
  "datenKontext": "TEST_MODUS",
  "erstelltAm": "2020-02-24",
  "externeVorgangsNummer": "string",
  "finanzierungsObjekt": {
    "adresse": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "autostellplaetze": [
      {
        "mieteinnahmenMonatlich": 0,
        "typ": "STELLPLATZ"
      }
    ],
    "bestehendeDarlehen": [
      {
        "abzuloesendeRestschuld": 0,
        "aktuelleRestschuldWennNichtAbzuloesen": 0,
        "darlehensArt": "BAUSPARDARLEHEN",
        "darlehensBetrag": 0,
        "darlehensGeber": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "darlehensKontonummer": "string",
        "eingetrageneGrundschuld": 0,
        "grundschuldArt": "BRIEF_GRUNDSCHULD",
        "id": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "sollZins": 0,
        "sondertilgungZumZinsBindungsEnde": 0,
        "verwendenAls": "ABLOESEN",
        "zinsBindungEndetAm": "2020-02-24"
      }
    ],
    "bewirtschaftungsKostenJaehrlich": 0,
    "bodenRichtwert": 0,
    "bundesland": "BADEN_WUERTTEMBERG",
    "effektivZinsErhoehendeKosten": {
      "anpassen": true,
      "grundbuchEintragungsKostenEinmalig": 0,
      "sonstigeKostenBezeichnung": "string",
      "sonstigeKostenEinmalig": 0,
      "wohnGebaeudeVersicherungsKostenJaehrlich": 0
    },
    "erbbaurecht": {
      "erbbaurecht": true,
      "erbbauzinsJaehrlich": 0,
      "grundstuecksEigentuemer": "ANDERE",
      "laufzeitBisJahr": "string"
    },
    "gebaeude": {
      "anzahlDerGewerbeeinheiten": 0,
      "anzahlDerWohneinheitenImGebaeude": 0,
      "anzahlVollgeschosse": 0,
      "aufbauFinanzierung": true,
      "aufzugVorhanden": true,
      "ausstattung": "EINFACH",
      "baujahr": "2016",
      "bauweise": "FACHWERK_MIT_STROH_LEHM",
      "bezeichnungWohneinheit": "string",
      "dachgeschossAusbau": "FLACHDACH",
      "einliegerwohnungVorhanden": true,
      "geschossLage": "UNTERGESCHOSS",
      "gewerbeflaeche": {
        "gesamtGroesse": 0,
        "vermietungsInformationen": {
          "mieteinnahmenNettoKaltMonatlich": 0,
          "nutzungsArt": "EIGENGENUTZT",
          "vermieteteFlaeche": 0
        }
      },
      "hausAnordnung": "FREISTEHEND",
      "hausTyp": "DOPPELHAUSHAELFTE",
      "istFertighaus": true,
      "kellerausbau": "AUSGEBAUT",
      "kubatur": 0,
      "miteigentumsAnteil": {
        "anteil": 0,
        "gesamt": 0
      },
      "modernisierungsAngaben": {
        "badWc": true,
        "bodenWandTreppe": true,
        "dach": true,
        "fenster": true,
        "heizungZentral": true,
        "modernisierungsGrad": "GERING",
        "modernisierungsJahr": "string",
        "raumaufteilung": true,
        "stromAbwasserHeizkoerper": true,
        "waermedaemmung": true,
        "wurdeModernisiert": true
      },
      "unterkellerung": "NICHT_UNTERKELLERT",
      "wohnflaeche": {
        "gesamtGroesse": 0,
        "vermietungsInformationen": {
          "mieteinnahmenNettoKaltMonatlich": 0,
          "nutzungsArt": "EIGENGENUTZT",
          "vermieteteFlaeche": 0
        }
      },
      "zustand": "SEHR_GUT"
    },
    "grundbuchAngabe": {
      "anmerkungen": "string",
      "bandUndBlatt": "string",
      "flurstuecke": [
        {
          "anteil": {
            "anteil": 0,
            "gesamt": 0
          },
          "flur": "string",
          "flurstuecksNummer": "string",
          "groesse": 0
        }
      ],
      "ort": "string",
      "rechteInAbteilung2": {
        "beschreibung": "string",
        "betrag": 0,
        "vorhanden": true
      }
    },
    "grundstueck": {
      "groesse": 0,
      "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
    },
    "id": "string",
    "keinBaulandFlaecheInQm": 0,
    "marktueblicherKaufpreisProQm": 0,
    "marktwert": 0,
    "objektArt": "GRUNDSTUECK",
    "vergleichsmieteFuerGewerbeflaecheProQm": 0,
    "vergleichsmieteFuerWohnflaecheProQm": 0,
    "verkehrswert": 0,
    "vorlaeufigerVerkehrswert": 0,
    "wohnlage": "GEHOBEN"
  },
  "geschlossenAm": "2020-02-24",
  "haushalte": [
    {
      "antragsteller": [
        {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "arbeitserlaubnis": false,
          "arbeitserlaubnisBefristetBis": "2020-02-24",
          "aufenthaltsTitel": "VISUM",
          "aufenthaltsTitelBefristetBis": "2020-02-24",
          "beschaeftigung": {
            "anzahlGehaelterProJahr": 0,
            "arbeitgeber": "string",
            "arbeitgeberInDeutschlandAnsaessig": false,
            "arbeitgeberLand": {
              "isoCountryCode": "string",
              "name": "string"
            },
            "art": "ANGESTELLTER",
            "befristungsStatus": "BEFRISTET",
            "beruf": "string",
            "beschaeftigtSeit": "2020-02-24",
            "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
            "einkommenNettoJaehrlich": 0,
            "einkommenNettoMonatlich": 0,
            "firma": "string",
            "inProbezeit": false,
            "situationNachRenteneintritt": {
              "gesetzlicheRenteMonatlich": 0,
              "privateRenteMonatlich": 0,
              "rentenBeginn": "2020-02-24",
              "sonstigesEinkommenMonatlich": 0
            },
            "taetigkeit": "ALTENPFLEGER"
          },
          "bruttoVorjahresEinkommen": 0,
          "email": "max.mustermann@test.de",
          "externeAntragstellerId": "string",
          "familienstand": "GESCHIEDEN",
          "geburtsdatum": "2020-02-24",
          "geburtsort": "string",
          "guetertrennungVereinbartWennVerheiratet": false,
          "id": "string",
          "inDeutschlandSeit": "2020-02-24",
          "legitimationsDaten": {
            "ausstellendeBehoerde": "string",
            "ausstellungsdatum": "2020-02-24",
            "ausweisArt": "PERSONALAUSWEIS",
            "ausweisArtBeiAndererAusweis": "string",
            "ausweisNummer": "string"
          },
          "nachname": "string",
          "schufaErgebnis": {
            "antragstellerUnbekannt": false,
            "inManuellerNachbehandlung": false,
            "score": "string"
          },
          "staatsangehoerigkeit": {
            "isoCountryCode": "string",
            "name": "string"
          },
          "steuerId": "string",
          "telefonnummer": "string",
          "telefonnummerVorwahl": "string",
          "titel": [
            "DOKTOR"
          ],
          "titelDoktor": true,
          "titelProfessor": true,
          "vorAnschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "vorname": "string",
          "weitereKontaktMoeglichkeiten": "string",
          "wohnhaftSeit": "2020-02-24"
        }
      ],
      "anzahlErwachseneImHaushalt": 0,
      "anzahlKinderNichtImHaushalt": 0,
      "bestehendeImmobilien": [
        {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "immobilienEinsatz": "KEIN_EINSATZ",
          "keinBaulandFlaecheInQm": 0,
          "keineBestehendenDarlehenVorhanden": true,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "maximalEinzusetzenderBetragWennVerkauf": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        }
      ],
      "id": "string",
      "kfzAnzahl": 0,
      "kinder": [
        {
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kindergeldWirdBezogen": true,
          "name": "string",
          "unterhaltsEinnahmenBetragMonatlich": 0
        }
      ],
      "lebenshaltungsKostenMonatlich": 0,
      "obligo": {
        "vermoegenOderVerbindlichkeiten": [
          {
            "aktuellerWert": 0,
            "anrechnungFuerBlankoAnteil": 0,
            "bezeichner": "string",
            "kontonummer": "string",
            "vermoegensTyp": "VERMOEGEN"
          }
        ]
      },
      "positionen": {
        "bankUndSparguthaben": [
          {
            "aktuellerWert": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zinsertragJaehrlich": 0,
            "zukuenftigeEinnahmen": 0
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "aktuellerWert": 0,
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "ertrag": 0,
            "id": "string",
            "maximalAufzuloesenderBetrag": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeitragMonatlich": 0,
            "tarif": "string",
            "typ": "string",
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "ehegattenUnterhalt": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "einkuenfteAusNebentaetigkeit": [
          {
            "beginnDerNebentaetigkeit": "2020-02-24",
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "kindergeld": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "lebensUndRentenVersicherungen": [
          {
            "id": "string",
            "maximalAufzuloesenderBetrag": 0,
            "praemieMonatlich": 0,
            "rueckkaufsWertAktuell": 0,
            "tarif": "string",
            "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "versicherungsGesellschaft": "string",
            "versicherungsSumme": 0,
            "vertragsBeginn": "2020-02-24",
            "vertragsEnde": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "mietAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "entfallenMitFinanzierung": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "privateDarlehen": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "privateKrankenversicherung": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "ratenkredite": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeEinnahmen": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeVerbindlichkeiten": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeVermoegen": [
          {
            "aktuellerWert": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zukuenftigeEinnahmen": 0
          }
        ],
        "sparplaene": [
          {
            "aktuellerWert": 0,
            "beitragMonatlich": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0
          }
        ],
        "unbefristeteZusatzRenten": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "unterhaltsVerpflichtungen": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "variableEinkuenfte": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "versicherungsAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "wertpapiere": [
          {
            "aktuellerWert": 0,
            "dividendenJaehrlich": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0
          }
        ]
      }
    }
  ],
  "importQuelle": "string",
  "kundenBetreuer": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "leadTracking": {
    "kampagne": "string",
    "keyword": "string",
    "kundenBetreuerBenachrichtigen": true,
    "trackingId": "string"
  },
  "letztesEreignis": "2020-02-24T11:55:47Z",
  "phase": "string",
  "prioritaet": "NIEDRIG",
  "status": "string",
  "tippGeber": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "vorgangsBearbeiter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "vorgangsNummer": "string",
  "vorhaben": {
    "absicherungswunsch": {
      "id": "string",
      "versicherungsWuensche": [
        {
          "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
          "id": "string",
          "praemienZahlungsweise": "EINMALIG",
          "risikoAbsicherungsWuensche": [
            {
              "abzusicherndesRisiko": "TODESFALL",
              "versicherteRate": 0,
              "versicherungsSumme": 0
            }
          ],
          "versichertePersonId": "string",
          "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
          "versicherungsBeginn": "2020-02-24",
          "versicherungsDauerInMonaten": 0
        }
      ]
    },
    "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
    "externeBausparAngebote": [
      {
        "abschlussGebuehr": 0,
        "angebotsHinweisFuerAntragsteller": "string",
        "bausparSumme": 0,
        "einmalzahlung": 0,
        "id": "string",
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparPhase": {
          "guthabenBeiZuteilung": 0,
          "sparBeitragMonatlich": 0,
          "sparPhaseInJahren": 0
        },
        "tarif": "string",
        "tilgungsPhase": {
          "bausparDarlehenSumme": 0,
          "sollZinsNachZuteilung": 0,
          "tilgungsBeitragMonatlich": 0,
          "tilgungsPhaseInJahren": 0
        },
        "typ": "string",
        "vertragsBeginn": "2020-02-24",
        "vertragsNummer": "string",
        "verwaltungsgebuehrenJaehrlich": 0,
        "zuteilungsDatum": "2020-02-24"
      }
    ],
    "finanzbedarf": {
      "anzahlTeilzahlungen": 0,
      "aussenAnlagen": 0,
      "bauNebenkosten": 0,
      "beratungsHonorar": 0,
      "bereitsBeglichen": 0,
      "erschliessung": 0,
      "grunderwerbsteuer": 0,
      "grundstueckBereitsBezahlt": true,
      "grundstuecksKaufpreis": 0,
      "herstellung": 0,
      "kapitalBeschaffung": 0,
      "kapitalWirdBeschafft": true,
      "kaufpreis": 0,
      "maklergebuehr": 0,
      "mobiliar": 0,
      "modernisieren": true,
      "modernisierung": 0,
      "notargebuehr": 0,
      "renovierung": 0,
      "sonstigeKosten": 0,
      "zusaetzlichesKapital": 0
    },
    "finanzierungswunsch": {
      "bausparWuensche": [
        {
          "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
          "bausparSummeAbsolut": 0,
          "bausparSummeRelativ": 0,
          "bausparTarif": [
            {
              "id": "string",
              "kurzName": "string",
              "langName": "string",
              "produktAnbieter": "string",
              "riesterFoerderung": true,
              "status": "AKTIV"
            }
          ],
          "bausparTarife": [
            "string"
          ],
          "id": "string",
          "sonderZahlungEinmalig": 0,
          "sonderZahlungen": [
            {
              "anzahl": 0,
              "betrag": 0,
              "termin": "2020-02-24",
              "zahlweise": "EINMALIG"
            }
          ],
          "sparBeginn": "2020-02-24",
          "sparBeitragMonatlichAbsolut": 0,
          "sparBeitragMonatlichRelativ": 0,
          "tilgungsBeitragMonatlich": 0,
          "vertragsPartnerIds": [
            "string"
          ],
          "verwendung": "ZINS_ABSICHERUNG",
          "zuteilungsDatum": "2020-02-24"
        }
      ],
      "darlehensWuensche": [
        {
          "annuitaetenDarlehen": {
            "auszahlungsDatum": "2020-02-24",
            "bereitstellungsZinsFreieZeitInMonaten": 0,
            "darlehensBetrag": 0,
            "provision": 0,
            "sondertilgungOptionalJaehrlich": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "zinsBindungInJahren": 0
          },
          "forwardDarlehen": {
            "auszahlungsDatum": "2020-02-24",
            "bereitstellungsZinsFreieZeitInMonaten": 0,
            "darlehensBetrag": 0,
            "provision": 0,
            "sondertilgungOptionalJaehrlich": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "zinsBindungInJahren": 0
          },
          "id": "string",
          "kfwDarlehen": {
            "darlehensBetrag": 0,
            "kfwEndfaellig": "NEIN",
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "laufzeitInJahren": 0,
            "provision": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "tilgungsfreieAnlaufjahre": 0,
            "zinsBindungInJahren": 0
          },
          "privatDarlehen": {
            "darlehensBetrag": 0,
            "laufzeitInMonaten": 0,
            "provision": 0
          },
          "variablesDarlehen": {
            "darlehensBetrag": 0,
            "provision": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            }
          },
          "zwischenFinanzierung": {
            "darlehensBetrag": 0,
            "detailsZurVerwendung": "string",
            "maximaleLaufzeitInMonaten": 0,
            "provision": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
          }
        }
      ],
      "id": "string"
    },
    "id": "string",
    "nachfinanzierung": true,
    "nachrangigeExterneDarlehen": [
      {
        "darlehensBetrag": 0,
        "darlehensGeber": "string",
        "id": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "typ": "ARBEITGEBERDARLEHEN",
        "zinsBindung": {
          "endetAm": "2020-02-24",
          "jahre": 0,
          "monate": 0,
          "restschuldNachZinsBindungsEnde": 0
        }
      }
    ],
    "praeferenzen": {
      "bereitstellungsZinsFreieZeit": {
        "darlehenBenoetigtInMonaten": 0,
        "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
        "zusatzlicheKommentare": "string"
      },
      "bestandteileDerFinanzierung": {
        "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
        "zusatzlicheKommentare": "string"
      },
      "hoeheDerRate": {
        "betrag": 0,
        "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
        "zusatzlicheKommentare": "string"
      },
      "laufzeit": {
        "bisZumJahr": "2016",
        "bisZurRenteImJahr": "2016",
        "inJahren": 0,
        "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
        "zusatzlicheKommentare": "string"
      },
      "sondertilgung": {
        "betragEinmalig": 0,
        "betragJaehrlich": 0,
        "praeferenzAuswahl": "JAEHRLICH",
        "zusatzlicheKommentare": "string"
      },
      "tilgungsSatzWechsel": {
        "mindestensBenoetigt": 0,
        "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
        "zusatzlicheKommentare": "string"
      },
      "weiterePraeferenz": "string",
      "zeitlicherRahmen": {
        "finanzierungszusageBis": "2020-02-24",
        "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
        "zusatzlicheKommentare": "string"
      },
      "zinsBindung": {
        "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
        "zinsBindungBisJahren": 0,
        "zinsBindungVonJahren": 0,
        "zinsBindungZwischenJahren": 0,
        "zusatzlicheKommentare": "string"
      }
    },
    "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
  },
  "_links": {
    "antraege": {
      "href": "string",
      "type": "string"
    },
    "ereignisse": {
      "href": "string",
      "type": "string"
    },
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}
```

<h3 id="updatevorgang-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Vorgang](#schemavorgang)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### getAllVorgangsAntraege

<a id="opIdgetAllVorgangsAntraege"></a>

> Code samples

```shell
## You can also use wget
curl -X GET https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /v2/vorgaenge/{vorgangsNummer}/antraege`

*Alle Anträge zum Vorgang*

<h3 id="getallvorgangsantraege-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|

> Example responses

> 200 Response

```json
{
  "antraege": [
    {
      "angebot": {
        "absicherungen": [
          {
            "abgesicherteRisiken": [
              {
                "abgesichertesRisiko": "TODESFALL",
                "auszahlungsBetrag": 0,
                "auszahlungsTurnus": "EINMALIG",
                "praemienAnteil": 0
              }
            ],
            "gesamtPraemie": 0,
            "praemienZahlungsweise": "EINMALIG",
            "tarifBezeichnung": "string",
            "tarifKennung": "string",
            "versichertePersonId": "string",
            "versicherungsArt": "string",
            "versicherungsNummer": "string",
            "versicherungsZeitraum": {
              "beginn": "2020-02-24",
              "dauerInMonaten": 0,
              "ende": "2020-02-24"
            }
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "angebotsHinweisFuerAntragsteller": "string",
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "gesamtLaufzeitInJahren": 0,
            "id": "string",
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparPhase": {
              "guthabenBeiZuteilung": 0,
              "sparBeitragMonatlich": 0,
              "sparPhaseInJahren": 0
            },
            "tarif": "string",
            "tilgungsPhase": {
              "bausparDarlehenSumme": 0,
              "sollZinsNachZuteilung": 0,
              "tilgungsBeitragMonatlich": 0,
              "tilgungsPhaseInJahren": 0
            },
            "typ": "string",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "beleihungsRechnung": {
          "beleihungsAuslauf": 0,
          "beleihungsWerte": [
            {
              "beleihungsWert": 0,
              "immobilie": {
                "id": "string"
              }
            }
          ],
          "beleihungsWerteSumme": 0,
          "produktAnbieter": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          }
        },
        "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
        "darlehen": [
          {
            "auszahlungsBetrag": 0,
            "auszahlungsDatum": "2020-02-24",
            "auszahlungsKurs": 0,
            "bereitstellung": {
              "bereitstellungsZins": 0,
              "bereitstellungsZinsFreieZeitInMonaten": 0
            },
            "darlehensBetrag": 0,
            "darlehensTyp": "ANNUITAETEN_DARLEHEN",
            "detailsZurVerwendung": "string",
            "effektivZins": 0,
            "effektivZinsRelevanteKosten": {
              "beratungsHonorar": 0,
              "grundbuchKosten": 0,
              "sonstigeKosten": 0,
              "tilgungsErsatzProduktKosten": 0,
              "wohnGebaeudeVersicherungsKosten": 0,
              "zinsabsicherungsKosten": 0,
              "zusatzSicherheitsKosten": 0
            },
            "forwardPeriodeInMonaten": 0,
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "konditionWurdeManuellAngepasst": true,
            "konditionsAnpassungsBegruendung": "string",
            "laufZeitInJahren": 0,
            "laufzeitInMonaten": 0,
            "maximaleLaufzeitInMonaten": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "rateMonatlich": 123.34,
            "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
            "sollZins": 2.05,
            "tilgung": {
              "anfaenglicheTilgung": 0,
              "sonderTilgungJaehrlich": 0,
              "tilgungsBeginnAm": "2020-02-24",
              "tilgungsErsatz": {
                "id": "string",
                "typ": "string"
              }
            },
            "tilgungsFreieAnlaufJahre": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
            "zinsBindung": {
              "endetAm": "2020-02-24",
              "jahre": 0,
              "monate": 0,
              "restschuldNachZinsBindungsEnde": 0
            },
            "zinsZahlungsBeginnAm": "2020-02-24"
          }
        ],
        "erzeugtAm": "2020-02-24T11:55:47Z",
        "kennung": "string",
        "machbarkeitsStatus": "MACHBAR",
        "meldungen": [
          {
            "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
            "kreditEntscheider": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "text": "string"
          }
        ],
        "pruefungsErgebnisse": [
          {
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "weitereAngaben": "string"
          }
        ],
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "ansprechpartner": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "antragsNummer": "string",
      "beratung": {
        "art": "PRAESENZ_GESCHAEFT",
        "hinweisFuerProduktAnbieter": "string",
        "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
      },
      "datenKontext": "TEST_MODUS",
      "dokumente": [
        {
          "art": "string",
          "href": "string",
          "name": "string",
          "titel": "string",
          "type": "string"
        }
      ],
      "kreditSachbearbeiter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "status": {
        "ablehnungsgrund": "FINANZIELLE_SITUATION",
        "antragsteller": "BEANTRAGT",
        "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
        "produktAnbieter": "NICHT_BEARBEITET"
      },
      "vermittler": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "zeitpunktDerAnnahme": "2020-02-24T11:55:47Z",
      "zugrundeliegendeDaten": {
        "bankverbindung": {
          "bic": "string",
          "iban": "string",
          "id": "string",
          "kontoinhaberIds": [
            "string"
          ],
          "kontoinhaberName": "string",
          "kreditinstitut": "string"
        },
        "finanzierungsObjekt": {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "verwendenAls": "ABLOESEN",
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "keinBaulandFlaecheInQm": 0,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        },
        "haushalte": [
          {
            "antragsteller": [
              {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "arbeitserlaubnis": false,
                "arbeitserlaubnisBefristetBis": "2020-02-24",
                "aufenthaltsTitel": "VISUM",
                "aufenthaltsTitelBefristetBis": "2020-02-24",
                "beschaeftigung": {
                  "anzahlGehaelterProJahr": 0,
                  "arbeitgeber": "string",
                  "arbeitgeberInDeutschlandAnsaessig": false,
                  "arbeitgeberLand": {
                    "isoCountryCode": "string",
                    "name": "string"
                  },
                  "art": "ANGESTELLTER",
                  "befristungsStatus": "BEFRISTET",
                  "beruf": "string",
                  "beschaeftigtSeit": "2020-02-24",
                  "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
                  "einkommenNettoJaehrlich": 0,
                  "einkommenNettoMonatlich": 0,
                  "firma": "string",
                  "inProbezeit": false,
                  "situationNachRenteneintritt": {
                    "gesetzlicheRenteMonatlich": 0,
                    "privateRenteMonatlich": 0,
                    "rentenBeginn": "2020-02-24",
                    "sonstigesEinkommenMonatlich": 0
                  },
                  "taetigkeit": "ALTENPFLEGER"
                },
                "bruttoVorjahresEinkommen": 0,
                "email": "max.mustermann@test.de",
                "externeAntragstellerId": "string",
                "familienstand": "GESCHIEDEN",
                "geburtsdatum": "2020-02-24",
                "geburtsort": "string",
                "guetertrennungVereinbartWennVerheiratet": false,
                "id": "string",
                "inDeutschlandSeit": "2020-02-24",
                "legitimationsDaten": {
                  "ausstellendeBehoerde": "string",
                  "ausstellungsdatum": "2020-02-24",
                  "ausweisArt": "PERSONALAUSWEIS",
                  "ausweisArtBeiAndererAusweis": "string",
                  "ausweisNummer": "string"
                },
                "nachname": "string",
                "schufaErgebnis": {
                  "antragstellerUnbekannt": false,
                  "inManuellerNachbehandlung": false,
                  "score": "string"
                },
                "staatsangehoerigkeit": {
                  "isoCountryCode": "string",
                  "name": "string"
                },
                "steuerId": "string",
                "telefonnummer": "string",
                "telefonnummerVorwahl": "string",
                "titel": [
                  "DOKTOR"
                ],
                "titelDoktor": true,
                "titelProfessor": true,
                "vorAnschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "vorname": "string",
                "weitereKontaktMoeglichkeiten": "string",
                "wohnhaftSeit": "2020-02-24"
              }
            ],
            "anzahlErwachseneImHaushalt": 0,
            "anzahlKinderNichtImHaushalt": 0,
            "bestehendeImmobilien": [
              {
                "adresse": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "autostellplaetze": [
                  {
                    "mieteinnahmenMonatlich": 0,
                    "typ": "STELLPLATZ"
                  }
                ],
                "bestehendeDarlehen": [
                  {
                    "abzuloesendeRestschuld": 0,
                    "aktuelleRestschuldWennNichtAbzuloesen": 0,
                    "darlehensArt": "BAUSPARDARLEHEN",
                    "darlehensBetrag": 0,
                    "darlehensGeber": {},
                    "darlehensKontonummer": "string",
                    "eingetrageneGrundschuld": 0,
                    "grundschuldArt": "BRIEF_GRUNDSCHULD",
                    "id": "string",
                    "laufzeitEnde": "2020-02-24",
                    "rateMonatlich": 0,
                    "sollZins": 0,
                    "sondertilgungZumZinsBindungsEnde": 0,
                    "zinsBindungEndetAm": "2020-02-24"
                  }
                ],
                "bewirtschaftungsKostenJaehrlich": 0,
                "bodenRichtwert": 0,
                "bundesland": "BADEN_WUERTTEMBERG",
                "effektivZinsErhoehendeKosten": {
                  "anpassen": true,
                  "grundbuchEintragungsKostenEinmalig": 0,
                  "sonstigeKostenBezeichnung": "string",
                  "sonstigeKostenEinmalig": 0,
                  "wohnGebaeudeVersicherungsKostenJaehrlich": 0
                },
                "erbbaurecht": {
                  "erbbaurecht": true,
                  "erbbauzinsJaehrlich": 0,
                  "grundstuecksEigentuemer": "ANDERE",
                  "laufzeitBisJahr": "string"
                },
                "gebaeude": {
                  "anzahlDerGewerbeeinheiten": 0,
                  "anzahlDerWohneinheitenImGebaeude": 0,
                  "anzahlVollgeschosse": 0,
                  "aufbauFinanzierung": true,
                  "aufzugVorhanden": true,
                  "ausstattung": "EINFACH",
                  "baujahr": "2016",
                  "bauweise": "FACHWERK_MIT_STROH_LEHM",
                  "bezeichnungWohneinheit": "string",
                  "dachgeschossAusbau": "FLACHDACH",
                  "einliegerwohnungVorhanden": true,
                  "geschossLage": "UNTERGESCHOSS",
                  "gewerbeflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "hausAnordnung": "FREISTEHEND",
                  "hausTyp": "DOPPELHAUSHAELFTE",
                  "istFertighaus": true,
                  "kellerausbau": "AUSGEBAUT",
                  "kubatur": 0,
                  "miteigentumsAnteil": {
                    "anteil": 0,
                    "gesamt": 0
                  },
                  "modernisierungsAngaben": {
                    "badWc": true,
                    "bodenWandTreppe": true,
                    "dach": true,
                    "fenster": true,
                    "heizungZentral": true,
                    "modernisierungsGrad": "GERING",
                    "modernisierungsJahr": "string",
                    "raumaufteilung": true,
                    "stromAbwasserHeizkoerper": true,
                    "waermedaemmung": true,
                    "wurdeModernisiert": true
                  },
                  "unterkellerung": "NICHT_UNTERKELLERT",
                  "wohnflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "zustand": "SEHR_GUT"
                },
                "grundbuchAngabe": {
                  "anmerkungen": "string",
                  "bandUndBlatt": "string",
                  "flurstuecke": [
                    {}
                  ],
                  "ort": "string",
                  "rechteInAbteilung2": {
                    "beschreibung": "string",
                    "betrag": 0,
                    "vorhanden": true
                  }
                },
                "grundstueck": {
                  "groesse": 0,
                  "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
                },
                "id": "string",
                "immobilienEinsatz": "KEIN_EINSATZ",
                "keinBaulandFlaecheInQm": 0,
                "keineBestehendenDarlehenVorhanden": true,
                "marktueblicherKaufpreisProQm": 0,
                "marktwert": 0,
                "maximalEinzusetzenderBetragWennVerkauf": 0,
                "objektArt": "GRUNDSTUECK",
                "vergleichsmieteFuerGewerbeflaecheProQm": 0,
                "vergleichsmieteFuerWohnflaecheProQm": 0,
                "verkehrswert": 0,
                "vorlaeufigerVerkehrswert": 0,
                "wohnlage": "GEHOBEN"
              }
            ],
            "id": "string",
            "kfzAnzahl": 0,
            "kinder": [
              {
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kindergeldWirdBezogen": true,
                "name": "string",
                "unterhaltsEinnahmenBetragMonatlich": 0
              }
            ],
            "lebenshaltungsKostenMonatlich": 0,
            "obligo": {
              "vermoegenOderVerbindlichkeiten": [
                {
                  "aktuellerWert": 0,
                  "anrechnungFuerBlankoAnteil": 0,
                  "bezeichner": "string",
                  "kontonummer": "string",
                  "vermoegensTyp": "VERMOEGEN"
                }
              ]
            },
            "positionen": {
              "bankUndSparguthaben": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zinsertragJaehrlich": 0,
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "bausparvertraege": [
                {
                  "abschlussGebuehr": 0,
                  "aktuellerWert": 0,
                  "bausparSumme": 0,
                  "einmalzahlung": 0,
                  "ertrag": 0,
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "produktAnbieter": {
                    "anrede": "FRAU",
                    "anschrift": {},
                    "email": "string",
                    "externePartnerId": "string",
                    "externerKreditSachbearbeiterId": "string",
                    "fax": "string",
                    "firmenNameZusatz": "string",
                    "firmierung": "string",
                    "geburtsdatum": "2020-02-24",
                    "id": "string",
                    "kreditsachbearbeiter": true,
                    "mobilTelefon": "string",
                    "nachname": "string",
                    "partnerId": "string",
                    "produktAnbieterId": "string",
                    "telefonnummer": "string",
                    "vertriebsOrganisation": {},
                    "vorname": "string",
                    "webseite": "string"
                  },
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeitragMonatlich": 0,
                  "tarif": "string",
                  "typ": "string",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "vertragsBeginn": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0,
                  "zuteilungsDatum": "2020-02-24"
                }
              ],
              "ehegattenUnterhalt": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "einkuenfteAusNebentaetigkeit": [
                {
                  "beginnDerNebentaetigkeit": "2020-02-24",
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "kindergeld": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "lebensUndRentenVersicherungen": [
                {
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "praemieMonatlich": 0,
                  "rueckkaufsWertAktuell": 0,
                  "tarif": "string",
                  "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "versicherungsGesellschaft": "string",
                  "versicherungsSumme": 0,
                  "vertragsBeginn": "2020-02-24",
                  "vertragsEnde": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "mietAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "entfallenMitFinanzierung": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateDarlehen": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateKrankenversicherung": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "ratenkredite": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeEinnahmen": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVerbindlichkeiten": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVermoegen": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "sparplaene": [
                {
                  "aktuellerWert": 0,
                  "beitragMonatlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "unbefristeteZusatzRenten": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "unterhaltsVerpflichtungen": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "variableEinkuenfte": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "versicherungsAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "wertpapiere": [
                {
                  "aktuellerWert": 0,
                  "dividendenJaehrlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ]
            }
          }
        ],
        "vorhaben": {
          "absicherungswunsch": {
            "id": "string",
            "versicherungsWuensche": [
              {
                "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
                "id": "string",
                "praemienZahlungsweise": "EINMALIG",
                "risikoAbsicherungsWuensche": [
                  {
                    "abzusicherndesRisiko": "TODESFALL",
                    "versicherteRate": 0,
                    "versicherungsSumme": 0
                  }
                ],
                "versichertePersonId": "string",
                "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
                "versicherungsBeginn": "2020-02-24",
                "versicherungsDauerInMonaten": 0
              }
            ]
          },
          "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
          "externeBausparAngebote": [
            {
              "abschlussGebuehr": 0,
              "angebotsHinweisFuerAntragsteller": "string",
              "bausparSumme": 0,
              "einmalzahlung": 0,
              "id": "string",
              "produktAnbieter": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparPhase": {
                "guthabenBeiZuteilung": 0,
                "sparBeitragMonatlich": 0,
                "sparPhaseInJahren": 0
              },
              "tarif": "string",
              "tilgungsPhase": {
                "bausparDarlehenSumme": 0,
                "sollZinsNachZuteilung": 0,
                "tilgungsBeitragMonatlich": 0,
                "tilgungsPhaseInJahren": 0
              },
              "typ": "string",
              "vertragsBeginn": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zuteilungsDatum": "2020-02-24"
            }
          ],
          "finanzbedarf": {
            "anzahlTeilzahlungen": 0,
            "aussenAnlagen": 0,
            "bauNebenkosten": 0,
            "beratungsHonorar": 0,
            "bereitsBeglichen": 0,
            "erschliessung": 0,
            "grunderwerbsteuer": 0,
            "grundstueckBereitsBezahlt": true,
            "grundstuecksKaufpreis": 0,
            "herstellung": 0,
            "kapitalBeschaffung": 0,
            "kapitalWirdBeschafft": true,
            "kaufpreis": 0,
            "maklergebuehr": 0,
            "mobiliar": 0,
            "modernisieren": true,
            "modernisierung": 0,
            "notargebuehr": 0,
            "renovierung": 0,
            "sonstigeKosten": 0,
            "zusaetzlichesKapital": 0
          },
          "finanzierungswunsch": {
            "bausparWuensche": [
              {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              }
            ],
            "darlehensWuensche": [
              {
                "annuitaetenDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "forwardDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "id": "string",
                "kfwDarlehen": {
                  "darlehensBetrag": 0,
                  "kfwEndfaellig": "NEIN",
                  "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
                  "kfwProgramm": "PROGRAMM_124",
                  "laufzeitInJahren": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "tilgungsfreieAnlaufjahre": 0,
                  "zinsBindungInJahren": 0
                },
                "privatDarlehen": {
                  "darlehensBetrag": 0,
                  "laufzeitInMonaten": 0,
                  "provision": 0
                },
                "variablesDarlehen": {
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  }
                },
                "zwischenFinanzierung": {
                  "darlehensBetrag": 0,
                  "detailsZurVerwendung": "string",
                  "maximaleLaufzeitInMonaten": 0,
                  "provision": 0,
                  "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
                }
              }
            ],
            "id": "string"
          },
          "id": "string",
          "nachfinanzierung": true,
          "nachrangigeExterneDarlehen": [
            {
              "darlehensBetrag": 0,
              "darlehensGeber": "string",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "typ": "ARBEITGEBERDARLEHEN",
              "zinsBindung": {
                "endetAm": "2020-02-24",
                "jahre": 0,
                "monate": 0,
                "restschuldNachZinsBindungsEnde": 0
              }
            }
          ],
          "praeferenzen": {
            "bereitstellungsZinsFreieZeit": {
              "darlehenBenoetigtInMonaten": 0,
              "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
              "zusatzlicheKommentare": "string"
            },
            "bestandteileDerFinanzierung": {
              "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
              "zusatzlicheKommentare": "string"
            },
            "hoeheDerRate": {
              "betrag": 0,
              "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
              "zusatzlicheKommentare": "string"
            },
            "laufzeit": {
              "bisZumJahr": "2016",
              "bisZurRenteImJahr": "2016",
              "inJahren": 0,
              "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
              "zusatzlicheKommentare": "string"
            },
            "sondertilgung": {
              "betragEinmalig": 0,
              "betragJaehrlich": 0,
              "praeferenzAuswahl": "JAEHRLICH",
              "zusatzlicheKommentare": "string"
            },
            "tilgungsSatzWechsel": {
              "mindestensBenoetigt": 0,
              "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
              "zusatzlicheKommentare": "string"
            },
            "weiterePraeferenz": "string",
            "zeitlicherRahmen": {
              "finanzierungszusageBis": "2020-02-24",
              "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
              "zusatzlicheKommentare": "string"
            },
            "zinsBindung": {
              "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
              "zinsBindungBisJahren": 0,
              "zinsBindungVonJahren": 0,
              "zinsBindungZwischenJahren": 0,
              "zusatzlicheKommentare": "string"
            }
          },
          "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
        }
      },
      "_links": {
        "self": {
          "href": "string",
          "type": "string"
        }
      }
    }
  ],
  "_links": {
    "next": {
      "href": "string",
      "type": "string"
    },
    "prev": {
      "href": "string",
      "type": "string"
    },
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}
```

<h3 id="getallvorgangsantraege-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Antraege](#schemaantraege)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[Error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[Error](#schemaerror)|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Method Not Allowed|[Error](#schemaerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)|
|502|[Bad Gateway](https://tools.ietf.org/html/rfc7231#section-6.6.3)|Bad Gateway|[Error](#schemaerror)|
|504|[Gateway Time-out](https://tools.ietf.org/html/rfc7231#section-6.6.5)|Gateway Timeout|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### getVorgangsAntraege

<a id="opIdgetVorgangsAntraege"></a>

> Code samples

```shell
## You can also use wget
curl -X GET https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer} \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}`

*Anträge zum Vorgang*

<h3 id="getvorgangsantraege-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|
|antragsNummer|path|integer(int32)|true|antragsNummer|

> Example responses

> 200 Response

```json
{
  "antraege": [
    {
      "angebot": {
        "absicherungen": [
          {
            "abgesicherteRisiken": [
              {
                "abgesichertesRisiko": "TODESFALL",
                "auszahlungsBetrag": 0,
                "auszahlungsTurnus": "EINMALIG",
                "praemienAnteil": 0
              }
            ],
            "gesamtPraemie": 0,
            "praemienZahlungsweise": "EINMALIG",
            "tarifBezeichnung": "string",
            "tarifKennung": "string",
            "versichertePersonId": "string",
            "versicherungsArt": "string",
            "versicherungsNummer": "string",
            "versicherungsZeitraum": {
              "beginn": "2020-02-24",
              "dauerInMonaten": 0,
              "ende": "2020-02-24"
            }
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "angebotsHinweisFuerAntragsteller": "string",
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "gesamtLaufzeitInJahren": 0,
            "id": "string",
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparPhase": {
              "guthabenBeiZuteilung": 0,
              "sparBeitragMonatlich": 0,
              "sparPhaseInJahren": 0
            },
            "tarif": "string",
            "tilgungsPhase": {
              "bausparDarlehenSumme": 0,
              "sollZinsNachZuteilung": 0,
              "tilgungsBeitragMonatlich": 0,
              "tilgungsPhaseInJahren": 0
            },
            "typ": "string",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "beleihungsRechnung": {
          "beleihungsAuslauf": 0,
          "beleihungsWerte": [
            {
              "beleihungsWert": 0,
              "immobilie": {
                "id": "string"
              }
            }
          ],
          "beleihungsWerteSumme": 0,
          "produktAnbieter": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          }
        },
        "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
        "darlehen": [
          {
            "auszahlungsBetrag": 0,
            "auszahlungsDatum": "2020-02-24",
            "auszahlungsKurs": 0,
            "bereitstellung": {
              "bereitstellungsZins": 0,
              "bereitstellungsZinsFreieZeitInMonaten": 0
            },
            "darlehensBetrag": 0,
            "darlehensTyp": "ANNUITAETEN_DARLEHEN",
            "detailsZurVerwendung": "string",
            "effektivZins": 0,
            "effektivZinsRelevanteKosten": {
              "beratungsHonorar": 0,
              "grundbuchKosten": 0,
              "sonstigeKosten": 0,
              "tilgungsErsatzProduktKosten": 0,
              "wohnGebaeudeVersicherungsKosten": 0,
              "zinsabsicherungsKosten": 0,
              "zusatzSicherheitsKosten": 0
            },
            "forwardPeriodeInMonaten": 0,
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "konditionWurdeManuellAngepasst": true,
            "konditionsAnpassungsBegruendung": "string",
            "laufZeitInJahren": 0,
            "laufzeitInMonaten": 0,
            "maximaleLaufzeitInMonaten": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "rateMonatlich": 123.34,
            "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
            "sollZins": 2.05,
            "tilgung": {
              "anfaenglicheTilgung": 0,
              "sonderTilgungJaehrlich": 0,
              "tilgungsBeginnAm": "2020-02-24",
              "tilgungsErsatz": {
                "id": "string",
                "typ": "string"
              }
            },
            "tilgungsFreieAnlaufJahre": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
            "zinsBindung": {
              "endetAm": "2020-02-24",
              "jahre": 0,
              "monate": 0,
              "restschuldNachZinsBindungsEnde": 0
            },
            "zinsZahlungsBeginnAm": "2020-02-24"
          }
        ],
        "erzeugtAm": "2020-02-24T11:55:47Z",
        "kennung": "string",
        "machbarkeitsStatus": "MACHBAR",
        "meldungen": [
          {
            "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
            "kreditEntscheider": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "text": "string"
          }
        ],
        "pruefungsErgebnisse": [
          {
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "weitereAngaben": "string"
          }
        ],
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "ansprechpartner": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "antragsNummer": "string",
      "beratung": {
        "art": "PRAESENZ_GESCHAEFT",
        "hinweisFuerProduktAnbieter": "string",
        "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
      },
      "datenKontext": "TEST_MODUS",
      "dokumente": [
        {
          "art": "string",
          "href": "string",
          "name": "string",
          "titel": "string",
          "type": "string"
        }
      ],
      "kreditSachbearbeiter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "status": {
        "ablehnungsgrund": "FINANZIELLE_SITUATION",
        "antragsteller": "BEANTRAGT",
        "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
        "produktAnbieter": "NICHT_BEARBEITET"
      },
      "vermittler": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "zeitpunktDerAnnahme": "2020-02-24T11:55:47Z",
      "zugrundeliegendeDaten": {
        "bankverbindung": {
          "bic": "string",
          "iban": "string",
          "id": "string",
          "kontoinhaberIds": [
            "string"
          ],
          "kontoinhaberName": "string",
          "kreditinstitut": "string"
        },
        "finanzierungsObjekt": {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "verwendenAls": "ABLOESEN",
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "keinBaulandFlaecheInQm": 0,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        },
        "haushalte": [
          {
            "antragsteller": [
              {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "arbeitserlaubnis": false,
                "arbeitserlaubnisBefristetBis": "2020-02-24",
                "aufenthaltsTitel": "VISUM",
                "aufenthaltsTitelBefristetBis": "2020-02-24",
                "beschaeftigung": {
                  "anzahlGehaelterProJahr": 0,
                  "arbeitgeber": "string",
                  "arbeitgeberInDeutschlandAnsaessig": false,
                  "arbeitgeberLand": {
                    "isoCountryCode": "string",
                    "name": "string"
                  },
                  "art": "ANGESTELLTER",
                  "befristungsStatus": "BEFRISTET",
                  "beruf": "string",
                  "beschaeftigtSeit": "2020-02-24",
                  "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
                  "einkommenNettoJaehrlich": 0,
                  "einkommenNettoMonatlich": 0,
                  "firma": "string",
                  "inProbezeit": false,
                  "situationNachRenteneintritt": {
                    "gesetzlicheRenteMonatlich": 0,
                    "privateRenteMonatlich": 0,
                    "rentenBeginn": "2020-02-24",
                    "sonstigesEinkommenMonatlich": 0
                  },
                  "taetigkeit": "ALTENPFLEGER"
                },
                "bruttoVorjahresEinkommen": 0,
                "email": "max.mustermann@test.de",
                "externeAntragstellerId": "string",
                "familienstand": "GESCHIEDEN",
                "geburtsdatum": "2020-02-24",
                "geburtsort": "string",
                "guetertrennungVereinbartWennVerheiratet": false,
                "id": "string",
                "inDeutschlandSeit": "2020-02-24",
                "legitimationsDaten": {
                  "ausstellendeBehoerde": "string",
                  "ausstellungsdatum": "2020-02-24",
                  "ausweisArt": "PERSONALAUSWEIS",
                  "ausweisArtBeiAndererAusweis": "string",
                  "ausweisNummer": "string"
                },
                "nachname": "string",
                "schufaErgebnis": {
                  "antragstellerUnbekannt": false,
                  "inManuellerNachbehandlung": false,
                  "score": "string"
                },
                "staatsangehoerigkeit": {
                  "isoCountryCode": "string",
                  "name": "string"
                },
                "steuerId": "string",
                "telefonnummer": "string",
                "telefonnummerVorwahl": "string",
                "titel": [
                  "DOKTOR"
                ],
                "titelDoktor": true,
                "titelProfessor": true,
                "vorAnschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "vorname": "string",
                "weitereKontaktMoeglichkeiten": "string",
                "wohnhaftSeit": "2020-02-24"
              }
            ],
            "anzahlErwachseneImHaushalt": 0,
            "anzahlKinderNichtImHaushalt": 0,
            "bestehendeImmobilien": [
              {
                "adresse": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "autostellplaetze": [
                  {
                    "mieteinnahmenMonatlich": 0,
                    "typ": "STELLPLATZ"
                  }
                ],
                "bestehendeDarlehen": [
                  {
                    "abzuloesendeRestschuld": 0,
                    "aktuelleRestschuldWennNichtAbzuloesen": 0,
                    "darlehensArt": "BAUSPARDARLEHEN",
                    "darlehensBetrag": 0,
                    "darlehensGeber": {},
                    "darlehensKontonummer": "string",
                    "eingetrageneGrundschuld": 0,
                    "grundschuldArt": "BRIEF_GRUNDSCHULD",
                    "id": "string",
                    "laufzeitEnde": "2020-02-24",
                    "rateMonatlich": 0,
                    "sollZins": 0,
                    "sondertilgungZumZinsBindungsEnde": 0,
                    "zinsBindungEndetAm": "2020-02-24"
                  }
                ],
                "bewirtschaftungsKostenJaehrlich": 0,
                "bodenRichtwert": 0,
                "bundesland": "BADEN_WUERTTEMBERG",
                "effektivZinsErhoehendeKosten": {
                  "anpassen": true,
                  "grundbuchEintragungsKostenEinmalig": 0,
                  "sonstigeKostenBezeichnung": "string",
                  "sonstigeKostenEinmalig": 0,
                  "wohnGebaeudeVersicherungsKostenJaehrlich": 0
                },
                "erbbaurecht": {
                  "erbbaurecht": true,
                  "erbbauzinsJaehrlich": 0,
                  "grundstuecksEigentuemer": "ANDERE",
                  "laufzeitBisJahr": "string"
                },
                "gebaeude": {
                  "anzahlDerGewerbeeinheiten": 0,
                  "anzahlDerWohneinheitenImGebaeude": 0,
                  "anzahlVollgeschosse": 0,
                  "aufbauFinanzierung": true,
                  "aufzugVorhanden": true,
                  "ausstattung": "EINFACH",
                  "baujahr": "2016",
                  "bauweise": "FACHWERK_MIT_STROH_LEHM",
                  "bezeichnungWohneinheit": "string",
                  "dachgeschossAusbau": "FLACHDACH",
                  "einliegerwohnungVorhanden": true,
                  "geschossLage": "UNTERGESCHOSS",
                  "gewerbeflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "hausAnordnung": "FREISTEHEND",
                  "hausTyp": "DOPPELHAUSHAELFTE",
                  "istFertighaus": true,
                  "kellerausbau": "AUSGEBAUT",
                  "kubatur": 0,
                  "miteigentumsAnteil": {
                    "anteil": 0,
                    "gesamt": 0
                  },
                  "modernisierungsAngaben": {
                    "badWc": true,
                    "bodenWandTreppe": true,
                    "dach": true,
                    "fenster": true,
                    "heizungZentral": true,
                    "modernisierungsGrad": "GERING",
                    "modernisierungsJahr": "string",
                    "raumaufteilung": true,
                    "stromAbwasserHeizkoerper": true,
                    "waermedaemmung": true,
                    "wurdeModernisiert": true
                  },
                  "unterkellerung": "NICHT_UNTERKELLERT",
                  "wohnflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "zustand": "SEHR_GUT"
                },
                "grundbuchAngabe": {
                  "anmerkungen": "string",
                  "bandUndBlatt": "string",
                  "flurstuecke": [
                    {}
                  ],
                  "ort": "string",
                  "rechteInAbteilung2": {
                    "beschreibung": "string",
                    "betrag": 0,
                    "vorhanden": true
                  }
                },
                "grundstueck": {
                  "groesse": 0,
                  "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
                },
                "id": "string",
                "immobilienEinsatz": "KEIN_EINSATZ",
                "keinBaulandFlaecheInQm": 0,
                "keineBestehendenDarlehenVorhanden": true,
                "marktueblicherKaufpreisProQm": 0,
                "marktwert": 0,
                "maximalEinzusetzenderBetragWennVerkauf": 0,
                "objektArt": "GRUNDSTUECK",
                "vergleichsmieteFuerGewerbeflaecheProQm": 0,
                "vergleichsmieteFuerWohnflaecheProQm": 0,
                "verkehrswert": 0,
                "vorlaeufigerVerkehrswert": 0,
                "wohnlage": "GEHOBEN"
              }
            ],
            "id": "string",
            "kfzAnzahl": 0,
            "kinder": [
              {
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kindergeldWirdBezogen": true,
                "name": "string",
                "unterhaltsEinnahmenBetragMonatlich": 0
              }
            ],
            "lebenshaltungsKostenMonatlich": 0,
            "obligo": {
              "vermoegenOderVerbindlichkeiten": [
                {
                  "aktuellerWert": 0,
                  "anrechnungFuerBlankoAnteil": 0,
                  "bezeichner": "string",
                  "kontonummer": "string",
                  "vermoegensTyp": "VERMOEGEN"
                }
              ]
            },
            "positionen": {
              "bankUndSparguthaben": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zinsertragJaehrlich": 0,
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "bausparvertraege": [
                {
                  "abschlussGebuehr": 0,
                  "aktuellerWert": 0,
                  "bausparSumme": 0,
                  "einmalzahlung": 0,
                  "ertrag": 0,
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "produktAnbieter": {
                    "anrede": "FRAU",
                    "anschrift": {},
                    "email": "string",
                    "externePartnerId": "string",
                    "externerKreditSachbearbeiterId": "string",
                    "fax": "string",
                    "firmenNameZusatz": "string",
                    "firmierung": "string",
                    "geburtsdatum": "2020-02-24",
                    "id": "string",
                    "kreditsachbearbeiter": true,
                    "mobilTelefon": "string",
                    "nachname": "string",
                    "partnerId": "string",
                    "produktAnbieterId": "string",
                    "telefonnummer": "string",
                    "vertriebsOrganisation": {},
                    "vorname": "string",
                    "webseite": "string"
                  },
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeitragMonatlich": 0,
                  "tarif": "string",
                  "typ": "string",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "vertragsBeginn": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0,
                  "zuteilungsDatum": "2020-02-24"
                }
              ],
              "ehegattenUnterhalt": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "einkuenfteAusNebentaetigkeit": [
                {
                  "beginnDerNebentaetigkeit": "2020-02-24",
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "kindergeld": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "lebensUndRentenVersicherungen": [
                {
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "praemieMonatlich": 0,
                  "rueckkaufsWertAktuell": 0,
                  "tarif": "string",
                  "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "versicherungsGesellschaft": "string",
                  "versicherungsSumme": 0,
                  "vertragsBeginn": "2020-02-24",
                  "vertragsEnde": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "mietAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "entfallenMitFinanzierung": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateDarlehen": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateKrankenversicherung": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "ratenkredite": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeEinnahmen": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVerbindlichkeiten": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVermoegen": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "sparplaene": [
                {
                  "aktuellerWert": 0,
                  "beitragMonatlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "unbefristeteZusatzRenten": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "unterhaltsVerpflichtungen": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "variableEinkuenfte": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "versicherungsAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "wertpapiere": [
                {
                  "aktuellerWert": 0,
                  "dividendenJaehrlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ]
            }
          }
        ],
        "vorhaben": {
          "absicherungswunsch": {
            "id": "string",
            "versicherungsWuensche": [
              {
                "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
                "id": "string",
                "praemienZahlungsweise": "EINMALIG",
                "risikoAbsicherungsWuensche": [
                  {
                    "abzusicherndesRisiko": "TODESFALL",
                    "versicherteRate": 0,
                    "versicherungsSumme": 0
                  }
                ],
                "versichertePersonId": "string",
                "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
                "versicherungsBeginn": "2020-02-24",
                "versicherungsDauerInMonaten": 0
              }
            ]
          },
          "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
          "externeBausparAngebote": [
            {
              "abschlussGebuehr": 0,
              "angebotsHinweisFuerAntragsteller": "string",
              "bausparSumme": 0,
              "einmalzahlung": 0,
              "id": "string",
              "produktAnbieter": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparPhase": {
                "guthabenBeiZuteilung": 0,
                "sparBeitragMonatlich": 0,
                "sparPhaseInJahren": 0
              },
              "tarif": "string",
              "tilgungsPhase": {
                "bausparDarlehenSumme": 0,
                "sollZinsNachZuteilung": 0,
                "tilgungsBeitragMonatlich": 0,
                "tilgungsPhaseInJahren": 0
              },
              "typ": "string",
              "vertragsBeginn": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zuteilungsDatum": "2020-02-24"
            }
          ],
          "finanzbedarf": {
            "anzahlTeilzahlungen": 0,
            "aussenAnlagen": 0,
            "bauNebenkosten": 0,
            "beratungsHonorar": 0,
            "bereitsBeglichen": 0,
            "erschliessung": 0,
            "grunderwerbsteuer": 0,
            "grundstueckBereitsBezahlt": true,
            "grundstuecksKaufpreis": 0,
            "herstellung": 0,
            "kapitalBeschaffung": 0,
            "kapitalWirdBeschafft": true,
            "kaufpreis": 0,
            "maklergebuehr": 0,
            "mobiliar": 0,
            "modernisieren": true,
            "modernisierung": 0,
            "notargebuehr": 0,
            "renovierung": 0,
            "sonstigeKosten": 0,
            "zusaetzlichesKapital": 0
          },
          "finanzierungswunsch": {
            "bausparWuensche": [
              {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              }
            ],
            "darlehensWuensche": [
              {
                "annuitaetenDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "forwardDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "id": "string",
                "kfwDarlehen": {
                  "darlehensBetrag": 0,
                  "kfwEndfaellig": "NEIN",
                  "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
                  "kfwProgramm": "PROGRAMM_124",
                  "laufzeitInJahren": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "tilgungsfreieAnlaufjahre": 0,
                  "zinsBindungInJahren": 0
                },
                "privatDarlehen": {
                  "darlehensBetrag": 0,
                  "laufzeitInMonaten": 0,
                  "provision": 0
                },
                "variablesDarlehen": {
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  }
                },
                "zwischenFinanzierung": {
                  "darlehensBetrag": 0,
                  "detailsZurVerwendung": "string",
                  "maximaleLaufzeitInMonaten": 0,
                  "provision": 0,
                  "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
                }
              }
            ],
            "id": "string"
          },
          "id": "string",
          "nachfinanzierung": true,
          "nachrangigeExterneDarlehen": [
            {
              "darlehensBetrag": 0,
              "darlehensGeber": "string",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "typ": "ARBEITGEBERDARLEHEN",
              "zinsBindung": {
                "endetAm": "2020-02-24",
                "jahre": 0,
                "monate": 0,
                "restschuldNachZinsBindungsEnde": 0
              }
            }
          ],
          "praeferenzen": {
            "bereitstellungsZinsFreieZeit": {
              "darlehenBenoetigtInMonaten": 0,
              "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
              "zusatzlicheKommentare": "string"
            },
            "bestandteileDerFinanzierung": {
              "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
              "zusatzlicheKommentare": "string"
            },
            "hoeheDerRate": {
              "betrag": 0,
              "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
              "zusatzlicheKommentare": "string"
            },
            "laufzeit": {
              "bisZumJahr": "2016",
              "bisZurRenteImJahr": "2016",
              "inJahren": 0,
              "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
              "zusatzlicheKommentare": "string"
            },
            "sondertilgung": {
              "betragEinmalig": 0,
              "betragJaehrlich": 0,
              "praeferenzAuswahl": "JAEHRLICH",
              "zusatzlicheKommentare": "string"
            },
            "tilgungsSatzWechsel": {
              "mindestensBenoetigt": 0,
              "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
              "zusatzlicheKommentare": "string"
            },
            "weiterePraeferenz": "string",
            "zeitlicherRahmen": {
              "finanzierungszusageBis": "2020-02-24",
              "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
              "zusatzlicheKommentare": "string"
            },
            "zinsBindung": {
              "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
              "zinsBindungBisJahren": 0,
              "zinsBindungVonJahren": 0,
              "zinsBindungZwischenJahren": 0,
              "zusatzlicheKommentare": "string"
            }
          },
          "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
        }
      },
      "_links": {
        "self": {
          "href": "string",
          "type": "string"
        }
      }
    }
  ],
  "_links": {
    "next": {
      "href": "string",
      "type": "string"
    },
    "prev": {
      "href": "string",
      "type": "string"
    },
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}
```

<h3 id="getvorgangsantraege-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Antraege](#schemaantraege)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[Error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[Error](#schemaerror)|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Method Not Allowed|[Error](#schemaerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)|
|502|[Bad Gateway](https://tools.ietf.org/html/rfc7231#section-6.6.3)|Bad Gateway|[Error](#schemaerror)|
|504|[Gateway Time-out](https://tools.ietf.org/html/rfc7231#section-6.6.5)|Gateway Timeout|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### getAntrag

<a id="opIdgetAntrag"></a>

> Code samples

```shell
## You can also use wget
curl -X GET https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}/{teilantragsNummer} \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}/{teilantragsNummer}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}/{teilantragsNummer}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}/{teilantragsNummer}`

*Ein spezifischer Antrag des Vorgangs*

<h3 id="getantrag-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|
|antragsNummer|path|integer(int32)|true|antragsNummer|
|teilantragsNummer|path|integer(int32)|true|teilantragsNummer|

> Example responses

> 200 Response

```json
{
  "angebot": {
    "absicherungen": [
      {
        "abgesicherteRisiken": [
          {
            "abgesichertesRisiko": "TODESFALL",
            "auszahlungsBetrag": 0,
            "auszahlungsTurnus": "EINMALIG",
            "praemienAnteil": 0
          }
        ],
        "gesamtPraemie": 0,
        "praemienZahlungsweise": "EINMALIG",
        "tarifBezeichnung": "string",
        "tarifKennung": "string",
        "versichertePersonId": "string",
        "versicherungsArt": "string",
        "versicherungsNummer": "string",
        "versicherungsZeitraum": {
          "beginn": "2020-02-24",
          "dauerInMonaten": 0,
          "ende": "2020-02-24"
        }
      }
    ],
    "bausparvertraege": [
      {
        "abschlussGebuehr": 0,
        "angebotsHinweisFuerAntragsteller": "string",
        "bausparSumme": 0,
        "einmalzahlung": 0,
        "gesamtLaufzeitInJahren": 0,
        "id": "string",
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparPhase": {
          "guthabenBeiZuteilung": 0,
          "sparBeitragMonatlich": 0,
          "sparPhaseInJahren": 0
        },
        "tarif": "string",
        "tilgungsPhase": {
          "bausparDarlehenSumme": 0,
          "sollZinsNachZuteilung": 0,
          "tilgungsBeitragMonatlich": 0,
          "tilgungsPhaseInJahren": 0
        },
        "typ": "string",
        "vertragsBeginn": "2020-02-24",
        "vertragsNummer": "string",
        "verwaltungsgebuehrenJaehrlich": 0,
        "zuteilungsDatum": "2020-02-24"
      }
    ],
    "beleihungsRechnung": {
      "beleihungsAuslauf": 0,
      "beleihungsWerte": [
        {
          "beleihungsWert": 0,
          "immobilie": {
            "id": "string"
          }
        }
      ],
      "beleihungsWerteSumme": 0,
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      }
    },
    "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
    "darlehen": [
      {
        "auszahlungsBetrag": 0,
        "auszahlungsDatum": "2020-02-24",
        "auszahlungsKurs": 0,
        "bereitstellung": {
          "bereitstellungsZins": 0,
          "bereitstellungsZinsFreieZeitInMonaten": 0
        },
        "darlehensBetrag": 0,
        "darlehensTyp": "ANNUITAETEN_DARLEHEN",
        "detailsZurVerwendung": "string",
        "effektivZins": 0,
        "effektivZinsRelevanteKosten": {
          "beratungsHonorar": 0,
          "grundbuchKosten": 0,
          "sonstigeKosten": 0,
          "tilgungsErsatzProduktKosten": 0,
          "wohnGebaeudeVersicherungsKosten": 0,
          "zinsabsicherungsKosten": 0,
          "zusatzSicherheitsKosten": 0
        },
        "forwardPeriodeInMonaten": 0,
        "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
        "kfwProgramm": "PROGRAMM_124",
        "konditionWurdeManuellAngepasst": true,
        "konditionsAnpassungsBegruendung": "string",
        "laufZeitInJahren": 0,
        "laufzeitInMonaten": 0,
        "maximaleLaufzeitInMonaten": 0,
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "rateMonatlich": 123.34,
        "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
        "sollZins": 2.05,
        "tilgung": {
          "anfaenglicheTilgung": 0,
          "sonderTilgungJaehrlich": 0,
          "tilgungsBeginnAm": "2020-02-24",
          "tilgungsErsatz": {
            "id": "string",
            "typ": "string"
          }
        },
        "tilgungsFreieAnlaufJahre": 0,
        "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
        "zinsBindung": {
          "endetAm": "2020-02-24",
          "jahre": 0,
          "monate": 0,
          "restschuldNachZinsBindungsEnde": 0
        },
        "zinsZahlungsBeginnAm": "2020-02-24"
      }
    ],
    "erzeugtAm": "2020-02-24T11:55:47Z",
    "kennung": "string",
    "machbarkeitsStatus": "MACHBAR",
    "meldungen": [
      {
        "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
        "kreditEntscheider": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "text": "string"
      }
    ],
    "pruefungsErgebnisse": [
      {
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "weitereAngaben": "string"
      }
    ],
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "ansprechpartner": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "antragsNummer": "string",
  "beratung": {
    "art": "PRAESENZ_GESCHAEFT",
    "hinweisFuerProduktAnbieter": "string",
    "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
  },
  "datenKontext": "TEST_MODUS",
  "dokumente": [
    {
      "art": "string",
      "href": "string",
      "name": "string",
      "titel": "string",
      "type": "string"
    }
  ],
  "kreditSachbearbeiter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "status": {
    "ablehnungsgrund": "FINANZIELLE_SITUATION",
    "antragsteller": "BEANTRAGT",
    "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
    "produktAnbieter": "NICHT_BEARBEITET"
  },
  "vermittler": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "zeitpunktDerAnnahme": "2020-02-24T11:55:47Z",
  "zugrundeliegendeDaten": {
    "bankverbindung": {
      "bic": "string",
      "iban": "string",
      "id": "string",
      "kontoinhaberIds": [
        "string"
      ],
      "kontoinhaberName": "string",
      "kreditinstitut": "string"
    },
    "finanzierungsObjekt": {
      "adresse": {
        "hausnummer": "string",
        "ort": "string",
        "postleitzahl": "string",
        "strasse": "string"
      },
      "autostellplaetze": [
        {
          "mieteinnahmenMonatlich": 0,
          "typ": "STELLPLATZ"
        }
      ],
      "bestehendeDarlehen": [
        {
          "abzuloesendeRestschuld": 0,
          "aktuelleRestschuldWennNichtAbzuloesen": 0,
          "darlehensArt": "BAUSPARDARLEHEN",
          "darlehensBetrag": 0,
          "darlehensGeber": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          },
          "darlehensKontonummer": "string",
          "eingetrageneGrundschuld": 0,
          "grundschuldArt": "BRIEF_GRUNDSCHULD",
          "id": "string",
          "laufzeitEnde": "2020-02-24",
          "rateMonatlich": 0,
          "sollZins": 0,
          "sondertilgungZumZinsBindungsEnde": 0,
          "verwendenAls": "ABLOESEN",
          "zinsBindungEndetAm": "2020-02-24"
        }
      ],
      "bewirtschaftungsKostenJaehrlich": 0,
      "bodenRichtwert": 0,
      "bundesland": "BADEN_WUERTTEMBERG",
      "effektivZinsErhoehendeKosten": {
        "anpassen": true,
        "grundbuchEintragungsKostenEinmalig": 0,
        "sonstigeKostenBezeichnung": "string",
        "sonstigeKostenEinmalig": 0,
        "wohnGebaeudeVersicherungsKostenJaehrlich": 0
      },
      "erbbaurecht": {
        "erbbaurecht": true,
        "erbbauzinsJaehrlich": 0,
        "grundstuecksEigentuemer": "ANDERE",
        "laufzeitBisJahr": "string"
      },
      "gebaeude": {
        "anzahlDerGewerbeeinheiten": 0,
        "anzahlDerWohneinheitenImGebaeude": 0,
        "anzahlVollgeschosse": 0,
        "aufbauFinanzierung": true,
        "aufzugVorhanden": true,
        "ausstattung": "EINFACH",
        "baujahr": "2016",
        "bauweise": "FACHWERK_MIT_STROH_LEHM",
        "bezeichnungWohneinheit": "string",
        "dachgeschossAusbau": "FLACHDACH",
        "einliegerwohnungVorhanden": true,
        "geschossLage": "UNTERGESCHOSS",
        "gewerbeflaeche": {
          "gesamtGroesse": 0,
          "vermietungsInformationen": {
            "mieteinnahmenNettoKaltMonatlich": 0,
            "nutzungsArt": "EIGENGENUTZT",
            "vermieteteFlaeche": 0
          }
        },
        "hausAnordnung": "FREISTEHEND",
        "hausTyp": "DOPPELHAUSHAELFTE",
        "istFertighaus": true,
        "kellerausbau": "AUSGEBAUT",
        "kubatur": 0,
        "miteigentumsAnteil": {
          "anteil": 0,
          "gesamt": 0
        },
        "modernisierungsAngaben": {
          "badWc": true,
          "bodenWandTreppe": true,
          "dach": true,
          "fenster": true,
          "heizungZentral": true,
          "modernisierungsGrad": "GERING",
          "modernisierungsJahr": "string",
          "raumaufteilung": true,
          "stromAbwasserHeizkoerper": true,
          "waermedaemmung": true,
          "wurdeModernisiert": true
        },
        "unterkellerung": "NICHT_UNTERKELLERT",
        "wohnflaeche": {
          "gesamtGroesse": 0,
          "vermietungsInformationen": {
            "mieteinnahmenNettoKaltMonatlich": 0,
            "nutzungsArt": "EIGENGENUTZT",
            "vermieteteFlaeche": 0
          }
        },
        "zustand": "SEHR_GUT"
      },
      "grundbuchAngabe": {
        "anmerkungen": "string",
        "bandUndBlatt": "string",
        "flurstuecke": [
          {
            "anteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "flur": "string",
            "flurstuecksNummer": "string",
            "groesse": 0
          }
        ],
        "ort": "string",
        "rechteInAbteilung2": {
          "beschreibung": "string",
          "betrag": 0,
          "vorhanden": true
        }
      },
      "grundstueck": {
        "groesse": 0,
        "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
      },
      "id": "string",
      "keinBaulandFlaecheInQm": 0,
      "marktueblicherKaufpreisProQm": 0,
      "marktwert": 0,
      "objektArt": "GRUNDSTUECK",
      "vergleichsmieteFuerGewerbeflaecheProQm": 0,
      "vergleichsmieteFuerWohnflaecheProQm": 0,
      "verkehrswert": 0,
      "vorlaeufigerVerkehrswert": 0,
      "wohnlage": "GEHOBEN"
    },
    "haushalte": [
      {
        "antragsteller": [
          {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "arbeitserlaubnis": false,
            "arbeitserlaubnisBefristetBis": "2020-02-24",
            "aufenthaltsTitel": "VISUM",
            "aufenthaltsTitelBefristetBis": "2020-02-24",
            "beschaeftigung": {
              "anzahlGehaelterProJahr": 0,
              "arbeitgeber": "string",
              "arbeitgeberInDeutschlandAnsaessig": false,
              "arbeitgeberLand": {
                "isoCountryCode": "string",
                "name": "string"
              },
              "art": "ANGESTELLTER",
              "befristungsStatus": "BEFRISTET",
              "beruf": "string",
              "beschaeftigtSeit": "2020-02-24",
              "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
              "einkommenNettoJaehrlich": 0,
              "einkommenNettoMonatlich": 0,
              "firma": "string",
              "inProbezeit": false,
              "situationNachRenteneintritt": {
                "gesetzlicheRenteMonatlich": 0,
                "privateRenteMonatlich": 0,
                "rentenBeginn": "2020-02-24",
                "sonstigesEinkommenMonatlich": 0
              },
              "taetigkeit": "ALTENPFLEGER"
            },
            "bruttoVorjahresEinkommen": 0,
            "email": "max.mustermann@test.de",
            "externeAntragstellerId": "string",
            "familienstand": "GESCHIEDEN",
            "geburtsdatum": "2020-02-24",
            "geburtsort": "string",
            "guetertrennungVereinbartWennVerheiratet": false,
            "id": "string",
            "inDeutschlandSeit": "2020-02-24",
            "legitimationsDaten": {
              "ausstellendeBehoerde": "string",
              "ausstellungsdatum": "2020-02-24",
              "ausweisArt": "PERSONALAUSWEIS",
              "ausweisArtBeiAndererAusweis": "string",
              "ausweisNummer": "string"
            },
            "nachname": "string",
            "schufaErgebnis": {
              "antragstellerUnbekannt": false,
              "inManuellerNachbehandlung": false,
              "score": "string"
            },
            "staatsangehoerigkeit": {
              "isoCountryCode": "string",
              "name": "string"
            },
            "steuerId": "string",
            "telefonnummer": "string",
            "telefonnummerVorwahl": "string",
            "titel": [
              "DOKTOR"
            ],
            "titelDoktor": true,
            "titelProfessor": true,
            "vorAnschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "vorname": "string",
            "weitereKontaktMoeglichkeiten": "string",
            "wohnhaftSeit": "2020-02-24"
          }
        ],
        "anzahlErwachseneImHaushalt": 0,
        "anzahlKinderNichtImHaushalt": 0,
        "bestehendeImmobilien": [
          {
            "adresse": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "autostellplaetze": [
              {
                "mieteinnahmenMonatlich": 0,
                "typ": "STELLPLATZ"
              }
            ],
            "bestehendeDarlehen": [
              {
                "abzuloesendeRestschuld": 0,
                "aktuelleRestschuldWennNichtAbzuloesen": 0,
                "darlehensArt": "BAUSPARDARLEHEN",
                "darlehensBetrag": 0,
                "darlehensGeber": {
                  "anrede": "FRAU",
                  "anschrift": {
                    "hausnummer": "string",
                    "ort": "string",
                    "postleitzahl": "string",
                    "strasse": "string"
                  },
                  "email": "string",
                  "externePartnerId": "string",
                  "externerKreditSachbearbeiterId": "string",
                  "fax": "string",
                  "firmenNameZusatz": "string",
                  "firmierung": "string",
                  "geburtsdatum": "2020-02-24",
                  "id": "string",
                  "kreditsachbearbeiter": true,
                  "mobilTelefon": "string",
                  "nachname": "string",
                  "partnerId": "string",
                  "produktAnbieterId": "string",
                  "telefonnummer": "string",
                  "vertriebsOrganisation": {
                    "firma": "string",
                    "name": "string",
                    "vertriebsOrganisationsId": "string"
                  },
                  "vorname": "string",
                  "webseite": "string"
                },
                "darlehensKontonummer": "string",
                "eingetrageneGrundschuld": 0,
                "grundschuldArt": "BRIEF_GRUNDSCHULD",
                "id": "string",
                "laufzeitEnde": "2020-02-24",
                "rateMonatlich": 0,
                "sollZins": 0,
                "sondertilgungZumZinsBindungsEnde": 0,
                "zinsBindungEndetAm": "2020-02-24"
              }
            ],
            "bewirtschaftungsKostenJaehrlich": 0,
            "bodenRichtwert": 0,
            "bundesland": "BADEN_WUERTTEMBERG",
            "effektivZinsErhoehendeKosten": {
              "anpassen": true,
              "grundbuchEintragungsKostenEinmalig": 0,
              "sonstigeKostenBezeichnung": "string",
              "sonstigeKostenEinmalig": 0,
              "wohnGebaeudeVersicherungsKostenJaehrlich": 0
            },
            "erbbaurecht": {
              "erbbaurecht": true,
              "erbbauzinsJaehrlich": 0,
              "grundstuecksEigentuemer": "ANDERE",
              "laufzeitBisJahr": "string"
            },
            "gebaeude": {
              "anzahlDerGewerbeeinheiten": 0,
              "anzahlDerWohneinheitenImGebaeude": 0,
              "anzahlVollgeschosse": 0,
              "aufbauFinanzierung": true,
              "aufzugVorhanden": true,
              "ausstattung": "EINFACH",
              "baujahr": "2016",
              "bauweise": "FACHWERK_MIT_STROH_LEHM",
              "bezeichnungWohneinheit": "string",
              "dachgeschossAusbau": "FLACHDACH",
              "einliegerwohnungVorhanden": true,
              "geschossLage": "UNTERGESCHOSS",
              "gewerbeflaeche": {
                "gesamtGroesse": 0,
                "vermietungsInformationen": {
                  "mieteinnahmenNettoKaltMonatlich": 0,
                  "nutzungsArt": "EIGENGENUTZT",
                  "vermieteteFlaeche": 0
                }
              },
              "hausAnordnung": "FREISTEHEND",
              "hausTyp": "DOPPELHAUSHAELFTE",
              "istFertighaus": true,
              "kellerausbau": "AUSGEBAUT",
              "kubatur": 0,
              "miteigentumsAnteil": {
                "anteil": 0,
                "gesamt": 0
              },
              "modernisierungsAngaben": {
                "badWc": true,
                "bodenWandTreppe": true,
                "dach": true,
                "fenster": true,
                "heizungZentral": true,
                "modernisierungsGrad": "GERING",
                "modernisierungsJahr": "string",
                "raumaufteilung": true,
                "stromAbwasserHeizkoerper": true,
                "waermedaemmung": true,
                "wurdeModernisiert": true
              },
              "unterkellerung": "NICHT_UNTERKELLERT",
              "wohnflaeche": {
                "gesamtGroesse": 0,
                "vermietungsInformationen": {
                  "mieteinnahmenNettoKaltMonatlich": 0,
                  "nutzungsArt": "EIGENGENUTZT",
                  "vermieteteFlaeche": 0
                }
              },
              "zustand": "SEHR_GUT"
            },
            "grundbuchAngabe": {
              "anmerkungen": "string",
              "bandUndBlatt": "string",
              "flurstuecke": [
                {
                  "anteil": {
                    "anteil": 0,
                    "gesamt": 0
                  },
                  "flur": "string",
                  "flurstuecksNummer": "string",
                  "groesse": 0
                }
              ],
              "ort": "string",
              "rechteInAbteilung2": {
                "beschreibung": "string",
                "betrag": 0,
                "vorhanden": true
              }
            },
            "grundstueck": {
              "groesse": 0,
              "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
            },
            "id": "string",
            "immobilienEinsatz": "KEIN_EINSATZ",
            "keinBaulandFlaecheInQm": 0,
            "keineBestehendenDarlehenVorhanden": true,
            "marktueblicherKaufpreisProQm": 0,
            "marktwert": 0,
            "maximalEinzusetzenderBetragWennVerkauf": 0,
            "objektArt": "GRUNDSTUECK",
            "vergleichsmieteFuerGewerbeflaecheProQm": 0,
            "vergleichsmieteFuerWohnflaecheProQm": 0,
            "verkehrswert": 0,
            "vorlaeufigerVerkehrswert": 0,
            "wohnlage": "GEHOBEN"
          }
        ],
        "id": "string",
        "kfzAnzahl": 0,
        "kinder": [
          {
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kindergeldWirdBezogen": true,
            "name": "string",
            "unterhaltsEinnahmenBetragMonatlich": 0
          }
        ],
        "lebenshaltungsKostenMonatlich": 0,
        "obligo": {
          "vermoegenOderVerbindlichkeiten": [
            {
              "aktuellerWert": 0,
              "anrechnungFuerBlankoAnteil": 0,
              "bezeichner": "string",
              "kontonummer": "string",
              "vermoegensTyp": "VERMOEGEN"
            }
          ]
        },
        "positionen": {
          "bankUndSparguthaben": [
            {
              "aktuellerWert": 0,
              "ertrag": 0,
              "maximalAufzuloesenderWert": 0,
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "zahlungsTyp": "EINNAHME",
              "zinsertragJaehrlich": 0,
              "zukuenftigeEinnahmen": 0
            }
          ],
          "bausparvertraege": [
            {
              "abschlussGebuehr": 0,
              "aktuellerWert": 0,
              "bausparSumme": 0,
              "einmalzahlung": 0,
              "ertrag": 0,
              "id": "string",
              "maximalAufzuloesenderBetrag": 0,
              "produktAnbieter": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparBeitragMonatlich": 0,
              "tarif": "string",
              "typ": "string",
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "vertragsBeginn": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zahlungsTyp": "EINNAHME",
              "zukuenftigeEinnahmen": 0,
              "zuteilungsDatum": "2020-02-24"
            }
          ],
          "ehegattenUnterhalt": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "einkuenfteAusNebentaetigkeit": [
            {
              "beginnDerNebentaetigkeit": "2020-02-24",
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "kindergeld": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "lebensUndRentenVersicherungen": [
            {
              "id": "string",
              "maximalAufzuloesenderBetrag": 0,
              "praemieMonatlich": 0,
              "rueckkaufsWertAktuell": 0,
              "tarif": "string",
              "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "versicherungsGesellschaft": "string",
              "versicherungsSumme": 0,
              "vertragsBeginn": "2020-02-24",
              "vertragsEnde": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "mietAusgaben": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "entfallenMitFinanzierung": true,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "privateDarlehen": [
            {
              "glaeubiger": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "restschuld": 0,
              "vermoegensTyp": "VERMOEGEN",
              "wirdAbgeloest": true,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "privateKrankenversicherung": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "ratenkredite": [
            {
              "glaeubiger": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "restschuld": 0,
              "vermoegensTyp": "VERMOEGEN",
              "wirdAbgeloest": true,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "sonstigeAusgaben": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "sonstigeEinnahmen": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "sonstigeVerbindlichkeiten": [
            {
              "glaeubiger": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "restschuld": 0,
              "vermoegensTyp": "VERMOEGEN",
              "wirdAbgeloest": true,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "sonstigeVermoegen": [
            {
              "aktuellerWert": 0,
              "ertrag": 0,
              "maximalAufzuloesenderWert": 0,
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "zukuenftigeEinnahmen": 0
            }
          ],
          "sparplaene": [
            {
              "aktuellerWert": 0,
              "beitragMonatlich": 0,
              "ertrag": 0,
              "maximalAufzuloesenderWert": 0,
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "zahlungsTyp": "EINNAHME",
              "zukuenftigeEinnahmen": 0
            }
          ],
          "unbefristeteZusatzRenten": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "unterhaltsVerpflichtungen": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "variableEinkuenfte": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "versicherungsAusgaben": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "wertpapiere": [
            {
              "aktuellerWert": 0,
              "dividendenJaehrlich": 0,
              "ertrag": 0,
              "maximalAufzuloesenderWert": 0,
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "zahlungsTyp": "EINNAHME",
              "zukuenftigeEinnahmen": 0
            }
          ]
        }
      }
    ],
    "vorhaben": {
      "absicherungswunsch": {
        "id": "string",
        "versicherungsWuensche": [
          {
            "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
            "id": "string",
            "praemienZahlungsweise": "EINMALIG",
            "risikoAbsicherungsWuensche": [
              {
                "abzusicherndesRisiko": "TODESFALL",
                "versicherteRate": 0,
                "versicherungsSumme": 0
              }
            ],
            "versichertePersonId": "string",
            "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
            "versicherungsBeginn": "2020-02-24",
            "versicherungsDauerInMonaten": 0
          }
        ]
      },
      "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
      "externeBausparAngebote": [
        {
          "abschlussGebuehr": 0,
          "angebotsHinweisFuerAntragsteller": "string",
          "bausparSumme": 0,
          "einmalzahlung": 0,
          "id": "string",
          "produktAnbieter": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          },
          "sonderZahlungen": [
            {
              "anzahl": 0,
              "betrag": 0,
              "termin": "2020-02-24",
              "zahlweise": "EINMALIG"
            }
          ],
          "sparPhase": {
            "guthabenBeiZuteilung": 0,
            "sparBeitragMonatlich": 0,
            "sparPhaseInJahren": 0
          },
          "tarif": "string",
          "tilgungsPhase": {
            "bausparDarlehenSumme": 0,
            "sollZinsNachZuteilung": 0,
            "tilgungsBeitragMonatlich": 0,
            "tilgungsPhaseInJahren": 0
          },
          "typ": "string",
          "vertragsBeginn": "2020-02-24",
          "vertragsNummer": "string",
          "verwaltungsgebuehrenJaehrlich": 0,
          "zuteilungsDatum": "2020-02-24"
        }
      ],
      "finanzbedarf": {
        "anzahlTeilzahlungen": 0,
        "aussenAnlagen": 0,
        "bauNebenkosten": 0,
        "beratungsHonorar": 0,
        "bereitsBeglichen": 0,
        "erschliessung": 0,
        "grunderwerbsteuer": 0,
        "grundstueckBereitsBezahlt": true,
        "grundstuecksKaufpreis": 0,
        "herstellung": 0,
        "kapitalBeschaffung": 0,
        "kapitalWirdBeschafft": true,
        "kaufpreis": 0,
        "maklergebuehr": 0,
        "mobiliar": 0,
        "modernisieren": true,
        "modernisierung": 0,
        "notargebuehr": 0,
        "renovierung": 0,
        "sonstigeKosten": 0,
        "zusaetzlichesKapital": 0
      },
      "finanzierungswunsch": {
        "bausparWuensche": [
          {
            "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
            "bausparSummeAbsolut": 0,
            "bausparSummeRelativ": 0,
            "bausparTarif": [
              {
                "id": "string",
                "kurzName": "string",
                "langName": "string",
                "produktAnbieter": "string",
                "riesterFoerderung": true,
                "status": "AKTIV"
              }
            ],
            "bausparTarife": [
              "string"
            ],
            "id": "string",
            "sonderZahlungEinmalig": 0,
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeginn": "2020-02-24",
            "sparBeitragMonatlichAbsolut": 0,
            "sparBeitragMonatlichRelativ": 0,
            "tilgungsBeitragMonatlich": 0,
            "vertragsPartnerIds": [
              "string"
            ],
            "verwendung": "ZINS_ABSICHERUNG",
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "darlehensWuensche": [
          {
            "annuitaetenDarlehen": {
              "auszahlungsDatum": "2020-02-24",
              "bereitstellungsZinsFreieZeitInMonaten": 0,
              "darlehensBetrag": 0,
              "provision": 0,
              "sondertilgungOptionalJaehrlich": 0,
              "tilgungsWunsch": {
                "anfaenglicheTilgung": 0,
                "ausgesetztBerechnet": false,
                "ausgesetztEigenesAngebot": false,
                "bausparWunsch": {
                  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                  "bausparSummeAbsolut": 0,
                  "bausparSummeRelativ": 0,
                  "bausparTarif": [
                    {}
                  ],
                  "bausparTarife": [
                    "string"
                  ],
                  "id": "string",
                  "sonderZahlungEinmalig": 0,
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeginn": "2020-02-24",
                  "sparBeitragMonatlichAbsolut": 0,
                  "sparBeitragMonatlichRelativ": 0,
                  "tilgungsBeitragMonatlich": 0,
                  "vertragsPartnerIds": [
                    "string"
                  ],
                  "verwendung": "ZINS_ABSICHERUNG",
                  "zuteilungsDatum": "2020-02-24"
                },
                "rate": 0,
                "tilgungsBeginn": "2020-02-24",
                "tilgungsErsatzProduktId": "string",
                "volltilgerWennAnnuitaetenOderForward": false
              },
              "zinsBindungInJahren": 0
            },
            "forwardDarlehen": {
              "auszahlungsDatum": "2020-02-24",
              "bereitstellungsZinsFreieZeitInMonaten": 0,
              "darlehensBetrag": 0,
              "provision": 0,
              "sondertilgungOptionalJaehrlich": 0,
              "tilgungsWunsch": {
                "anfaenglicheTilgung": 0,
                "ausgesetztBerechnet": false,
                "ausgesetztEigenesAngebot": false,
                "bausparWunsch": {
                  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                  "bausparSummeAbsolut": 0,
                  "bausparSummeRelativ": 0,
                  "bausparTarif": [
                    {}
                  ],
                  "bausparTarife": [
                    "string"
                  ],
                  "id": "string",
                  "sonderZahlungEinmalig": 0,
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeginn": "2020-02-24",
                  "sparBeitragMonatlichAbsolut": 0,
                  "sparBeitragMonatlichRelativ": 0,
                  "tilgungsBeitragMonatlich": 0,
                  "vertragsPartnerIds": [
                    "string"
                  ],
                  "verwendung": "ZINS_ABSICHERUNG",
                  "zuteilungsDatum": "2020-02-24"
                },
                "rate": 0,
                "tilgungsBeginn": "2020-02-24",
                "tilgungsErsatzProduktId": "string",
                "volltilgerWennAnnuitaetenOderForward": false
              },
              "zinsBindungInJahren": 0
            },
            "id": "string",
            "kfwDarlehen": {
              "darlehensBetrag": 0,
              "kfwEndfaellig": "NEIN",
              "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
              "kfwProgramm": "PROGRAMM_124",
              "laufzeitInJahren": 0,
              "provision": 0,
              "tilgungsWunsch": {
                "anfaenglicheTilgung": 0,
                "ausgesetztBerechnet": false,
                "ausgesetztEigenesAngebot": false,
                "bausparWunsch": {
                  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                  "bausparSummeAbsolut": 0,
                  "bausparSummeRelativ": 0,
                  "bausparTarif": [
                    {}
                  ],
                  "bausparTarife": [
                    "string"
                  ],
                  "id": "string",
                  "sonderZahlungEinmalig": 0,
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeginn": "2020-02-24",
                  "sparBeitragMonatlichAbsolut": 0,
                  "sparBeitragMonatlichRelativ": 0,
                  "tilgungsBeitragMonatlich": 0,
                  "vertragsPartnerIds": [
                    "string"
                  ],
                  "verwendung": "ZINS_ABSICHERUNG",
                  "zuteilungsDatum": "2020-02-24"
                },
                "rate": 0,
                "tilgungsBeginn": "2020-02-24",
                "tilgungsErsatzProduktId": "string",
                "volltilgerWennAnnuitaetenOderForward": false
              },
              "tilgungsfreieAnlaufjahre": 0,
              "zinsBindungInJahren": 0
            },
            "privatDarlehen": {
              "darlehensBetrag": 0,
              "laufzeitInMonaten": 0,
              "provision": 0
            },
            "variablesDarlehen": {
              "darlehensBetrag": 0,
              "provision": 0,
              "tilgungsWunsch": {
                "anfaenglicheTilgung": 0,
                "ausgesetztBerechnet": false,
                "ausgesetztEigenesAngebot": false,
                "bausparWunsch": {
                  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                  "bausparSummeAbsolut": 0,
                  "bausparSummeRelativ": 0,
                  "bausparTarif": [
                    {}
                  ],
                  "bausparTarife": [
                    "string"
                  ],
                  "id": "string",
                  "sonderZahlungEinmalig": 0,
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeginn": "2020-02-24",
                  "sparBeitragMonatlichAbsolut": 0,
                  "sparBeitragMonatlichRelativ": 0,
                  "tilgungsBeitragMonatlich": 0,
                  "vertragsPartnerIds": [
                    "string"
                  ],
                  "verwendung": "ZINS_ABSICHERUNG",
                  "zuteilungsDatum": "2020-02-24"
                },
                "rate": 0,
                "tilgungsBeginn": "2020-02-24",
                "tilgungsErsatzProduktId": "string",
                "volltilgerWennAnnuitaetenOderForward": false
              }
            },
            "zwischenFinanzierung": {
              "darlehensBetrag": 0,
              "detailsZurVerwendung": "string",
              "maximaleLaufzeitInMonaten": 0,
              "provision": 0,
              "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
            }
          }
        ],
        "id": "string"
      },
      "id": "string",
      "nachfinanzierung": true,
      "nachrangigeExterneDarlehen": [
        {
          "darlehensBetrag": 0,
          "darlehensGeber": "string",
          "id": "string",
          "laufzeitEnde": "2020-02-24",
          "rateMonatlich": 0,
          "typ": "ARBEITGEBERDARLEHEN",
          "zinsBindung": {
            "endetAm": "2020-02-24",
            "jahre": 0,
            "monate": 0,
            "restschuldNachZinsBindungsEnde": 0
          }
        }
      ],
      "praeferenzen": {
        "bereitstellungsZinsFreieZeit": {
          "darlehenBenoetigtInMonaten": 0,
          "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
          "zusatzlicheKommentare": "string"
        },
        "bestandteileDerFinanzierung": {
          "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
          "zusatzlicheKommentare": "string"
        },
        "hoeheDerRate": {
          "betrag": 0,
          "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
          "zusatzlicheKommentare": "string"
        },
        "laufzeit": {
          "bisZumJahr": "2016",
          "bisZurRenteImJahr": "2016",
          "inJahren": 0,
          "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
          "zusatzlicheKommentare": "string"
        },
        "sondertilgung": {
          "betragEinmalig": 0,
          "betragJaehrlich": 0,
          "praeferenzAuswahl": "JAEHRLICH",
          "zusatzlicheKommentare": "string"
        },
        "tilgungsSatzWechsel": {
          "mindestensBenoetigt": 0,
          "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
          "zusatzlicheKommentare": "string"
        },
        "weiterePraeferenz": "string",
        "zeitlicherRahmen": {
          "finanzierungszusageBis": "2020-02-24",
          "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
          "zusatzlicheKommentare": "string"
        },
        "zinsBindung": {
          "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
          "zinsBindungBisJahren": 0,
          "zinsBindungVonJahren": 0,
          "zinsBindungZwischenJahren": 0,
          "zusatzlicheKommentare": "string"
        }
      },
      "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
    }
  },
  "_links": {
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}
```

<h3 id="getantrag-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Antrag](#schemaantrag)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[Error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[Error](#schemaerror)|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Method Not Allowed|[Error](#schemaerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)|
|502|[Bad Gateway](https://tools.ietf.org/html/rfc7231#section-6.6.3)|Bad Gateway|[Error](#schemaerror)|
|504|[Gateway Time-out](https://tools.ietf.org/html/rfc7231#section-6.6.5)|Gateway Timeout|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### setAntragsStatus

<a id="opIdsetAntragsStatus"></a>

> Code samples

```shell
## You can also use wget
curl -X POST https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}/{teilantragsNummer}/status \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}/{teilantragsNummer}/status");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}/{teilantragsNummer}/status',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`POST /v2/vorgaenge/{vorgangsNummer}/antraege/{antragsNummer}/{teilantragsNummer}/status`

*Zum Setzen des Antragsstatus*

> Body parameter

```json
{
  "ablehnungsgrund": "FINANZIELLE_SITUATION",
  "antragsteller": "BEANTRAGT",
  "kommentar": "string",
  "produktAnbieter": "NICHT_BEARBEITET"
}
```

<h3 id="setantragsstatus-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|
|antragsNummer|path|integer(int32)|true|antragsNummer|
|teilantragsNummer|path|integer(int32)|true|teilantragsNummer|
|body|body|[StatusDTO](#schemastatusdto)|true|statusDTO|

> Example responses

> 400 Response

```json
{
  "message": "string",
  "statusCode": 0,
  "statusMessage": "string",
  "timestamp": "string",
  "traceId": "string"
}
```

<h3 id="setantragsstatus-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Accepted|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[Error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[Error](#schemaerror)|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Method Not Allowed|[Error](#schemaerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)|
|502|[Bad Gateway](https://tools.ietf.org/html/rfc7231#section-6.6.3)|Bad Gateway|[Error](#schemaerror)|
|504|[Gateway Time-out](https://tools.ietf.org/html/rfc7231#section-6.6.5)|Gateway Timeout|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### getKundenbetreuer

<a id="opIdgetKundenbetreuer"></a>

> Code samples

```shell
## You can also use wget
curl -X GET https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/kundenBetreuer \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/kundenBetreuer");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/kundenBetreuer',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /v2/vorgaenge/{vorgangsNummer}/kundenBetreuer`

*Den Kundenbetreuer des Vorgangs abrufen*

Als Parameter wird die Vorgangsnummer verwendet, die aus BaufiSmart erzeugt wurde.

<h3 id="getkundenbetreuer-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|

> Example responses

> 200 Response

```json
{
  "anrede": "FRAU",
  "anschrift": {
    "hausnummer": "string",
    "ort": "string",
    "postleitzahl": "string",
    "strasse": "string"
  },
  "email": "string",
  "externePartnerId": "string",
  "externerKreditSachbearbeiterId": "string",
  "fax": "string",
  "firmenNameZusatz": "string",
  "firmierung": "string",
  "geburtsdatum": "2020-02-24",
  "id": "string",
  "kreditsachbearbeiter": true,
  "mobilTelefon": "string",
  "nachname": "string",
  "partnerId": "string",
  "telefonnummer": "string",
  "vertriebsOrganisation": {
    "firma": "string",
    "name": "string",
    "vertriebsOrganisationsId": "string"
  },
  "vorname": "string",
  "webseite": "string",
  "_links": {
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}
```

<h3 id="getkundenbetreuer-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Partner](#schemapartner)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[Error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[Error](#schemaerror)|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Method Not Allowed|[Error](#schemaerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)|
|502|[Bad Gateway](https://tools.ietf.org/html/rfc7231#section-6.6.3)|Bad Gateway|[Error](#schemaerror)|
|504|[Gateway Time-out](https://tools.ietf.org/html/rfc7231#section-6.6.5)|Gateway Timeout|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### updateKundenBetreuerUsingPUT

<a id="opIdupdateKundenBetreuerUsingPUT"></a>

> Code samples

```shell
## You can also use wget
curl -X PUT https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/kundenBetreuer \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/kundenBetreuer");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/kundenBetreuer',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`PUT /v2/vorgaenge/{vorgangsNummer}/kundenBetreuer`

*Den Kundenbetreuer ändern*

> Body parameter

```json
{
  "partnerId": "string"
}
```

<h3 id="updatekundenbetreuerusingput-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|
|body|body|[PartnerDTO](#schemapartnerdto)|true|partnerDTO|

<h3 id="updatekundenbetreuerusingput-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### getVorgangsBearbeiter

<a id="opIdgetVorgangsBearbeiter"></a>

> Code samples

```shell
## You can also use wget
curl -X GET https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/vorgangsBearbeiter \
  -H 'Accept: application/json;charset=UTF-8' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/vorgangsBearbeiter");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Accept':'application/json;charset=UTF-8',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/vorgangsBearbeiter',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /v2/vorgaenge/{vorgangsNummer}/vorgangsBearbeiter`

*Den Vorgangsbearbeiter des Vorgangs abrufen*

Als Parameter wird die Vorgangsnummer verwendet, die aus BaufiSmart erzeugt wurde.

<h3 id="getvorgangsbearbeiter-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|

> Example responses

> 200 Response

```json
{
  "anrede": "FRAU",
  "anschrift": {
    "hausnummer": "string",
    "ort": "string",
    "postleitzahl": "string",
    "strasse": "string"
  },
  "email": "string",
  "externePartnerId": "string",
  "externerKreditSachbearbeiterId": "string",
  "fax": "string",
  "firmenNameZusatz": "string",
  "firmierung": "string",
  "geburtsdatum": "2020-02-24",
  "id": "string",
  "kreditsachbearbeiter": true,
  "mobilTelefon": "string",
  "nachname": "string",
  "partnerId": "string",
  "telefonnummer": "string",
  "vertriebsOrganisation": {
    "firma": "string",
    "name": "string",
    "vertriebsOrganisationsId": "string"
  },
  "vorname": "string",
  "webseite": "string",
  "_links": {
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}
```

<h3 id="getvorgangsbearbeiter-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[Partner](#schemapartner)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[Error](#schemaerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[Error](#schemaerror)|
|405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|Method Not Allowed|[Error](#schemaerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[Error](#schemaerror)|
|502|[Bad Gateway](https://tools.ietf.org/html/rfc7231#section-6.6.3)|Bad Gateway|[Error](#schemaerror)|
|504|[Gateway Time-out](https://tools.ietf.org/html/rfc7231#section-6.6.5)|Gateway Timeout|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

### putVorgangsBearbeiterIdUsingPUT

<a id="opIdputVorgangsBearbeiterIdUsingPUT"></a>

> Code samples

```shell
## You can also use wget
curl -X PUT https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/vorgangsBearbeiter \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```java
URL obj = new URL("https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/vorgangsBearbeiter");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://baufismart.api.europace.de/v2/vorgaenge/{vorgangsNummer}/vorgangsBearbeiter',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`PUT /v2/vorgaenge/{vorgangsNummer}/vorgangsBearbeiter`

*putVorgangsBearbeiterId*

> Body parameter

```json
{
  "partnerId": "string"
}
```

<h3 id="putvorgangsbearbeiteridusingput-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|vorgangsNummer|path|string|true|vorgangsNummer|
|body|body|[PartnerDTO](#schemapartnerdto)|true|partnerDTO|

<h3 id="putvorgangsbearbeiteridusingput-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: API )
</aside>

## Schemas

<h2 id="tocSabsicherung">Absicherung</h2>

<a id="schemaabsicherung"></a>

```json
{
  "abgesicherteRisiken": [
    {
      "abgesichertesRisiko": "TODESFALL",
      "auszahlungsBetrag": 0,
      "auszahlungsTurnus": "EINMALIG",
      "praemienAnteil": 0
    }
  ],
  "gesamtPraemie": 0,
  "praemienZahlungsweise": "EINMALIG",
  "tarifBezeichnung": "string",
  "tarifKennung": "string",
  "versichertePersonId": "string",
  "versicherungsArt": "string",
  "versicherungsNummer": "string",
  "versicherungsZeitraum": {
    "beginn": "2020-02-24",
    "dauerInMonaten": 0,
    "ende": "2020-02-24"
  }
}

```

*Absicherung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abgesicherteRisiken|[[RisikoAbsicherung](#schemarisikoabsicherung)]|false|none|none|
|gesamtPraemie|number|false|none|none|
|praemienZahlungsweise|string|false|none|none|
|tarifBezeichnung|string|false|none|none|
|tarifKennung|string|false|none|none|
|versichertePersonId|string|false|none|none|
|versicherungsArt|string|false|none|none|
|versicherungsNummer|string|false|none|none|
|versicherungsZeitraum|[VersicherungsZeitraum](#schemaversicherungszeitraum)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praemienZahlungsweise|EINMALIG|
|praemienZahlungsweise|MONATLICH|
|praemienZahlungsweise|VIERTELJAEHRLICH|
|praemienZahlungsweise|HALBJAEHRLICH|
|praemienZahlungsweise|JAEHRLICH|

<h2 id="tocSabsicherungswunsch">Absicherungswunsch</h2>

<a id="schemaabsicherungswunsch"></a>

```json
{
  "id": "string",
  "versicherungsWuensche": [
    {
      "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
      "id": "string",
      "praemienZahlungsweise": "EINMALIG",
      "risikoAbsicherungsWuensche": [
        {
          "abzusicherndesRisiko": "TODESFALL",
          "versicherteRate": 0,
          "versicherungsSumme": 0
        }
      ],
      "versichertePersonId": "string",
      "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
      "versicherungsBeginn": "2020-02-24",
      "versicherungsDauerInMonaten": 0
    }
  ]
}

```

*Absicherungswunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|versicherungsWuensche|[[VersicherungsWunsch](#schemaversicherungswunsch)]|false|none|none|

<h2 id="tocSangebot">Angebot</h2>

<a id="schemaangebot"></a>

```json
{
  "absicherungen": [
    {
      "abgesicherteRisiken": [
        {
          "abgesichertesRisiko": "TODESFALL",
          "auszahlungsBetrag": 0,
          "auszahlungsTurnus": "EINMALIG",
          "praemienAnteil": 0
        }
      ],
      "gesamtPraemie": 0,
      "praemienZahlungsweise": "EINMALIG",
      "tarifBezeichnung": "string",
      "tarifKennung": "string",
      "versichertePersonId": "string",
      "versicherungsArt": "string",
      "versicherungsNummer": "string",
      "versicherungsZeitraum": {
        "beginn": "2020-02-24",
        "dauerInMonaten": 0,
        "ende": "2020-02-24"
      }
    }
  ],
  "bausparvertraege": [
    {
      "abschlussGebuehr": 0,
      "angebotsHinweisFuerAntragsteller": "string",
      "bausparSumme": 0,
      "einmalzahlung": 0,
      "gesamtLaufzeitInJahren": 0,
      "id": "string",
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "sonderZahlungen": [
        {
          "anzahl": 0,
          "betrag": 0,
          "termin": "2020-02-24",
          "zahlweise": "EINMALIG"
        }
      ],
      "sparPhase": {
        "guthabenBeiZuteilung": 0,
        "sparBeitragMonatlich": 0,
        "sparPhaseInJahren": 0
      },
      "tarif": "string",
      "tilgungsPhase": {
        "bausparDarlehenSumme": 0,
        "sollZinsNachZuteilung": 0,
        "tilgungsBeitragMonatlich": 0,
        "tilgungsPhaseInJahren": 0
      },
      "typ": "string",
      "vertragsBeginn": "2020-02-24",
      "vertragsNummer": "string",
      "verwaltungsgebuehrenJaehrlich": 0,
      "zuteilungsDatum": "2020-02-24"
    }
  ],
  "beleihungsRechnung": {
    "beleihungsAuslauf": 0,
    "beleihungsWerte": [
      {
        "beleihungsWert": 0,
        "immobilie": {
          "id": "string"
        }
      }
    ],
    "beleihungsWerteSumme": 0,
    "produktAnbieter": {
      "anrede": "FRAU",
      "anschrift": {
        "hausnummer": "string",
        "ort": "string",
        "postleitzahl": "string",
        "strasse": "string"
      },
      "email": "string",
      "externePartnerId": "string",
      "externerKreditSachbearbeiterId": "string",
      "fax": "string",
      "firmenNameZusatz": "string",
      "firmierung": "string",
      "geburtsdatum": "2020-02-24",
      "id": "string",
      "kreditsachbearbeiter": true,
      "mobilTelefon": "string",
      "nachname": "string",
      "partnerId": "string",
      "produktAnbieterId": "string",
      "telefonnummer": "string",
      "vertriebsOrganisation": {
        "firma": "string",
        "name": "string",
        "vertriebsOrganisationsId": "string"
      },
      "vorname": "string",
      "webseite": "string"
    }
  },
  "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
  "darlehen": [
    {
      "auszahlungsBetrag": 0,
      "auszahlungsDatum": "2020-02-24",
      "auszahlungsKurs": 0,
      "bereitstellung": {
        "bereitstellungsZins": 0,
        "bereitstellungsZinsFreieZeitInMonaten": 0
      },
      "darlehensBetrag": 0,
      "darlehensTyp": "ANNUITAETEN_DARLEHEN",
      "detailsZurVerwendung": "string",
      "effektivZins": 0,
      "effektivZinsRelevanteKosten": {
        "beratungsHonorar": 0,
        "grundbuchKosten": 0,
        "sonstigeKosten": 0,
        "tilgungsErsatzProduktKosten": 0,
        "wohnGebaeudeVersicherungsKosten": 0,
        "zinsabsicherungsKosten": 0,
        "zusatzSicherheitsKosten": 0
      },
      "forwardPeriodeInMonaten": 0,
      "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
      "kfwProgramm": "PROGRAMM_124",
      "konditionWurdeManuellAngepasst": true,
      "konditionsAnpassungsBegruendung": "string",
      "laufZeitInJahren": 0,
      "laufzeitInMonaten": 0,
      "maximaleLaufzeitInMonaten": 0,
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "rateMonatlich": 123.34,
      "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
      "sollZins": 2.05,
      "tilgung": {
        "anfaenglicheTilgung": 0,
        "sonderTilgungJaehrlich": 0,
        "tilgungsBeginnAm": "2020-02-24",
        "tilgungsErsatz": {
          "id": "string",
          "typ": "string"
        }
      },
      "tilgungsFreieAnlaufJahre": 0,
      "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
      "zinsBindung": {
        "endetAm": "2020-02-24",
        "jahre": 0,
        "monate": 0,
        "restschuldNachZinsBindungsEnde": 0
      },
      "zinsZahlungsBeginnAm": "2020-02-24"
    }
  ],
  "erzeugtAm": "2020-02-24T11:55:47Z",
  "kennung": "string",
  "machbarkeitsStatus": "MACHBAR",
  "meldungen": [
    {
      "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
      "kreditEntscheider": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "text": "string"
    }
  ],
  "pruefungsErgebnisse": [
    {
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "weitereAngaben": "string"
    }
  ],
  "_links": {
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}

```

*Angebot*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|absicherungen|[[Absicherung](#schemaabsicherung)]|false|none|none|
|bausparvertraege|[[Bausparvertrag](#schemabausparvertrag)]|false|none|none|
|beleihungsRechnung|[BeleihungsRechnung](#schemabeleihungsrechnung)|false|none|none|
|bewertungDesAngebots|string|false|none|none|
|darlehen|[[Darlehen](#schemadarlehen)]|false|none|none|
|erzeugtAm|string(date-time)|false|none|Erzeugungsdatum des Angebots|
|kennung|string|false|none|none|
|machbarkeitsStatus|string|false|none|none|
|meldungen|[[Meldung](#schemameldung)]|false|none|none|
|pruefungsErgebnisse|[[AngebotsPruefungsErgebnis](#schemaangebotspruefungsergebnis)]|false|none|none|
|_links|[Links](#schemalinks)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|bewertungDesAngebots|ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS|
|bewertungDesAngebots|ANGEBOT_ENTSPRICHT_DEM_WUNSCH_DES_KUNDEN|
|machbarkeitsStatus|MACHBAR|
|machbarkeitsStatus|UNTER_VORBEHALT_PRODUZENT|
|machbarkeitsStatus|NICHT_MACHBAR|

<h2 id="tocSangebotspruefungsergebnis">AngebotsPruefungsErgebnis</h2>

<a id="schemaangebotspruefungsergebnis"></a>

```json
{
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "weitereAngaben": "string"
}

```

*AngebotsPruefungsErgebnis*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|produktAnbieter|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|weitereAngaben|string|false|none|Vom Produktanbieter bei der Angebotsprüfung ergänzte Daten. Das Format entspricht der Definition des Produktanbieters.|

<h2 id="tocSannuitaetendarlehenswunsch">AnnuitaetenDarlehensWunsch</h2>

<a id="schemaannuitaetendarlehenswunsch"></a>

```json
{
  "auszahlungsDatum": "2020-02-24",
  "bereitstellungsZinsFreieZeitInMonaten": 0,
  "darlehensBetrag": 0,
  "provision": 0,
  "sondertilgungOptionalJaehrlich": 0,
  "tilgungsWunsch": {
    "anfaenglicheTilgung": 0,
    "ausgesetztBerechnet": false,
    "ausgesetztEigenesAngebot": false,
    "bausparWunsch": {
      "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
      "bausparSummeAbsolut": 0,
      "bausparSummeRelativ": 0,
      "bausparTarif": [
        {
          "id": "string",
          "kurzName": "string",
          "langName": "string",
          "produktAnbieter": "string",
          "riesterFoerderung": true,
          "status": "AKTIV"
        }
      ],
      "bausparTarife": [
        "string"
      ],
      "id": "string",
      "sonderZahlungEinmalig": 0,
      "sonderZahlungen": [
        {
          "anzahl": 0,
          "betrag": 0,
          "termin": "2020-02-24",
          "zahlweise": "EINMALIG"
        }
      ],
      "sparBeginn": "2020-02-24",
      "sparBeitragMonatlichAbsolut": 0,
      "sparBeitragMonatlichRelativ": 0,
      "tilgungsBeitragMonatlich": 0,
      "vertragsPartnerIds": [
        "string"
      ],
      "verwendung": "ZINS_ABSICHERUNG",
      "zuteilungsDatum": "2020-02-24"
    },
    "rate": 0,
    "tilgungsBeginn": "2020-02-24",
    "tilgungsErsatzProduktId": "string",
    "volltilgerWennAnnuitaetenOderForward": false
  },
  "zinsBindungInJahren": 0
}

```

*AnnuitaetenDarlehensWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|auszahlungsDatum|string(date)|false|none|none|
|bereitstellungsZinsFreieZeitInMonaten|integer(int32)|false|none|none|
|darlehensBetrag|number|false|none|none|
|provision|number|false|none|none|
|sondertilgungOptionalJaehrlich|number|false|none|none|
|tilgungsWunsch|[TilgungsWunsch](#schematilgungswunsch)|false|none|none|
|zinsBindungInJahren|integer(int32)|false|none|none|

<h2 id="tocSantraege">Antraege</h2>

<a id="schemaantraege"></a>

```json
{
  "antraege": [
    {
      "angebot": {
        "absicherungen": [
          {
            "abgesicherteRisiken": [
              {
                "abgesichertesRisiko": "TODESFALL",
                "auszahlungsBetrag": 0,
                "auszahlungsTurnus": "EINMALIG",
                "praemienAnteil": 0
              }
            ],
            "gesamtPraemie": 0,
            "praemienZahlungsweise": "EINMALIG",
            "tarifBezeichnung": "string",
            "tarifKennung": "string",
            "versichertePersonId": "string",
            "versicherungsArt": "string",
            "versicherungsNummer": "string",
            "versicherungsZeitraum": {
              "beginn": "2020-02-24",
              "dauerInMonaten": 0,
              "ende": "2020-02-24"
            }
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "angebotsHinweisFuerAntragsteller": "string",
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "gesamtLaufzeitInJahren": 0,
            "id": "string",
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparPhase": {
              "guthabenBeiZuteilung": 0,
              "sparBeitragMonatlich": 0,
              "sparPhaseInJahren": 0
            },
            "tarif": "string",
            "tilgungsPhase": {
              "bausparDarlehenSumme": 0,
              "sollZinsNachZuteilung": 0,
              "tilgungsBeitragMonatlich": 0,
              "tilgungsPhaseInJahren": 0
            },
            "typ": "string",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "beleihungsRechnung": {
          "beleihungsAuslauf": 0,
          "beleihungsWerte": [
            {
              "beleihungsWert": 0,
              "immobilie": {
                "id": "string"
              }
            }
          ],
          "beleihungsWerteSumme": 0,
          "produktAnbieter": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          }
        },
        "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
        "darlehen": [
          {
            "auszahlungsBetrag": 0,
            "auszahlungsDatum": "2020-02-24",
            "auszahlungsKurs": 0,
            "bereitstellung": {
              "bereitstellungsZins": 0,
              "bereitstellungsZinsFreieZeitInMonaten": 0
            },
            "darlehensBetrag": 0,
            "darlehensTyp": "ANNUITAETEN_DARLEHEN",
            "detailsZurVerwendung": "string",
            "effektivZins": 0,
            "effektivZinsRelevanteKosten": {
              "beratungsHonorar": 0,
              "grundbuchKosten": 0,
              "sonstigeKosten": 0,
              "tilgungsErsatzProduktKosten": 0,
              "wohnGebaeudeVersicherungsKosten": 0,
              "zinsabsicherungsKosten": 0,
              "zusatzSicherheitsKosten": 0
            },
            "forwardPeriodeInMonaten": 0,
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "konditionWurdeManuellAngepasst": true,
            "konditionsAnpassungsBegruendung": "string",
            "laufZeitInJahren": 0,
            "laufzeitInMonaten": 0,
            "maximaleLaufzeitInMonaten": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "rateMonatlich": 123.34,
            "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
            "sollZins": 2.05,
            "tilgung": {
              "anfaenglicheTilgung": 0,
              "sonderTilgungJaehrlich": 0,
              "tilgungsBeginnAm": "2020-02-24",
              "tilgungsErsatz": {
                "id": "string",
                "typ": "string"
              }
            },
            "tilgungsFreieAnlaufJahre": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
            "zinsBindung": {
              "endetAm": "2020-02-24",
              "jahre": 0,
              "monate": 0,
              "restschuldNachZinsBindungsEnde": 0
            },
            "zinsZahlungsBeginnAm": "2020-02-24"
          }
        ],
        "erzeugtAm": "2020-02-24T11:55:47Z",
        "kennung": "string",
        "machbarkeitsStatus": "MACHBAR",
        "meldungen": [
          {
            "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
            "kreditEntscheider": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "text": "string"
          }
        ],
        "pruefungsErgebnisse": [
          {
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "weitereAngaben": "string"
          }
        ],
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "ansprechpartner": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "antragsNummer": "string",
      "beratung": {
        "art": "PRAESENZ_GESCHAEFT",
        "hinweisFuerProduktAnbieter": "string",
        "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
      },
      "datenKontext": "TEST_MODUS",
      "dokumente": [
        {
          "art": "string",
          "href": "string",
          "name": "string",
          "titel": "string",
          "type": "string"
        }
      ],
      "kreditSachbearbeiter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "status": {
        "ablehnungsgrund": "FINANZIELLE_SITUATION",
        "antragsteller": "BEANTRAGT",
        "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
        "produktAnbieter": "NICHT_BEARBEITET"
      },
      "vermittler": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "zeitpunktDerAnnahme": "2020-02-24T11:55:47Z",
      "zugrundeliegendeDaten": {
        "bankverbindung": {
          "bic": "string",
          "iban": "string",
          "id": "string",
          "kontoinhaberIds": [
            "string"
          ],
          "kontoinhaberName": "string",
          "kreditinstitut": "string"
        },
        "finanzierungsObjekt": {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "verwendenAls": "ABLOESEN",
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "keinBaulandFlaecheInQm": 0,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        },
        "haushalte": [
          {
            "antragsteller": [
              {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "arbeitserlaubnis": false,
                "arbeitserlaubnisBefristetBis": "2020-02-24",
                "aufenthaltsTitel": "VISUM",
                "aufenthaltsTitelBefristetBis": "2020-02-24",
                "beschaeftigung": {
                  "anzahlGehaelterProJahr": 0,
                  "arbeitgeber": "string",
                  "arbeitgeberInDeutschlandAnsaessig": false,
                  "arbeitgeberLand": {
                    "isoCountryCode": "string",
                    "name": "string"
                  },
                  "art": "ANGESTELLTER",
                  "befristungsStatus": "BEFRISTET",
                  "beruf": "string",
                  "beschaeftigtSeit": "2020-02-24",
                  "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
                  "einkommenNettoJaehrlich": 0,
                  "einkommenNettoMonatlich": 0,
                  "firma": "string",
                  "inProbezeit": false,
                  "situationNachRenteneintritt": {
                    "gesetzlicheRenteMonatlich": 0,
                    "privateRenteMonatlich": 0,
                    "rentenBeginn": "2020-02-24",
                    "sonstigesEinkommenMonatlich": 0
                  },
                  "taetigkeit": "ALTENPFLEGER"
                },
                "bruttoVorjahresEinkommen": 0,
                "email": "max.mustermann@test.de",
                "externeAntragstellerId": "string",
                "familienstand": "GESCHIEDEN",
                "geburtsdatum": "2020-02-24",
                "geburtsort": "string",
                "guetertrennungVereinbartWennVerheiratet": false,
                "id": "string",
                "inDeutschlandSeit": "2020-02-24",
                "legitimationsDaten": {
                  "ausstellendeBehoerde": "string",
                  "ausstellungsdatum": "2020-02-24",
                  "ausweisArt": "PERSONALAUSWEIS",
                  "ausweisArtBeiAndererAusweis": "string",
                  "ausweisNummer": "string"
                },
                "nachname": "string",
                "schufaErgebnis": {
                  "antragstellerUnbekannt": false,
                  "inManuellerNachbehandlung": false,
                  "score": "string"
                },
                "staatsangehoerigkeit": {
                  "isoCountryCode": "string",
                  "name": "string"
                },
                "steuerId": "string",
                "telefonnummer": "string",
                "telefonnummerVorwahl": "string",
                "titel": [
                  "DOKTOR"
                ],
                "titelDoktor": true,
                "titelProfessor": true,
                "vorAnschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "vorname": "string",
                "weitereKontaktMoeglichkeiten": "string",
                "wohnhaftSeit": "2020-02-24"
              }
            ],
            "anzahlErwachseneImHaushalt": 0,
            "anzahlKinderNichtImHaushalt": 0,
            "bestehendeImmobilien": [
              {
                "adresse": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "autostellplaetze": [
                  {
                    "mieteinnahmenMonatlich": 0,
                    "typ": "STELLPLATZ"
                  }
                ],
                "bestehendeDarlehen": [
                  {
                    "abzuloesendeRestschuld": 0,
                    "aktuelleRestschuldWennNichtAbzuloesen": 0,
                    "darlehensArt": "BAUSPARDARLEHEN",
                    "darlehensBetrag": 0,
                    "darlehensGeber": {},
                    "darlehensKontonummer": "string",
                    "eingetrageneGrundschuld": 0,
                    "grundschuldArt": "BRIEF_GRUNDSCHULD",
                    "id": "string",
                    "laufzeitEnde": "2020-02-24",
                    "rateMonatlich": 0,
                    "sollZins": 0,
                    "sondertilgungZumZinsBindungsEnde": 0,
                    "zinsBindungEndetAm": "2020-02-24"
                  }
                ],
                "bewirtschaftungsKostenJaehrlich": 0,
                "bodenRichtwert": 0,
                "bundesland": "BADEN_WUERTTEMBERG",
                "effektivZinsErhoehendeKosten": {
                  "anpassen": true,
                  "grundbuchEintragungsKostenEinmalig": 0,
                  "sonstigeKostenBezeichnung": "string",
                  "sonstigeKostenEinmalig": 0,
                  "wohnGebaeudeVersicherungsKostenJaehrlich": 0
                },
                "erbbaurecht": {
                  "erbbaurecht": true,
                  "erbbauzinsJaehrlich": 0,
                  "grundstuecksEigentuemer": "ANDERE",
                  "laufzeitBisJahr": "string"
                },
                "gebaeude": {
                  "anzahlDerGewerbeeinheiten": 0,
                  "anzahlDerWohneinheitenImGebaeude": 0,
                  "anzahlVollgeschosse": 0,
                  "aufbauFinanzierung": true,
                  "aufzugVorhanden": true,
                  "ausstattung": "EINFACH",
                  "baujahr": "2016",
                  "bauweise": "FACHWERK_MIT_STROH_LEHM",
                  "bezeichnungWohneinheit": "string",
                  "dachgeschossAusbau": "FLACHDACH",
                  "einliegerwohnungVorhanden": true,
                  "geschossLage": "UNTERGESCHOSS",
                  "gewerbeflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "hausAnordnung": "FREISTEHEND",
                  "hausTyp": "DOPPELHAUSHAELFTE",
                  "istFertighaus": true,
                  "kellerausbau": "AUSGEBAUT",
                  "kubatur": 0,
                  "miteigentumsAnteil": {
                    "anteil": 0,
                    "gesamt": 0
                  },
                  "modernisierungsAngaben": {
                    "badWc": true,
                    "bodenWandTreppe": true,
                    "dach": true,
                    "fenster": true,
                    "heizungZentral": true,
                    "modernisierungsGrad": "GERING",
                    "modernisierungsJahr": "string",
                    "raumaufteilung": true,
                    "stromAbwasserHeizkoerper": true,
                    "waermedaemmung": true,
                    "wurdeModernisiert": true
                  },
                  "unterkellerung": "NICHT_UNTERKELLERT",
                  "wohnflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "zustand": "SEHR_GUT"
                },
                "grundbuchAngabe": {
                  "anmerkungen": "string",
                  "bandUndBlatt": "string",
                  "flurstuecke": [
                    {}
                  ],
                  "ort": "string",
                  "rechteInAbteilung2": {
                    "beschreibung": "string",
                    "betrag": 0,
                    "vorhanden": true
                  }
                },
                "grundstueck": {
                  "groesse": 0,
                  "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
                },
                "id": "string",
                "immobilienEinsatz": "KEIN_EINSATZ",
                "keinBaulandFlaecheInQm": 0,
                "keineBestehendenDarlehenVorhanden": true,
                "marktueblicherKaufpreisProQm": 0,
                "marktwert": 0,
                "maximalEinzusetzenderBetragWennVerkauf": 0,
                "objektArt": "GRUNDSTUECK",
                "vergleichsmieteFuerGewerbeflaecheProQm": 0,
                "vergleichsmieteFuerWohnflaecheProQm": 0,
                "verkehrswert": 0,
                "vorlaeufigerVerkehrswert": 0,
                "wohnlage": "GEHOBEN"
              }
            ],
            "id": "string",
            "kfzAnzahl": 0,
            "kinder": [
              {
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kindergeldWirdBezogen": true,
                "name": "string",
                "unterhaltsEinnahmenBetragMonatlich": 0
              }
            ],
            "lebenshaltungsKostenMonatlich": 0,
            "obligo": {
              "vermoegenOderVerbindlichkeiten": [
                {
                  "aktuellerWert": 0,
                  "anrechnungFuerBlankoAnteil": 0,
                  "bezeichner": "string",
                  "kontonummer": "string",
                  "vermoegensTyp": "VERMOEGEN"
                }
              ]
            },
            "positionen": {
              "bankUndSparguthaben": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zinsertragJaehrlich": 0,
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "bausparvertraege": [
                {
                  "abschlussGebuehr": 0,
                  "aktuellerWert": 0,
                  "bausparSumme": 0,
                  "einmalzahlung": 0,
                  "ertrag": 0,
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "produktAnbieter": {
                    "anrede": "FRAU",
                    "anschrift": {},
                    "email": "string",
                    "externePartnerId": "string",
                    "externerKreditSachbearbeiterId": "string",
                    "fax": "string",
                    "firmenNameZusatz": "string",
                    "firmierung": "string",
                    "geburtsdatum": "2020-02-24",
                    "id": "string",
                    "kreditsachbearbeiter": true,
                    "mobilTelefon": "string",
                    "nachname": "string",
                    "partnerId": "string",
                    "produktAnbieterId": "string",
                    "telefonnummer": "string",
                    "vertriebsOrganisation": {},
                    "vorname": "string",
                    "webseite": "string"
                  },
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeitragMonatlich": 0,
                  "tarif": "string",
                  "typ": "string",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "vertragsBeginn": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0,
                  "zuteilungsDatum": "2020-02-24"
                }
              ],
              "ehegattenUnterhalt": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "einkuenfteAusNebentaetigkeit": [
                {
                  "beginnDerNebentaetigkeit": "2020-02-24",
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "kindergeld": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "lebensUndRentenVersicherungen": [
                {
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "praemieMonatlich": 0,
                  "rueckkaufsWertAktuell": 0,
                  "tarif": "string",
                  "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "versicherungsGesellschaft": "string",
                  "versicherungsSumme": 0,
                  "vertragsBeginn": "2020-02-24",
                  "vertragsEnde": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "mietAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "entfallenMitFinanzierung": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateDarlehen": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateKrankenversicherung": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "ratenkredite": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeEinnahmen": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVerbindlichkeiten": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVermoegen": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "sparplaene": [
                {
                  "aktuellerWert": 0,
                  "beitragMonatlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "unbefristeteZusatzRenten": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "unterhaltsVerpflichtungen": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "variableEinkuenfte": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "versicherungsAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "wertpapiere": [
                {
                  "aktuellerWert": 0,
                  "dividendenJaehrlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ]
            }
          }
        ],
        "vorhaben": {
          "absicherungswunsch": {
            "id": "string",
            "versicherungsWuensche": [
              {
                "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
                "id": "string",
                "praemienZahlungsweise": "EINMALIG",
                "risikoAbsicherungsWuensche": [
                  {
                    "abzusicherndesRisiko": "TODESFALL",
                    "versicherteRate": 0,
                    "versicherungsSumme": 0
                  }
                ],
                "versichertePersonId": "string",
                "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
                "versicherungsBeginn": "2020-02-24",
                "versicherungsDauerInMonaten": 0
              }
            ]
          },
          "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
          "externeBausparAngebote": [
            {
              "abschlussGebuehr": 0,
              "angebotsHinweisFuerAntragsteller": "string",
              "bausparSumme": 0,
              "einmalzahlung": 0,
              "id": "string",
              "produktAnbieter": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparPhase": {
                "guthabenBeiZuteilung": 0,
                "sparBeitragMonatlich": 0,
                "sparPhaseInJahren": 0
              },
              "tarif": "string",
              "tilgungsPhase": {
                "bausparDarlehenSumme": 0,
                "sollZinsNachZuteilung": 0,
                "tilgungsBeitragMonatlich": 0,
                "tilgungsPhaseInJahren": 0
              },
              "typ": "string",
              "vertragsBeginn": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zuteilungsDatum": "2020-02-24"
            }
          ],
          "finanzbedarf": {
            "anzahlTeilzahlungen": 0,
            "aussenAnlagen": 0,
            "bauNebenkosten": 0,
            "beratungsHonorar": 0,
            "bereitsBeglichen": 0,
            "erschliessung": 0,
            "grunderwerbsteuer": 0,
            "grundstueckBereitsBezahlt": true,
            "grundstuecksKaufpreis": 0,
            "herstellung": 0,
            "kapitalBeschaffung": 0,
            "kapitalWirdBeschafft": true,
            "kaufpreis": 0,
            "maklergebuehr": 0,
            "mobiliar": 0,
            "modernisieren": true,
            "modernisierung": 0,
            "notargebuehr": 0,
            "renovierung": 0,
            "sonstigeKosten": 0,
            "zusaetzlichesKapital": 0
          },
          "finanzierungswunsch": {
            "bausparWuensche": [
              {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              }
            ],
            "darlehensWuensche": [
              {
                "annuitaetenDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "forwardDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "id": "string",
                "kfwDarlehen": {
                  "darlehensBetrag": 0,
                  "kfwEndfaellig": "NEIN",
                  "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
                  "kfwProgramm": "PROGRAMM_124",
                  "laufzeitInJahren": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "tilgungsfreieAnlaufjahre": 0,
                  "zinsBindungInJahren": 0
                },
                "privatDarlehen": {
                  "darlehensBetrag": 0,
                  "laufzeitInMonaten": 0,
                  "provision": 0
                },
                "variablesDarlehen": {
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  }
                },
                "zwischenFinanzierung": {
                  "darlehensBetrag": 0,
                  "detailsZurVerwendung": "string",
                  "maximaleLaufzeitInMonaten": 0,
                  "provision": 0,
                  "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
                }
              }
            ],
            "id": "string"
          },
          "id": "string",
          "nachfinanzierung": true,
          "nachrangigeExterneDarlehen": [
            {
              "darlehensBetrag": 0,
              "darlehensGeber": "string",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "typ": "ARBEITGEBERDARLEHEN",
              "zinsBindung": {
                "endetAm": "2020-02-24",
                "jahre": 0,
                "monate": 0,
                "restschuldNachZinsBindungsEnde": 0
              }
            }
          ],
          "praeferenzen": {
            "bereitstellungsZinsFreieZeit": {
              "darlehenBenoetigtInMonaten": 0,
              "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
              "zusatzlicheKommentare": "string"
            },
            "bestandteileDerFinanzierung": {
              "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
              "zusatzlicheKommentare": "string"
            },
            "hoeheDerRate": {
              "betrag": 0,
              "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
              "zusatzlicheKommentare": "string"
            },
            "laufzeit": {
              "bisZumJahr": "2016",
              "bisZurRenteImJahr": "2016",
              "inJahren": 0,
              "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
              "zusatzlicheKommentare": "string"
            },
            "sondertilgung": {
              "betragEinmalig": 0,
              "betragJaehrlich": 0,
              "praeferenzAuswahl": "JAEHRLICH",
              "zusatzlicheKommentare": "string"
            },
            "tilgungsSatzWechsel": {
              "mindestensBenoetigt": 0,
              "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
              "zusatzlicheKommentare": "string"
            },
            "weiterePraeferenz": "string",
            "zeitlicherRahmen": {
              "finanzierungszusageBis": "2020-02-24",
              "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
              "zusatzlicheKommentare": "string"
            },
            "zinsBindung": {
              "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
              "zinsBindungBisJahren": 0,
              "zinsBindungVonJahren": 0,
              "zinsBindungZwischenJahren": 0,
              "zusatzlicheKommentare": "string"
            }
          },
          "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
        }
      },
      "_links": {
        "self": {
          "href": "string",
          "type": "string"
        }
      }
    }
  ],
  "_links": {
    "next": {
      "href": "string",
      "type": "string"
    },
    "prev": {
      "href": "string",
      "type": "string"
    },
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}

```

*Antraege*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|antraege|[[Antrag](#schemaantrag)]|false|none|[Diese Resource repräsentiert einen Antrag in Baufi Smart.]|
|_links|[PaginationLinks](#schemapaginationlinks)|false|none|none|

<h2 id="tocSantrag">Antrag</h2>

<a id="schemaantrag"></a>

```json
{
  "angebot": {
    "absicherungen": [
      {
        "abgesicherteRisiken": [
          {
            "abgesichertesRisiko": "TODESFALL",
            "auszahlungsBetrag": 0,
            "auszahlungsTurnus": "EINMALIG",
            "praemienAnteil": 0
          }
        ],
        "gesamtPraemie": 0,
        "praemienZahlungsweise": "EINMALIG",
        "tarifBezeichnung": "string",
        "tarifKennung": "string",
        "versichertePersonId": "string",
        "versicherungsArt": "string",
        "versicherungsNummer": "string",
        "versicherungsZeitraum": {
          "beginn": "2020-02-24",
          "dauerInMonaten": 0,
          "ende": "2020-02-24"
        }
      }
    ],
    "bausparvertraege": [
      {
        "abschlussGebuehr": 0,
        "angebotsHinweisFuerAntragsteller": "string",
        "bausparSumme": 0,
        "einmalzahlung": 0,
        "gesamtLaufzeitInJahren": 0,
        "id": "string",
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparPhase": {
          "guthabenBeiZuteilung": 0,
          "sparBeitragMonatlich": 0,
          "sparPhaseInJahren": 0
        },
        "tarif": "string",
        "tilgungsPhase": {
          "bausparDarlehenSumme": 0,
          "sollZinsNachZuteilung": 0,
          "tilgungsBeitragMonatlich": 0,
          "tilgungsPhaseInJahren": 0
        },
        "typ": "string",
        "vertragsBeginn": "2020-02-24",
        "vertragsNummer": "string",
        "verwaltungsgebuehrenJaehrlich": 0,
        "zuteilungsDatum": "2020-02-24"
      }
    ],
    "beleihungsRechnung": {
      "beleihungsAuslauf": 0,
      "beleihungsWerte": [
        {
          "beleihungsWert": 0,
          "immobilie": {
            "id": "string"
          }
        }
      ],
      "beleihungsWerteSumme": 0,
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      }
    },
    "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
    "darlehen": [
      {
        "auszahlungsBetrag": 0,
        "auszahlungsDatum": "2020-02-24",
        "auszahlungsKurs": 0,
        "bereitstellung": {
          "bereitstellungsZins": 0,
          "bereitstellungsZinsFreieZeitInMonaten": 0
        },
        "darlehensBetrag": 0,
        "darlehensTyp": "ANNUITAETEN_DARLEHEN",
        "detailsZurVerwendung": "string",
        "effektivZins": 0,
        "effektivZinsRelevanteKosten": {
          "beratungsHonorar": 0,
          "grundbuchKosten": 0,
          "sonstigeKosten": 0,
          "tilgungsErsatzProduktKosten": 0,
          "wohnGebaeudeVersicherungsKosten": 0,
          "zinsabsicherungsKosten": 0,
          "zusatzSicherheitsKosten": 0
        },
        "forwardPeriodeInMonaten": 0,
        "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
        "kfwProgramm": "PROGRAMM_124",
        "konditionWurdeManuellAngepasst": true,
        "konditionsAnpassungsBegruendung": "string",
        "laufZeitInJahren": 0,
        "laufzeitInMonaten": 0,
        "maximaleLaufzeitInMonaten": 0,
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "rateMonatlich": 123.34,
        "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
        "sollZins": 2.05,
        "tilgung": {
          "anfaenglicheTilgung": 0,
          "sonderTilgungJaehrlich": 0,
          "tilgungsBeginnAm": "2020-02-24",
          "tilgungsErsatz": {
            "id": "string",
            "typ": "string"
          }
        },
        "tilgungsFreieAnlaufJahre": 0,
        "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
        "zinsBindung": {
          "endetAm": "2020-02-24",
          "jahre": 0,
          "monate": 0,
          "restschuldNachZinsBindungsEnde": 0
        },
        "zinsZahlungsBeginnAm": "2020-02-24"
      }
    ],
    "erzeugtAm": "2020-02-24T11:55:47Z",
    "kennung": "string",
    "machbarkeitsStatus": "MACHBAR",
    "meldungen": [
      {
        "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
        "kreditEntscheider": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "text": "string"
      }
    ],
    "pruefungsErgebnisse": [
      {
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "weitereAngaben": "string"
      }
    ],
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "ansprechpartner": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "antragsNummer": "string",
  "beratung": {
    "art": "PRAESENZ_GESCHAEFT",
    "hinweisFuerProduktAnbieter": "string",
    "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
  },
  "datenKontext": "TEST_MODUS",
  "dokumente": [
    {
      "art": "string",
      "href": "string",
      "name": "string",
      "titel": "string",
      "type": "string"
    }
  ],
  "kreditSachbearbeiter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "status": {
    "ablehnungsgrund": "FINANZIELLE_SITUATION",
    "antragsteller": "BEANTRAGT",
    "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
    "produktAnbieter": "NICHT_BEARBEITET"
  },
  "vermittler": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "zeitpunktDerAnnahme": "2020-02-24T11:55:47Z",
  "zugrundeliegendeDaten": {
    "bankverbindung": {
      "bic": "string",
      "iban": "string",
      "id": "string",
      "kontoinhaberIds": [
        "string"
      ],
      "kontoinhaberName": "string",
      "kreditinstitut": "string"
    },
    "finanzierungsObjekt": {
      "adresse": {
        "hausnummer": "string",
        "ort": "string",
        "postleitzahl": "string",
        "strasse": "string"
      },
      "autostellplaetze": [
        {
          "mieteinnahmenMonatlich": 0,
          "typ": "STELLPLATZ"
        }
      ],
      "bestehendeDarlehen": [
        {
          "abzuloesendeRestschuld": 0,
          "aktuelleRestschuldWennNichtAbzuloesen": 0,
          "darlehensArt": "BAUSPARDARLEHEN",
          "darlehensBetrag": 0,
          "darlehensGeber": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          },
          "darlehensKontonummer": "string",
          "eingetrageneGrundschuld": 0,
          "grundschuldArt": "BRIEF_GRUNDSCHULD",
          "id": "string",
          "laufzeitEnde": "2020-02-24",
          "rateMonatlich": 0,
          "sollZins": 0,
          "sondertilgungZumZinsBindungsEnde": 0,
          "verwendenAls": "ABLOESEN",
          "zinsBindungEndetAm": "2020-02-24"
        }
      ],
      "bewirtschaftungsKostenJaehrlich": 0,
      "bodenRichtwert": 0,
      "bundesland": "BADEN_WUERTTEMBERG",
      "effektivZinsErhoehendeKosten": {
        "anpassen": true,
        "grundbuchEintragungsKostenEinmalig": 0,
        "sonstigeKostenBezeichnung": "string",
        "sonstigeKostenEinmalig": 0,
        "wohnGebaeudeVersicherungsKostenJaehrlich": 0
      },
      "erbbaurecht": {
        "erbbaurecht": true,
        "erbbauzinsJaehrlich": 0,
        "grundstuecksEigentuemer": "ANDERE",
        "laufzeitBisJahr": "string"
      },
      "gebaeude": {
        "anzahlDerGewerbeeinheiten": 0,
        "anzahlDerWohneinheitenImGebaeude": 0,
        "anzahlVollgeschosse": 0,
        "aufbauFinanzierung": true,
        "aufzugVorhanden": true,
        "ausstattung": "EINFACH",
        "baujahr": "2016",
        "bauweise": "FACHWERK_MIT_STROH_LEHM",
        "bezeichnungWohneinheit": "string",
        "dachgeschossAusbau": "FLACHDACH",
        "einliegerwohnungVorhanden": true,
        "geschossLage": "UNTERGESCHOSS",
        "gewerbeflaeche": {
          "gesamtGroesse": 0,
          "vermietungsInformationen": {
            "mieteinnahmenNettoKaltMonatlich": 0,
            "nutzungsArt": "EIGENGENUTZT",
            "vermieteteFlaeche": 0
          }
        },
        "hausAnordnung": "FREISTEHEND",
        "hausTyp": "DOPPELHAUSHAELFTE",
        "istFertighaus": true,
        "kellerausbau": "AUSGEBAUT",
        "kubatur": 0,
        "miteigentumsAnteil": {
          "anteil": 0,
          "gesamt": 0
        },
        "modernisierungsAngaben": {
          "badWc": true,
          "bodenWandTreppe": true,
          "dach": true,
          "fenster": true,
          "heizungZentral": true,
          "modernisierungsGrad": "GERING",
          "modernisierungsJahr": "string",
          "raumaufteilung": true,
          "stromAbwasserHeizkoerper": true,
          "waermedaemmung": true,
          "wurdeModernisiert": true
        },
        "unterkellerung": "NICHT_UNTERKELLERT",
        "wohnflaeche": {
          "gesamtGroesse": 0,
          "vermietungsInformationen": {
            "mieteinnahmenNettoKaltMonatlich": 0,
            "nutzungsArt": "EIGENGENUTZT",
            "vermieteteFlaeche": 0
          }
        },
        "zustand": "SEHR_GUT"
      },
      "grundbuchAngabe": {
        "anmerkungen": "string",
        "bandUndBlatt": "string",
        "flurstuecke": [
          {
            "anteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "flur": "string",
            "flurstuecksNummer": "string",
            "groesse": 0
          }
        ],
        "ort": "string",
        "rechteInAbteilung2": {
          "beschreibung": "string",
          "betrag": 0,
          "vorhanden": true
        }
      },
      "grundstueck": {
        "groesse": 0,
        "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
      },
      "id": "string",
      "keinBaulandFlaecheInQm": 0,
      "marktueblicherKaufpreisProQm": 0,
      "marktwert": 0,
      "objektArt": "GRUNDSTUECK",
      "vergleichsmieteFuerGewerbeflaecheProQm": 0,
      "vergleichsmieteFuerWohnflaecheProQm": 0,
      "verkehrswert": 0,
      "vorlaeufigerVerkehrswert": 0,
      "wohnlage": "GEHOBEN"
    },
    "haushalte": [
      {
        "antragsteller": [
          {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "arbeitserlaubnis": false,
            "arbeitserlaubnisBefristetBis": "2020-02-24",
            "aufenthaltsTitel": "VISUM",
            "aufenthaltsTitelBefristetBis": "2020-02-24",
            "beschaeftigung": {
              "anzahlGehaelterProJahr": 0,
              "arbeitgeber": "string",
              "arbeitgeberInDeutschlandAnsaessig": false,
              "arbeitgeberLand": {
                "isoCountryCode": "string",
                "name": "string"
              },
              "art": "ANGESTELLTER",
              "befristungsStatus": "BEFRISTET",
              "beruf": "string",
              "beschaeftigtSeit": "2020-02-24",
              "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
              "einkommenNettoJaehrlich": 0,
              "einkommenNettoMonatlich": 0,
              "firma": "string",
              "inProbezeit": false,
              "situationNachRenteneintritt": {
                "gesetzlicheRenteMonatlich": 0,
                "privateRenteMonatlich": 0,
                "rentenBeginn": "2020-02-24",
                "sonstigesEinkommenMonatlich": 0
              },
              "taetigkeit": "ALTENPFLEGER"
            },
            "bruttoVorjahresEinkommen": 0,
            "email": "max.mustermann@test.de",
            "externeAntragstellerId": "string",
            "familienstand": "GESCHIEDEN",
            "geburtsdatum": "2020-02-24",
            "geburtsort": "string",
            "guetertrennungVereinbartWennVerheiratet": false,
            "id": "string",
            "inDeutschlandSeit": "2020-02-24",
            "legitimationsDaten": {
              "ausstellendeBehoerde": "string",
              "ausstellungsdatum": "2020-02-24",
              "ausweisArt": "PERSONALAUSWEIS",
              "ausweisArtBeiAndererAusweis": "string",
              "ausweisNummer": "string"
            },
            "nachname": "string",
            "schufaErgebnis": {
              "antragstellerUnbekannt": false,
              "inManuellerNachbehandlung": false,
              "score": "string"
            },
            "staatsangehoerigkeit": {
              "isoCountryCode": "string",
              "name": "string"
            },
            "steuerId": "string",
            "telefonnummer": "string",
            "telefonnummerVorwahl": "string",
            "titel": [
              "DOKTOR"
            ],
            "titelDoktor": true,
            "titelProfessor": true,
            "vorAnschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "vorname": "string",
            "weitereKontaktMoeglichkeiten": "string",
            "wohnhaftSeit": "2020-02-24"
          }
        ],
        "anzahlErwachseneImHaushalt": 0,
        "anzahlKinderNichtImHaushalt": 0,
        "bestehendeImmobilien": [
          {
            "adresse": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "autostellplaetze": [
              {
                "mieteinnahmenMonatlich": 0,
                "typ": "STELLPLATZ"
              }
            ],
            "bestehendeDarlehen": [
              {
                "abzuloesendeRestschuld": 0,
                "aktuelleRestschuldWennNichtAbzuloesen": 0,
                "darlehensArt": "BAUSPARDARLEHEN",
                "darlehensBetrag": 0,
                "darlehensGeber": {
                  "anrede": "FRAU",
                  "anschrift": {
                    "hausnummer": "string",
                    "ort": "string",
                    "postleitzahl": "string",
                    "strasse": "string"
                  },
                  "email": "string",
                  "externePartnerId": "string",
                  "externerKreditSachbearbeiterId": "string",
                  "fax": "string",
                  "firmenNameZusatz": "string",
                  "firmierung": "string",
                  "geburtsdatum": "2020-02-24",
                  "id": "string",
                  "kreditsachbearbeiter": true,
                  "mobilTelefon": "string",
                  "nachname": "string",
                  "partnerId": "string",
                  "produktAnbieterId": "string",
                  "telefonnummer": "string",
                  "vertriebsOrganisation": {
                    "firma": "string",
                    "name": "string",
                    "vertriebsOrganisationsId": "string"
                  },
                  "vorname": "string",
                  "webseite": "string"
                },
                "darlehensKontonummer": "string",
                "eingetrageneGrundschuld": 0,
                "grundschuldArt": "BRIEF_GRUNDSCHULD",
                "id": "string",
                "laufzeitEnde": "2020-02-24",
                "rateMonatlich": 0,
                "sollZins": 0,
                "sondertilgungZumZinsBindungsEnde": 0,
                "zinsBindungEndetAm": "2020-02-24"
              }
            ],
            "bewirtschaftungsKostenJaehrlich": 0,
            "bodenRichtwert": 0,
            "bundesland": "BADEN_WUERTTEMBERG",
            "effektivZinsErhoehendeKosten": {
              "anpassen": true,
              "grundbuchEintragungsKostenEinmalig": 0,
              "sonstigeKostenBezeichnung": "string",
              "sonstigeKostenEinmalig": 0,
              "wohnGebaeudeVersicherungsKostenJaehrlich": 0
            },
            "erbbaurecht": {
              "erbbaurecht": true,
              "erbbauzinsJaehrlich": 0,
              "grundstuecksEigentuemer": "ANDERE",
              "laufzeitBisJahr": "string"
            },
            "gebaeude": {
              "anzahlDerGewerbeeinheiten": 0,
              "anzahlDerWohneinheitenImGebaeude": 0,
              "anzahlVollgeschosse": 0,
              "aufbauFinanzierung": true,
              "aufzugVorhanden": true,
              "ausstattung": "EINFACH",
              "baujahr": "2016",
              "bauweise": "FACHWERK_MIT_STROH_LEHM",
              "bezeichnungWohneinheit": "string",
              "dachgeschossAusbau": "FLACHDACH",
              "einliegerwohnungVorhanden": true,
              "geschossLage": "UNTERGESCHOSS",
              "gewerbeflaeche": {
                "gesamtGroesse": 0,
                "vermietungsInformationen": {
                  "mieteinnahmenNettoKaltMonatlich": 0,
                  "nutzungsArt": "EIGENGENUTZT",
                  "vermieteteFlaeche": 0
                }
              },
              "hausAnordnung": "FREISTEHEND",
              "hausTyp": "DOPPELHAUSHAELFTE",
              "istFertighaus": true,
              "kellerausbau": "AUSGEBAUT",
              "kubatur": 0,
              "miteigentumsAnteil": {
                "anteil": 0,
                "gesamt": 0
              },
              "modernisierungsAngaben": {
                "badWc": true,
                "bodenWandTreppe": true,
                "dach": true,
                "fenster": true,
                "heizungZentral": true,
                "modernisierungsGrad": "GERING",
                "modernisierungsJahr": "string",
                "raumaufteilung": true,
                "stromAbwasserHeizkoerper": true,
                "waermedaemmung": true,
                "wurdeModernisiert": true
              },
              "unterkellerung": "NICHT_UNTERKELLERT",
              "wohnflaeche": {
                "gesamtGroesse": 0,
                "vermietungsInformationen": {
                  "mieteinnahmenNettoKaltMonatlich": 0,
                  "nutzungsArt": "EIGENGENUTZT",
                  "vermieteteFlaeche": 0
                }
              },
              "zustand": "SEHR_GUT"
            },
            "grundbuchAngabe": {
              "anmerkungen": "string",
              "bandUndBlatt": "string",
              "flurstuecke": [
                {
                  "anteil": {
                    "anteil": 0,
                    "gesamt": 0
                  },
                  "flur": "string",
                  "flurstuecksNummer": "string",
                  "groesse": 0
                }
              ],
              "ort": "string",
              "rechteInAbteilung2": {
                "beschreibung": "string",
                "betrag": 0,
                "vorhanden": true
              }
            },
            "grundstueck": {
              "groesse": 0,
              "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
            },
            "id": "string",
            "immobilienEinsatz": "KEIN_EINSATZ",
            "keinBaulandFlaecheInQm": 0,
            "keineBestehendenDarlehenVorhanden": true,
            "marktueblicherKaufpreisProQm": 0,
            "marktwert": 0,
            "maximalEinzusetzenderBetragWennVerkauf": 0,
            "objektArt": "GRUNDSTUECK",
            "vergleichsmieteFuerGewerbeflaecheProQm": 0,
            "vergleichsmieteFuerWohnflaecheProQm": 0,
            "verkehrswert": 0,
            "vorlaeufigerVerkehrswert": 0,
            "wohnlage": "GEHOBEN"
          }
        ],
        "id": "string",
        "kfzAnzahl": 0,
        "kinder": [
          {
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kindergeldWirdBezogen": true,
            "name": "string",
            "unterhaltsEinnahmenBetragMonatlich": 0
          }
        ],
        "lebenshaltungsKostenMonatlich": 0,
        "obligo": {
          "vermoegenOderVerbindlichkeiten": [
            {
              "aktuellerWert": 0,
              "anrechnungFuerBlankoAnteil": 0,
              "bezeichner": "string",
              "kontonummer": "string",
              "vermoegensTyp": "VERMOEGEN"
            }
          ]
        },
        "positionen": {
          "bankUndSparguthaben": [
            {
              "aktuellerWert": 0,
              "ertrag": 0,
              "maximalAufzuloesenderWert": 0,
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "zahlungsTyp": "EINNAHME",
              "zinsertragJaehrlich": 0,
              "zukuenftigeEinnahmen": 0
            }
          ],
          "bausparvertraege": [
            {
              "abschlussGebuehr": 0,
              "aktuellerWert": 0,
              "bausparSumme": 0,
              "einmalzahlung": 0,
              "ertrag": 0,
              "id": "string",
              "maximalAufzuloesenderBetrag": 0,
              "produktAnbieter": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparBeitragMonatlich": 0,
              "tarif": "string",
              "typ": "string",
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "vertragsBeginn": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zahlungsTyp": "EINNAHME",
              "zukuenftigeEinnahmen": 0,
              "zuteilungsDatum": "2020-02-24"
            }
          ],
          "ehegattenUnterhalt": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "einkuenfteAusNebentaetigkeit": [
            {
              "beginnDerNebentaetigkeit": "2020-02-24",
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "kindergeld": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "lebensUndRentenVersicherungen": [
            {
              "id": "string",
              "maximalAufzuloesenderBetrag": 0,
              "praemieMonatlich": 0,
              "rueckkaufsWertAktuell": 0,
              "tarif": "string",
              "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "versicherungsGesellschaft": "string",
              "versicherungsSumme": 0,
              "vertragsBeginn": "2020-02-24",
              "vertragsEnde": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "mietAusgaben": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "entfallenMitFinanzierung": true,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "privateDarlehen": [
            {
              "glaeubiger": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "restschuld": 0,
              "vermoegensTyp": "VERMOEGEN",
              "wirdAbgeloest": true,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "privateKrankenversicherung": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "ratenkredite": [
            {
              "glaeubiger": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "restschuld": 0,
              "vermoegensTyp": "VERMOEGEN",
              "wirdAbgeloest": true,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "sonstigeAusgaben": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "sonstigeEinnahmen": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "sonstigeVerbindlichkeiten": [
            {
              "glaeubiger": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "restschuld": 0,
              "vermoegensTyp": "VERMOEGEN",
              "wirdAbgeloest": true,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "sonstigeVermoegen": [
            {
              "aktuellerWert": 0,
              "ertrag": 0,
              "maximalAufzuloesenderWert": 0,
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "zukuenftigeEinnahmen": 0
            }
          ],
          "sparplaene": [
            {
              "aktuellerWert": 0,
              "beitragMonatlich": 0,
              "ertrag": 0,
              "maximalAufzuloesenderWert": 0,
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "zahlungsTyp": "EINNAHME",
              "zukuenftigeEinnahmen": 0
            }
          ],
          "unbefristeteZusatzRenten": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "unterhaltsVerpflichtungen": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "variableEinkuenfte": [
            {
              "einnahmenMonatlich": 0,
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "versicherungsAusgaben": [
            {
              "ausgabenMonatlich": 0,
              "berechnungsHilfeVermoegen": {
                "betragNachFinanzierung": 0,
                "betragVorFinanzierung": 0
              },
              "zahlungsTyp": "EINNAHME"
            }
          ],
          "wertpapiere": [
            {
              "aktuellerWert": 0,
              "dividendenJaehrlich": 0,
              "ertrag": 0,
              "maximalAufzuloesenderWert": 0,
              "vermoegensEinsatz": "KEIN_EINSATZ",
              "vermoegensTyp": "VERMOEGEN",
              "zahlungsTyp": "EINNAHME",
              "zukuenftigeEinnahmen": 0
            }
          ]
        }
      }
    ],
    "vorhaben": {
      "absicherungswunsch": {
        "id": "string",
        "versicherungsWuensche": [
          {
            "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
            "id": "string",
            "praemienZahlungsweise": "EINMALIG",
            "risikoAbsicherungsWuensche": [
              {
                "abzusicherndesRisiko": "TODESFALL",
                "versicherteRate": 0,
                "versicherungsSumme": 0
              }
            ],
            "versichertePersonId": "string",
            "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
            "versicherungsBeginn": "2020-02-24",
            "versicherungsDauerInMonaten": 0
          }
        ]
      },
      "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
      "externeBausparAngebote": [
        {
          "abschlussGebuehr": 0,
          "angebotsHinweisFuerAntragsteller": "string",
          "bausparSumme": 0,
          "einmalzahlung": 0,
          "id": "string",
          "produktAnbieter": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          },
          "sonderZahlungen": [
            {
              "anzahl": 0,
              "betrag": 0,
              "termin": "2020-02-24",
              "zahlweise": "EINMALIG"
            }
          ],
          "sparPhase": {
            "guthabenBeiZuteilung": 0,
            "sparBeitragMonatlich": 0,
            "sparPhaseInJahren": 0
          },
          "tarif": "string",
          "tilgungsPhase": {
            "bausparDarlehenSumme": 0,
            "sollZinsNachZuteilung": 0,
            "tilgungsBeitragMonatlich": 0,
            "tilgungsPhaseInJahren": 0
          },
          "typ": "string",
          "vertragsBeginn": "2020-02-24",
          "vertragsNummer": "string",
          "verwaltungsgebuehrenJaehrlich": 0,
          "zuteilungsDatum": "2020-02-24"
        }
      ],
      "finanzbedarf": {
        "anzahlTeilzahlungen": 0,
        "aussenAnlagen": 0,
        "bauNebenkosten": 0,
        "beratungsHonorar": 0,
        "bereitsBeglichen": 0,
        "erschliessung": 0,
        "grunderwerbsteuer": 0,
        "grundstueckBereitsBezahlt": true,
        "grundstuecksKaufpreis": 0,
        "herstellung": 0,
        "kapitalBeschaffung": 0,
        "kapitalWirdBeschafft": true,
        "kaufpreis": 0,
        "maklergebuehr": 0,
        "mobiliar": 0,
        "modernisieren": true,
        "modernisierung": 0,
        "notargebuehr": 0,
        "renovierung": 0,
        "sonstigeKosten": 0,
        "zusaetzlichesKapital": 0
      },
      "finanzierungswunsch": {
        "bausparWuensche": [
          {
            "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
            "bausparSummeAbsolut": 0,
            "bausparSummeRelativ": 0,
            "bausparTarif": [
              {
                "id": "string",
                "kurzName": "string",
                "langName": "string",
                "produktAnbieter": "string",
                "riesterFoerderung": true,
                "status": "AKTIV"
              }
            ],
            "bausparTarife": [
              "string"
            ],
            "id": "string",
            "sonderZahlungEinmalig": 0,
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeginn": "2020-02-24",
            "sparBeitragMonatlichAbsolut": 0,
            "sparBeitragMonatlichRelativ": 0,
            "tilgungsBeitragMonatlich": 0,
            "vertragsPartnerIds": [
              "string"
            ],
            "verwendung": "ZINS_ABSICHERUNG",
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "darlehensWuensche": [
          {
            "annuitaetenDarlehen": {
              "auszahlungsDatum": "2020-02-24",
              "bereitstellungsZinsFreieZeitInMonaten": 0,
              "darlehensBetrag": 0,
              "provision": 0,
              "sondertilgungOptionalJaehrlich": 0,
              "tilgungsWunsch": {
                "anfaenglicheTilgung": 0,
                "ausgesetztBerechnet": false,
                "ausgesetztEigenesAngebot": false,
                "bausparWunsch": {
                  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                  "bausparSummeAbsolut": 0,
                  "bausparSummeRelativ": 0,
                  "bausparTarif": [
                    {}
                  ],
                  "bausparTarife": [
                    "string"
                  ],
                  "id": "string",
                  "sonderZahlungEinmalig": 0,
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeginn": "2020-02-24",
                  "sparBeitragMonatlichAbsolut": 0,
                  "sparBeitragMonatlichRelativ": 0,
                  "tilgungsBeitragMonatlich": 0,
                  "vertragsPartnerIds": [
                    "string"
                  ],
                  "verwendung": "ZINS_ABSICHERUNG",
                  "zuteilungsDatum": "2020-02-24"
                },
                "rate": 0,
                "tilgungsBeginn": "2020-02-24",
                "tilgungsErsatzProduktId": "string",
                "volltilgerWennAnnuitaetenOderForward": false
              },
              "zinsBindungInJahren": 0
            },
            "forwardDarlehen": {
              "auszahlungsDatum": "2020-02-24",
              "bereitstellungsZinsFreieZeitInMonaten": 0,
              "darlehensBetrag": 0,
              "provision": 0,
              "sondertilgungOptionalJaehrlich": 0,
              "tilgungsWunsch": {
                "anfaenglicheTilgung": 0,
                "ausgesetztBerechnet": false,
                "ausgesetztEigenesAngebot": false,
                "bausparWunsch": {
                  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                  "bausparSummeAbsolut": 0,
                  "bausparSummeRelativ": 0,
                  "bausparTarif": [
                    {}
                  ],
                  "bausparTarife": [
                    "string"
                  ],
                  "id": "string",
                  "sonderZahlungEinmalig": 0,
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeginn": "2020-02-24",
                  "sparBeitragMonatlichAbsolut": 0,
                  "sparBeitragMonatlichRelativ": 0,
                  "tilgungsBeitragMonatlich": 0,
                  "vertragsPartnerIds": [
                    "string"
                  ],
                  "verwendung": "ZINS_ABSICHERUNG",
                  "zuteilungsDatum": "2020-02-24"
                },
                "rate": 0,
                "tilgungsBeginn": "2020-02-24",
                "tilgungsErsatzProduktId": "string",
                "volltilgerWennAnnuitaetenOderForward": false
              },
              "zinsBindungInJahren": 0
            },
            "id": "string",
            "kfwDarlehen": {
              "darlehensBetrag": 0,
              "kfwEndfaellig": "NEIN",
              "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
              "kfwProgramm": "PROGRAMM_124",
              "laufzeitInJahren": 0,
              "provision": 0,
              "tilgungsWunsch": {
                "anfaenglicheTilgung": 0,
                "ausgesetztBerechnet": false,
                "ausgesetztEigenesAngebot": false,
                "bausparWunsch": {
                  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                  "bausparSummeAbsolut": 0,
                  "bausparSummeRelativ": 0,
                  "bausparTarif": [
                    {}
                  ],
                  "bausparTarife": [
                    "string"
                  ],
                  "id": "string",
                  "sonderZahlungEinmalig": 0,
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeginn": "2020-02-24",
                  "sparBeitragMonatlichAbsolut": 0,
                  "sparBeitragMonatlichRelativ": 0,
                  "tilgungsBeitragMonatlich": 0,
                  "vertragsPartnerIds": [
                    "string"
                  ],
                  "verwendung": "ZINS_ABSICHERUNG",
                  "zuteilungsDatum": "2020-02-24"
                },
                "rate": 0,
                "tilgungsBeginn": "2020-02-24",
                "tilgungsErsatzProduktId": "string",
                "volltilgerWennAnnuitaetenOderForward": false
              },
              "tilgungsfreieAnlaufjahre": 0,
              "zinsBindungInJahren": 0
            },
            "privatDarlehen": {
              "darlehensBetrag": 0,
              "laufzeitInMonaten": 0,
              "provision": 0
            },
            "variablesDarlehen": {
              "darlehensBetrag": 0,
              "provision": 0,
              "tilgungsWunsch": {
                "anfaenglicheTilgung": 0,
                "ausgesetztBerechnet": false,
                "ausgesetztEigenesAngebot": false,
                "bausparWunsch": {
                  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                  "bausparSummeAbsolut": 0,
                  "bausparSummeRelativ": 0,
                  "bausparTarif": [
                    {}
                  ],
                  "bausparTarife": [
                    "string"
                  ],
                  "id": "string",
                  "sonderZahlungEinmalig": 0,
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeginn": "2020-02-24",
                  "sparBeitragMonatlichAbsolut": 0,
                  "sparBeitragMonatlichRelativ": 0,
                  "tilgungsBeitragMonatlich": 0,
                  "vertragsPartnerIds": [
                    "string"
                  ],
                  "verwendung": "ZINS_ABSICHERUNG",
                  "zuteilungsDatum": "2020-02-24"
                },
                "rate": 0,
                "tilgungsBeginn": "2020-02-24",
                "tilgungsErsatzProduktId": "string",
                "volltilgerWennAnnuitaetenOderForward": false
              }
            },
            "zwischenFinanzierung": {
              "darlehensBetrag": 0,
              "detailsZurVerwendung": "string",
              "maximaleLaufzeitInMonaten": 0,
              "provision": 0,
              "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
            }
          }
        ],
        "id": "string"
      },
      "id": "string",
      "nachfinanzierung": true,
      "nachrangigeExterneDarlehen": [
        {
          "darlehensBetrag": 0,
          "darlehensGeber": "string",
          "id": "string",
          "laufzeitEnde": "2020-02-24",
          "rateMonatlich": 0,
          "typ": "ARBEITGEBERDARLEHEN",
          "zinsBindung": {
            "endetAm": "2020-02-24",
            "jahre": 0,
            "monate": 0,
            "restschuldNachZinsBindungsEnde": 0
          }
        }
      ],
      "praeferenzen": {
        "bereitstellungsZinsFreieZeit": {
          "darlehenBenoetigtInMonaten": 0,
          "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
          "zusatzlicheKommentare": "string"
        },
        "bestandteileDerFinanzierung": {
          "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
          "zusatzlicheKommentare": "string"
        },
        "hoeheDerRate": {
          "betrag": 0,
          "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
          "zusatzlicheKommentare": "string"
        },
        "laufzeit": {
          "bisZumJahr": "2016",
          "bisZurRenteImJahr": "2016",
          "inJahren": 0,
          "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
          "zusatzlicheKommentare": "string"
        },
        "sondertilgung": {
          "betragEinmalig": 0,
          "betragJaehrlich": 0,
          "praeferenzAuswahl": "JAEHRLICH",
          "zusatzlicheKommentare": "string"
        },
        "tilgungsSatzWechsel": {
          "mindestensBenoetigt": 0,
          "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
          "zusatzlicheKommentare": "string"
        },
        "weiterePraeferenz": "string",
        "zeitlicherRahmen": {
          "finanzierungszusageBis": "2020-02-24",
          "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
          "zusatzlicheKommentare": "string"
        },
        "zinsBindung": {
          "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
          "zinsBindungBisJahren": 0,
          "zinsBindungVonJahren": 0,
          "zinsBindungZwischenJahren": 0,
          "zusatzlicheKommentare": "string"
        }
      },
      "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
    }
  },
  "_links": {
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}

```

*Antrag*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|angebot|[Angebot](#schemaangebot)|false|none|Das angenommene Angebot, auf dem dieser Antrag basiert|
|ansprechpartner|[Partner](#schemapartner)|false|none|none|
|antragsNummer|string|false|none|Nummer des Antrags auf der Europace Plattform|
|beratung|[Beratung](#schemaberatung)|false|none|Informationen zum Geschäftsabschluss|
|datenKontext|string|false|none|Gibt an, ob es sich um einen Antrag aus dem Testmodus oder Echtgeschäft handelt|
|dokumente|[[Dokument](#schemadokument)]|false|none|Enthält alle Plattformdokumente, freigegebene Dokumente des Vertriebs, sowie die hochgeladenen Dokumente des Produktanbieters. **Aktuell sind nur Selbstauskunft und Kreditentscheidungsinformation enthalten.**|
|kreditSachbearbeiter|[Partner](#schemapartner)|false|none|none|
|produktAnbieter|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|status|[AntragsStatus](#schemaantragsstatus)|false|none|Bearbeitungsfortschritt des Antrags|
|vermittler|[Partner](#schemapartner)|false|none|none|
|zeitpunktDerAnnahme|string(date-time)|false|none|Zeitpunkt, zu dem der Antrag im System erstellt wurde.|
|zugrundeliegendeDaten|[ZugrundeliegendeDaten](#schemazugrundeliegendedaten)|false|none|none|
|_links|[Links](#schemalinks)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|datenKontext|TEST_MODUS|
|datenKontext|ECHT_GESCHAEFT|

<h2 id="tocSantragsstatus">AntragsStatus</h2>

<a id="schemaantragsstatus"></a>

```json
{
  "ablehnungsgrund": "FINANZIELLE_SITUATION",
  "antragsteller": "BEANTRAGT",
  "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
  "produktAnbieter": "NICHT_BEARBEITET"
}

```

*AntragsStatus*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ablehnungsgrund|string|false|none|Ablehnungsgrund des Produktanbieters|
|antragsteller|string|false|none|Willenserklärung des Antragstellers|
|bearbeitungsFortschritt|string|false|none|Bearbeitungsfortschritt des Antrags nach beidseitiger Unterzeichnung|
|produktAnbieter|string|false|none|Willenserklärung des Produktanbieters|

##### Enumerated Values

|Property|Value|
|---|---|
|ablehnungsgrund|FINANZIELLE_SITUATION|
|ablehnungsgrund|NEGATIV_MERKMAL|
|ablehnungsgrund|WERTERMITTLUNG|
|ablehnungsgrund|KRITERIEN|
|ablehnungsgrund|UNTERLAGEN_UNVOLLSTAENDIG|
|ablehnungsgrund|GEGENANGEBOT|
|ablehnungsgrund|KEINE_ANGABE|
|antragsteller|BEANTRAGT|
|antragsteller|UNTERSCHRIEBEN|
|antragsteller|NICHT_ANGENOMMEN|
|antragsteller|WIDERRUFEN|
|bearbeitungsFortschritt|NICHT_VON_PRODUKTANBIETER_BESTAETIGT|
|bearbeitungsFortschritt|VON_PRODUKTANBIETER_BESTAETIGT|
|bearbeitungsFortschritt|FREIGEGEBEN_FUER_SAMMELFORDERUNG|
|bearbeitungsFortschritt|PROVISION_IN_BEARBEITUNG|
|bearbeitungsFortschritt|PROVISON_AN_KUNDENBETREUER_VOLLSTAENDIG_AUSGEZAHLT|
|produktAnbieter|NICHT_BEARBEITET|
|produktAnbieter|UNTERSCHRIEBEN|
|produktAnbieter|ABGELEHNT|
|produktAnbieter|ZURUECKGESTELLT|

<h2 id="tocSantragsteller">Antragsteller</h2>

<a id="schemaantragsteller"></a>

```json
{
  "anrede": "FRAU",
  "anschrift": {
    "hausnummer": "string",
    "ort": "string",
    "postleitzahl": "string",
    "strasse": "string"
  },
  "arbeitserlaubnis": false,
  "arbeitserlaubnisBefristetBis": "2020-02-24",
  "aufenthaltsTitel": "VISUM",
  "aufenthaltsTitelBefristetBis": "2020-02-24",
  "beschaeftigung": {
    "anzahlGehaelterProJahr": 0,
    "arbeitgeber": "string",
    "arbeitgeberInDeutschlandAnsaessig": false,
    "arbeitgeberLand": {
      "isoCountryCode": "string",
      "name": "string"
    },
    "art": "ANGESTELLTER",
    "befristungsStatus": "BEFRISTET",
    "beruf": "string",
    "beschaeftigtSeit": "2020-02-24",
    "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
    "einkommenNettoJaehrlich": 0,
    "einkommenNettoMonatlich": 0,
    "firma": "string",
    "inProbezeit": false,
    "situationNachRenteneintritt": {
      "gesetzlicheRenteMonatlich": 0,
      "privateRenteMonatlich": 0,
      "rentenBeginn": "2020-02-24",
      "sonstigesEinkommenMonatlich": 0
    },
    "taetigkeit": "ALTENPFLEGER"
  },
  "bruttoVorjahresEinkommen": 0,
  "email": "max.mustermann@test.de",
  "externeAntragstellerId": "string",
  "familienstand": "GESCHIEDEN",
  "geburtsdatum": "2020-02-24",
  "geburtsort": "string",
  "guetertrennungVereinbartWennVerheiratet": false,
  "id": "string",
  "inDeutschlandSeit": "2020-02-24",
  "legitimationsDaten": {
    "ausstellendeBehoerde": "string",
    "ausstellungsdatum": "2020-02-24",
    "ausweisArt": "PERSONALAUSWEIS",
    "ausweisArtBeiAndererAusweis": "string",
    "ausweisNummer": "string"
  },
  "nachname": "string",
  "schufaErgebnis": {
    "antragstellerUnbekannt": false,
    "inManuellerNachbehandlung": false,
    "score": "string"
  },
  "staatsangehoerigkeit": {
    "isoCountryCode": "string",
    "name": "string"
  },
  "steuerId": "string",
  "telefonnummer": "string",
  "telefonnummerVorwahl": "string",
  "titel": [
    "DOKTOR"
  ],
  "titelDoktor": true,
  "titelProfessor": true,
  "vorAnschrift": {
    "hausnummer": "string",
    "ort": "string",
    "postleitzahl": "string",
    "strasse": "string"
  },
  "vorname": "string",
  "weitereKontaktMoeglichkeiten": "string",
  "wohnhaftSeit": "2020-02-24"
}

```

*Antragsteller*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anrede|string|false|none|none|
|anschrift|[Postadresse](#schemapostadresse)|false|none|none|
|arbeitserlaubnis|boolean|false|none|wenn keine deutsche Staatsangehörigkeit|
|arbeitserlaubnisBefristetBis|string(date)|false|none|wenn Arbeitserlaubnis befristet|
|aufenthaltsTitel|string|false|none|wenn keine deutsche Staatsangehörigkeit|
|aufenthaltsTitelBefristetBis|string(date)|false|none|wenn Aufenthaltstitel befristet|
|beschaeftigung|[Beschaeftigung](#schemabeschaeftigung)|false|none|none|
|bruttoVorjahresEinkommen|number|false|none|none|
|email|string|false|none|Eine valide Emailadresse|
|externeAntragstellerId|string|false|none|none|
|familienstand|string|false|none|none|
|geburtsdatum|string(date)|false|none|none|
|geburtsort|string|false|none|none|
|guetertrennungVereinbartWennVerheiratet|boolean|false|none|nur wenn verheiratet|
|id|string|false|none|none|
|inDeutschlandSeit|string(date)|false|none|wenn keine deutsche Staatsangehörigkeit|
|legitimationsDaten|[LegitimationsDaten](#schemalegitimationsdaten)|false|none|none|
|nachname|string|false|none|none|
|schufaErgebnis|[SchufaErgebnis](#schemaschufaergebnis)|false|none|none|
|staatsangehoerigkeit|[Staat](#schemastaat)|false|none|none|
|steuerId|string|false|none|none|
|telefonnummer|string|false|none|none|
|telefonnummerVorwahl|string|false|none|none|
|titel|[string]|false|none|none|
|titelDoktor|boolean|false|none|none|
|titelProfessor|boolean|false|none|none|
|vorAnschrift|[Postadresse](#schemapostadresse)|false|none|none|
|vorname|string|false|none|none|
|weitereKontaktMoeglichkeiten|string|false|none|none|
|wohnhaftSeit|string(date)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|anrede|FRAU|
|anrede|HERR|
|aufenthaltsTitel|VISUM|
|aufenthaltsTitel|AUFENTHALTS_ERLAUBNIS|
|aufenthaltsTitel|NIEDERLASSUNGS_ERLAUBNIS|
|aufenthaltsTitel|DAUERAUFENTHALT_EU|
|familienstand|GESCHIEDEN|
|familienstand|GETRENNT_LEBEND|
|familienstand|LEBENSPARTNERSCHAFT|
|familienstand|LEDIG|
|familienstand|VERHEIRATET|
|familienstand|VERWITWET|

<h2 id="tocSarchivierung">Archivierung</h2>

<a id="schemaarchivierung"></a>

```json
{
  "grund": "VORGANG_ERFOLGREICH_ABGESCHLOSSEN",
  "kommentar": "string"
}

```

*Archivierung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|grund|string|false|none|none|
|kommentar|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|grund|VORGANG_ERFOLGREICH_ABGESCHLOSSEN|
|grund|KUNDE_IST_NICHT_MEHR_INTERESSIERT|
|grund|DAS_OBJEKT_IST_WEG|
|grund|OBJEKT_IST_NICHT_MEHR_VERFUEGBAR|
|grund|KUNDE_HAT_EIN_ANDERES_ANGEBOT|
|grund|SCHLECHTER_LEAD_NICHT_ZU_ERREICHEN|
|grund|FINANZIERUNG_IST_NICHT_MACHBAR|

<h2 id="tocSausgabenmonatlich">AusgabenMonatlich</h2>

<a id="schemaausgabenmonatlich"></a>

```json
{
  "ausgabenMonatlich": 0,
  "berechnungsHilfeVermoegen": {
    "betragNachFinanzierung": 0,
    "betragVorFinanzierung": 0
  },
  "zahlungsTyp": "EINNAHME"
}

```

*AusgabenMonatlich*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ausgabenMonatlich|number|false|none|none|
|berechnungsHilfeVermoegen|[BerechnungsHilfeBetrag](#schemaberechnungshilfebetrag)|false|none|none|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|

##### Enumerated Values

|Property|Value|
|---|---|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSautostellplatz">Autostellplatz</h2>

<a id="schemaautostellplatz"></a>

```json
{
  "mieteinnahmenMonatlich": 0,
  "typ": "STELLPLATZ"
}

```

*Autostellplatz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|mieteinnahmenMonatlich|number|false|none|none|
|typ|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|typ|STELLPLATZ|
|typ|CARPORT|
|typ|GARAGE|
|typ|DOPPEL_GARAGE|
|typ|KELLER_GARAGE|
|typ|TIEFGARAGEN_STELLPLATZ|

<h2 id="tocSbankundsparguthaben">BankUndSparguthaben</h2>

<a id="schemabankundsparguthaben"></a>

```json
{
  "aktuellerWert": 0,
  "ertrag": 0,
  "maximalAufzuloesenderWert": 0,
  "vermoegensEinsatz": "KEIN_EINSATZ",
  "vermoegensTyp": "VERMOEGEN",
  "zahlungsTyp": "EINNAHME",
  "zinsertragJaehrlich": 0,
  "zukuenftigeEinnahmen": 0
}

```

*BankUndSparguthaben*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|aktuellerWert|number|false|none|none|
|ertrag|number|false|none|none|
|maximalAufzuloesenderWert|number|false|none|none|
|vermoegensEinsatz|string|false|none|none|
|vermoegensTyp|string|false|none|Redundante Angabe des Vermögenstyp dient als zusätzliches Filterkriterium|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|
|zinsertragJaehrlich|number|false|none|none|
|zukuenftigeEinnahmen|number|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|vermoegensEinsatz|KEIN_EINSATZ|
|vermoegensEinsatz|ABTRETEN|
|vermoegensEinsatz|AUFLOESEN|
|vermoegensTyp|VERMOEGEN|
|vermoegensTyp|VERBINDLICHKEIT|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSbankverbindung">Bankverbindung</h2>

<a id="schemabankverbindung"></a>

```json
{
  "bic": "string",
  "iban": "string",
  "id": "string",
  "kontoinhaberIds": [
    "string"
  ],
  "kontoinhaberName": "string",
  "kreditinstitut": "string"
}

```

*Bankverbindung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bic|string|false|none|none|
|iban|string|false|none|none|
|id|string|false|none|none|
|kontoinhaberIds|[string]|false|none|none|
|kontoinhaberName|string|false|none|none|
|kreditinstitut|string|false|none|none|

<h2 id="tocSbausparangebot">BausparAngebot</h2>

<a id="schemabausparangebot"></a>

```json
{
  "abschlussGebuehr": 0,
  "angebotsHinweisFuerAntragsteller": "string",
  "bausparSumme": 0,
  "einmalzahlung": 0,
  "id": "string",
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "sonderZahlungen": [
    {
      "anzahl": 0,
      "betrag": 0,
      "termin": "2020-02-24",
      "zahlweise": "EINMALIG"
    }
  ],
  "sparPhase": {
    "guthabenBeiZuteilung": 0,
    "sparBeitragMonatlich": 0,
    "sparPhaseInJahren": 0
  },
  "tarif": "string",
  "tilgungsPhase": {
    "bausparDarlehenSumme": 0,
    "sollZinsNachZuteilung": 0,
    "tilgungsBeitragMonatlich": 0,
    "tilgungsPhaseInJahren": 0
  },
  "typ": "string",
  "vertragsBeginn": "2020-02-24",
  "vertragsNummer": "string",
  "verwaltungsgebuehrenJaehrlich": 0,
  "zuteilungsDatum": "2020-02-24"
}

```

*BausparAngebot*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abschlussGebuehr|number|false|none|none|
|angebotsHinweisFuerAntragsteller|string|false|none|nur bei neuen extern berechneten Bausparverträgen und bei Gegenangeboten|
|bausparSumme|number|false|none|none|
|einmalzahlung|number|false|none|none|
|id|string|false|none|none|
|produktAnbieter|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|sonderZahlungen|[[SonderZahlung](#schemasonderzahlung)]|false|none|none|
|sparPhase|[SparPhase](#schemasparphase)|false|none|none|
|tarif|string|false|none|none|
|tilgungsPhase|[TilgungsPhase](#schematilgungsphase)|false|none|none|
|typ|string|false|none|none|
|vertragsBeginn|string(date)|false|none|none|
|vertragsNummer|string|false|none|none|
|verwaltungsgebuehrenJaehrlich|number|false|none|none|
|zuteilungsDatum|string(date)|false|none|none|

<h2 id="tocSbauspartarif">BausparTarif</h2>

<a id="schemabauspartarif"></a>

```json
{
  "id": "string",
  "kurzName": "string",
  "langName": "string",
  "produktAnbieter": "string",
  "riesterFoerderung": true,
  "status": "AKTIV"
}

```

*BausparTarif*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|kurzName|string|false|none|none|
|langName|string|false|none|none|
|produktAnbieter|string|false|none|none|
|riesterFoerderung|boolean|false|none|none|
|status|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|status|AKTIV|
|status|IN_ENTWICKLUNG|
|status|DEAKTIVIERT|

<h2 id="tocSbausparwunsch">BausparWunsch</h2>

<a id="schemabausparwunsch"></a>

```json
{
  "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
  "bausparSummeAbsolut": 0,
  "bausparSummeRelativ": 0,
  "bausparTarif": [
    {
      "id": "string",
      "kurzName": "string",
      "langName": "string",
      "produktAnbieter": "string",
      "riesterFoerderung": true,
      "status": "AKTIV"
    }
  ],
  "bausparTarife": [
    "string"
  ],
  "id": "string",
  "sonderZahlungEinmalig": 0,
  "sonderZahlungen": [
    {
      "anzahl": 0,
      "betrag": 0,
      "termin": "2020-02-24",
      "zahlweise": "EINMALIG"
    }
  ],
  "sparBeginn": "2020-02-24",
  "sparBeitragMonatlichAbsolut": 0,
  "sparBeitragMonatlichRelativ": 0,
  "tilgungsBeitragMonatlich": 0,
  "vertragsPartnerIds": [
    "string"
  ],
  "verwendung": "ZINS_ABSICHERUNG",
  "zuteilungsDatum": "2020-02-24"
}

```

*BausparWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abschlussGebuehrenVerrechnung|string|false|none|none|
|bausparSummeAbsolut|number|false|none|none|
|bausparSummeRelativ|number|false|none|none|
|bausparTarif|[[BausparTarif](#schemabauspartarif)]|false|none|siehe weitere Beschreibung unter Weitere Informationen -> Bezeichnung Bauspartarife|
|bausparTarife|[string]|false|none|Deprecated, Zukünftig sind die Informationen zum gewünschen Tarif unter bausparTarif zu finden.|
|id|string|false|none|none|
|sonderZahlungEinmalig|number|false|none|none|
|sonderZahlungen|[[SonderZahlung](#schemasonderzahlung)]|false|none|none|
|sparBeginn|string(date)|false|none|Der Beginn des Besparens des Bausparvertrags ist frei festlegbar.|
|sparBeitragMonatlichAbsolut|number|false|none|none|
|sparBeitragMonatlichRelativ|number|false|none|none|
|tilgungsBeitragMonatlich|number|false|none|none|
|vertragsPartnerIds|[string]|false|none|none|
|verwendung|string|false|none|none|
|zuteilungsDatum|string(date)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|abschlussGebuehrenVerrechnung|SOFORTZAHLUNG|
|abschlussGebuehrenVerrechnung|VERRECHNUNG|
|verwendung|ZINS_ABSICHERUNG|
|verwendung|TILGUNGS_AUSGESETZT|

<h2 id="tocSbausparvertrag">Bausparvertrag</h2>

<a id="schemabausparvertrag"></a>

```json
{
  "abschlussGebuehr": 0,
  "angebotsHinweisFuerAntragsteller": "string",
  "bausparSumme": 0,
  "einmalzahlung": 0,
  "gesamtLaufzeitInJahren": 0,
  "id": "string",
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "sonderZahlungen": [
    {
      "anzahl": 0,
      "betrag": 0,
      "termin": "2020-02-24",
      "zahlweise": "EINMALIG"
    }
  ],
  "sparPhase": {
    "guthabenBeiZuteilung": 0,
    "sparBeitragMonatlich": 0,
    "sparPhaseInJahren": 0
  },
  "tarif": "string",
  "tilgungsPhase": {
    "bausparDarlehenSumme": 0,
    "sollZinsNachZuteilung": 0,
    "tilgungsBeitragMonatlich": 0,
    "tilgungsPhaseInJahren": 0
  },
  "typ": "string",
  "vertragsBeginn": "2020-02-24",
  "vertragsNummer": "string",
  "verwaltungsgebuehrenJaehrlich": 0,
  "zuteilungsDatum": "2020-02-24"
}

```

*Bausparvertrag*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abschlussGebuehr|number|false|none|none|
|angebotsHinweisFuerAntragsteller|string|false|none|nur bei neuen extern berechneten Bausparverträgen und bei Gegenangeboten|
|bausparSumme|number|false|none|none|
|einmalzahlung|number|false|none|none|
|gesamtLaufzeitInJahren|integer(int32)|false|none|none|
|id|string|false|none|none|
|produktAnbieter|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|sonderZahlungen|[[SonderZahlung](#schemasonderzahlung)]|false|none|none|
|sparPhase|[SparPhase](#schemasparphase)|false|none|none|
|tarif|string|false|none|none|
|tilgungsPhase|[TilgungsPhase](#schematilgungsphase)|false|none|none|
|typ|string|false|none|none|
|vertragsBeginn|string(date)|false|none|none|
|vertragsNummer|string|false|none|none|
|verwaltungsgebuehrenJaehrlich|number|false|none|none|
|zuteilungsDatum|string(date)|false|none|none|

<h2 id="tocSbeleihungsrechnung">BeleihungsRechnung</h2>

<a id="schemabeleihungsrechnung"></a>

```json
{
  "beleihungsAuslauf": 0,
  "beleihungsWerte": [
    {
      "beleihungsWert": 0,
      "immobilie": {
        "id": "string"
      }
    }
  ],
  "beleihungsWerteSumme": 0,
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  }
}

```

*BeleihungsRechnung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|beleihungsAuslauf|number|false|none|Der Beleihungsauslauf aus Sicht des Produktanbieters. Berechnet sich aus dem Verhältnis anerkannter Darlehen zur Summe der anerkannten Beleihungswerte.|
|beleihungsWerte|[[BeleihungsWert](#schemabeleihungswert)]|false|none|Enthält die vom Produktanbieter anerkannten Beleihungswerte|
|beleihungsWerteSumme|number|false|none|Berechnungshilfe: Die Summe aller vom Produktanbieter anerkannten Beleihungswerte|
|produktAnbieter|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|

<h2 id="tocSbeleihungswert">BeleihungsWert</h2>

<a id="schemabeleihungswert"></a>

```json
{
  "beleihungsWert": 0,
  "immobilie": {
    "id": "string"
  }
}

```

*BeleihungsWert*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|beleihungsWert|number|false|none|none|
|immobilie|[ImmobilieVerknuepfung](#schemaimmobilieverknuepfung)|false|none|none|

<h2 id="tocSberatung">Beratung</h2>

<a id="schemaberatung"></a>

```json
{
  "art": "PRAESENZ_GESCHAEFT",
  "hinweisFuerProduktAnbieter": "string",
  "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
}

```

*Beratung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|art|string|false|none|none|
|hinweisFuerProduktAnbieter|string|false|none|none|
|istKundenBetreuerVerkaeuferOderMaklerDerImmobilie|boolean|false|none|Mit diesem Wert wird ausgedrückt, ob der Kundenbetreuer auch der Immobilienmakler ist.|

##### Enumerated Values

|Property|Value|
|---|---|
|art|PRAESENZ_GESCHAEFT|
|art|FERN_ABSATZ_GESCHAEFT|
|art|AUSSER_GESCHAEFTSRAUM_VERTRAG|

<h2 id="tocSberechnungshilfebetrag">BerechnungsHilfeBetrag</h2>

<a id="schemaberechnungshilfebetrag"></a>

```json
{
  "betragNachFinanzierung": 0,
  "betragVorFinanzierung": 0
}

```

*BerechnungsHilfeBetrag*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|betragNachFinanzierung|number|false|none|none|
|betragVorFinanzierung|number|false|none|none|

<h2 id="tocSbereitstellung">Bereitstellung</h2>

<a id="schemabereitstellung"></a>

```json
{
  "bereitstellungsZins": 0,
  "bereitstellungsZinsFreieZeitInMonaten": 0
}

```

*Bereitstellung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bereitstellungsZins|number|false|none|none|
|bereitstellungsZinsFreieZeitInMonaten|integer(int32)|false|none|none|

<h2 id="tocSbereitstellungszinsfreiezeitpraeferenz">BereitstellungsZinsFreieZeitPraeferenz</h2>

<a id="schemabereitstellungszinsfreiezeitpraeferenz"></a>

```json
{
  "darlehenBenoetigtInMonaten": 0,
  "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
  "zusatzlicheKommentare": "string"
}

```

*BereitstellungsZinsFreieZeitPraeferenz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|darlehenBenoetigtInMonaten|integer(int32)|false|none|wenn praeferenzAuswahl == IN_MONATEN|
|praeferenzAuswahl|string|false|none|none|
|zusatzlicheKommentare|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praeferenzAuswahl|MIT_DER_ERSTEN_AUSZAHLUNG|
|praeferenzAuswahl|IN_MONATEN|
|praeferenzAuswahl|NOCH_NICHT_FESTGELEGT|
|praeferenzAuswahl|EGAL|

<h2 id="tocSbeschaeftigung">Beschaeftigung</h2>

<a id="schemabeschaeftigung"></a>

```json
{
  "anzahlGehaelterProJahr": 0,
  "arbeitgeber": "string",
  "arbeitgeberInDeutschlandAnsaessig": false,
  "arbeitgeberLand": {
    "isoCountryCode": "string",
    "name": "string"
  },
  "art": "ANGESTELLTER",
  "befristungsStatus": "BEFRISTET",
  "beruf": "string",
  "beschaeftigtSeit": "2020-02-24",
  "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
  "einkommenNettoJaehrlich": 0,
  "einkommenNettoMonatlich": 0,
  "firma": "string",
  "inProbezeit": false,
  "situationNachRenteneintritt": {
    "gesetzlicheRenteMonatlich": 0,
    "privateRenteMonatlich": 0,
    "rentenBeginn": "2020-02-24",
    "sonstigesEinkommenMonatlich": 0
  },
  "taetigkeit": "ALTENPFLEGER"
}

```

*Beschaeftigung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anzahlGehaelterProJahr|number(double)|false|none|nur bei art==ANGESTELLTER,ARBEITER,BEAMTER|
|arbeitgeber|string|false|none|nur bei art==ANGESTELLTER,ARBEITER,BEAMTER|
|arbeitgeberInDeutschlandAnsaessig|boolean|false|none|nur bei art==ANGESTELLTER,ARBEITER,BEAMTER|
|arbeitgeberLand|[Staat](#schemastaat)|false|none|nur bei arbeitgeberInDeutschlandAnsaessig==false|
|art|string|false|none|none|
|befristungsStatus|string|false|none|nur bei art==ANGESTELLTER,ARBEITER|
|beruf|string|false|none|nur bei art!=RENTNER|
|beschaeftigtSeit|string(date)|false|none|nur bei art==ANGESTELLTER,ARBEITER,BEAMTER,FREIBERUFLER,SELBSTAENDIGER|
|branche|string|false|none|Berufsgruppe des Antragstellers.|
|einkommenNettoJaehrlich|number|false|none|nur bei art==FREIBERUFLER,SELBSTAENDIGER|
|einkommenNettoMonatlich|number|false|none|nur bei art!=FREIBERUFLER,SELBSTAENDIGER|
|firma|string|false|none|nur bei art==FREIBERUFLER,SELBSTAENDIGER|
|inProbezeit|boolean|false|none|nur bei art==ANGESTELLTER,ARBEITER,BEAMTER|
|situationNachRenteneintritt|[SituationNachRenteneintritt](#schemasituationnachrenteneintritt)|false|none|nur bei art!=RENTNER|
|taetigkeit|string|false|none|nur bei art==FREIBERUFLER,SELBSTAENDIGER|

##### Enumerated Values

|Property|Value|
|---|---|
|art|ANGESTELLTER|
|art|ARBEITER|
|art|BEAMTER|
|art|FREIBERUFLER|
|art|SELBSTAENDIGER|
|art|RENTNER|
|art|HAUSFRAU|
|art|ARBEITSLOSER|
|befristungsStatus|BEFRISTET|
|befristungsStatus|UNBEFRISTET|
|branche|LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI|
|branche|BERGBAU_GEWINNUNG_VON_STEINEN_UND_ERDEN|
|branche|VERARBEITENDES_GEWERBE|
|branche|WASSERVERSORGUNG|
|branche|ENERGIEVERSORGUNG|
|branche|BAUGEWERBE|
|branche|HANDEL_INSTANDHALTUNG_VON_KRAFTFAHRZEUGEN|
|branche|VERKEHR_LOGISTIK|
|branche|GASTGEWERBE|
|branche|INFORMATION_KOMMUNIKATION|
|branche|FINANZ_UND_VERSICHERUNGSDIENSTLEISTUNGEN|
|branche|GRUNDSTÜCKS_UND_WOHNUNGSWESEN|
|branche|FREIBERUFLICHE_WISSENSCHAFTLICHE_UND_TECHNISCHE_DIENSTLEISTUNGEN|
|branche|SONSTIGE_WIRTSCHAFTLICHE_DIENSTLEISTUNGEN|
|branche|OEFFENTLICHE_VERWALTUNG_VERTEIDIGUNG_SOZIALVERSICHERUNG|
|branche|ERZIEHUNG_UNTERRICHT|
|branche|GESUNDHEIT_UND_SOZIALWESEN|
|branche|KUNST_UNTERHALTUNG_ERHOLUNG|
|branche|SONSTIGE_DIENSTLEISTUNGEN|
|branche|PRIVATE_HAUSHALTE|
|taetigkeit|ALTENPFLEGER|
|taetigkeit|AMBULANTER_KRANKENPFLEGER|
|taetigkeit|ANWALT|
|taetigkeit|APOTHEKER|
|taetigkeit|ARCHITEKT|
|taetigkeit|ARZT|
|taetigkeit|BESTATTER|
|taetigkeit|DATENSCHUTZBEAUFTRAGTER|
|taetigkeit|DEKORATEUR|
|taetigkeit|DIAETASSISTENT|
|taetigkeit|DOLMETSCHER|
|taetigkeit|EDV_BERATER|
|taetigkeit|ERGOTHERAPEUT|
|taetigkeit|ERNAEHRUNGSBERATER|
|taetigkeit|FOTOGRAF|
|taetigkeit|GEOGRAF|
|taetigkeit|GRAFIKDESIGNER|
|taetigkeit|GRAFIKER|
|taetigkeit|HEBAMME|
|taetigkeit|HEILMASSEUR|
|taetigkeit|HEILPRAKTIKER|
|taetigkeit|HISTORIKER|
|taetigkeit|INFORMATIKER|
|taetigkeit|INGENIEUR|
|taetigkeit|INSOLVENZVERWALTER|
|taetigkeit|JOURNALIST|
|taetigkeit|KLASSISCHER_KONZERTMUSIKER|
|taetigkeit|KONSTRUKTEUR|
|taetigkeit|KRANKENGYMNAST|
|taetigkeit|KRANKENPFLEGER|
|taetigkeit|KRANKENSCHWESTER|
|taetigkeit|LOGOPAEDE|
|taetigkeit|MEDIZINISCH_TECHN_ASSISTENT|
|taetigkeit|NOTAR|
|taetigkeit|OPERNSAENGER|
|taetigkeit|PERSONALBERATER|
|taetigkeit|PHYSIOTHERAPEUT|
|taetigkeit|PSYCHOLOGE|
|taetigkeit|RAUMAUSSTATTER|
|taetigkeit|RUNDFUNKSPRECHER|
|taetigkeit|SACHVERSTAENDIGER|
|taetigkeit|STADTPLANER|
|taetigkeit|STATIKER|
|taetigkeit|STEUERBERATER|
|taetigkeit|TIERARZT|
|taetigkeit|UNTERNEHMENSBERATER|
|taetigkeit|VERMITTLER|
|taetigkeit|WIRTSCH_BUCHPRUEFER_REVISOR|
|taetigkeit|ZAHNARZT|
|taetigkeit|ZAHNTECHNIKER|
|taetigkeit|SONSTIGES|

<h2 id="tocSbestandteilederfinanzierungpraeferenz">BestandteileDerFinanzierungPraeferenz</h2>

<a id="schemabestandteilederfinanzierungpraeferenz"></a>

```json
{
  "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
  "zusatzlicheKommentare": "string"
}

```

*BestandteileDerFinanzierungPraeferenz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|praeferenzAuswahl|string|false|none|none|
|zusatzlicheKommentare|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praeferenzAuswahl|UNKOMPLIZIERTE_FINANZIERUNG|
|praeferenzAuswahl|WEITERE_PRODUKTE|
|praeferenzAuswahl|KONKRETE_VORSTELLUNGEN|
|praeferenzAuswahl|EGAL|

<h2 id="tocSbestehendeimmobilie">BestehendeImmobilie</h2>

<a id="schemabestehendeimmobilie"></a>

```json
{
  "adresse": {
    "hausnummer": "string",
    "ort": "string",
    "postleitzahl": "string",
    "strasse": "string"
  },
  "autostellplaetze": [
    {
      "mieteinnahmenMonatlich": 0,
      "typ": "STELLPLATZ"
    }
  ],
  "bestehendeDarlehen": [
    {
      "abzuloesendeRestschuld": 0,
      "aktuelleRestschuldWennNichtAbzuloesen": 0,
      "darlehensArt": "BAUSPARDARLEHEN",
      "darlehensBetrag": 0,
      "darlehensGeber": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "darlehensKontonummer": "string",
      "eingetrageneGrundschuld": 0,
      "grundschuldArt": "BRIEF_GRUNDSCHULD",
      "id": "string",
      "laufzeitEnde": "2020-02-24",
      "rateMonatlich": 0,
      "sollZins": 0,
      "sondertilgungZumZinsBindungsEnde": 0,
      "zinsBindungEndetAm": "2020-02-24"
    }
  ],
  "bewirtschaftungsKostenJaehrlich": 0,
  "bodenRichtwert": 0,
  "bundesland": "BADEN_WUERTTEMBERG",
  "effektivZinsErhoehendeKosten": {
    "anpassen": true,
    "grundbuchEintragungsKostenEinmalig": 0,
    "sonstigeKostenBezeichnung": "string",
    "sonstigeKostenEinmalig": 0,
    "wohnGebaeudeVersicherungsKostenJaehrlich": 0
  },
  "erbbaurecht": {
    "erbbaurecht": true,
    "erbbauzinsJaehrlich": 0,
    "grundstuecksEigentuemer": "ANDERE",
    "laufzeitBisJahr": "string"
  },
  "gebaeude": {
    "anzahlDerGewerbeeinheiten": 0,
    "anzahlDerWohneinheitenImGebaeude": 0,
    "anzahlVollgeschosse": 0,
    "aufbauFinanzierung": true,
    "aufzugVorhanden": true,
    "ausstattung": "EINFACH",
    "baujahr": "2016",
    "bauweise": "FACHWERK_MIT_STROH_LEHM",
    "bezeichnungWohneinheit": "string",
    "dachgeschossAusbau": "FLACHDACH",
    "einliegerwohnungVorhanden": true,
    "geschossLage": "UNTERGESCHOSS",
    "gewerbeflaeche": {
      "gesamtGroesse": 0,
      "vermietungsInformationen": {
        "mieteinnahmenNettoKaltMonatlich": 0,
        "nutzungsArt": "EIGENGENUTZT",
        "vermieteteFlaeche": 0
      }
    },
    "hausAnordnung": "FREISTEHEND",
    "hausTyp": "DOPPELHAUSHAELFTE",
    "istFertighaus": true,
    "kellerausbau": "AUSGEBAUT",
    "kubatur": 0,
    "miteigentumsAnteil": {
      "anteil": 0,
      "gesamt": 0
    },
    "modernisierungsAngaben": {
      "badWc": true,
      "bodenWandTreppe": true,
      "dach": true,
      "fenster": true,
      "heizungZentral": true,
      "modernisierungsGrad": "GERING",
      "modernisierungsJahr": "string",
      "raumaufteilung": true,
      "stromAbwasserHeizkoerper": true,
      "waermedaemmung": true,
      "wurdeModernisiert": true
    },
    "unterkellerung": "NICHT_UNTERKELLERT",
    "wohnflaeche": {
      "gesamtGroesse": 0,
      "vermietungsInformationen": {
        "mieteinnahmenNettoKaltMonatlich": 0,
        "nutzungsArt": "EIGENGENUTZT",
        "vermieteteFlaeche": 0
      }
    },
    "zustand": "SEHR_GUT"
  },
  "grundbuchAngabe": {
    "anmerkungen": "string",
    "bandUndBlatt": "string",
    "flurstuecke": [
      {
        "anteil": {
          "anteil": 0,
          "gesamt": 0
        },
        "flur": "string",
        "flurstuecksNummer": "string",
        "groesse": 0
      }
    ],
    "ort": "string",
    "rechteInAbteilung2": {
      "beschreibung": "string",
      "betrag": 0,
      "vorhanden": true
    }
  },
  "grundstueck": {
    "groesse": 0,
    "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
  },
  "id": "string",
  "immobilienEinsatz": "KEIN_EINSATZ",
  "keinBaulandFlaecheInQm": 0,
  "keineBestehendenDarlehenVorhanden": true,
  "marktueblicherKaufpreisProQm": 0,
  "marktwert": 0,
  "maximalEinzusetzenderBetragWennVerkauf": 0,
  "objektArt": "GRUNDSTUECK",
  "vergleichsmieteFuerGewerbeflaecheProQm": 0,
  "vergleichsmieteFuerWohnflaecheProQm": 0,
  "verkehrswert": 0,
  "vorlaeufigerVerkehrswert": 0,
  "wohnlage": "GEHOBEN"
}

```

*BestehendeImmobilie*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|adresse|[Postadresse](#schemapostadresse)|false|none|none|
|autostellplaetze|[[Autostellplatz](#schemaautostellplatz)]|false|none|none|
|bestehendeDarlehen|[[BestehendesDarlehen](#schemabestehendesdarlehen)]|false|none|none|
|bewirtschaftungsKostenJaehrlich|number|false|none|none|
|bodenRichtwert|number|false|none|none|
|bundesland|string|false|none|none|
|effektivZinsErhoehendeKosten|[EffektivZinsErhoehendeKosten](#schemaeffektivzinserhoehendekosten)|false|none|none|
|erbbaurecht|[Erbbaurecht](#schemaerbbaurecht)|false|none|none|
|gebaeude|[Gebaeude](#schemagebaeude)|false|none|none|
|grundbuchAngabe|[GrundbuchAngabe](#schemagrundbuchangabe)|false|none|none|
|grundstueck|[Grundstueck](#schemagrundstueck)|false|none|none|
|id|string|false|none|none|
|immobilienEinsatz|string|false|none|none|
|keinBaulandFlaecheInQm|number|false|none|none|
|keineBestehendenDarlehenVorhanden|boolean|false|none|none|
|marktueblicherKaufpreisProQm|number|false|none|none|
|marktwert|number|false|none|Nur relevant bei Finanzbedarf AnschlussFinanzierung, Modernisierung und Kapitalbeschaffung.|
|maximalEinzusetzenderBetragWennVerkauf|number|false|none|none|
|objektArt|string|false|none|none|
|vergleichsmieteFuerGewerbeflaecheProQm|number|false|none|none|
|vergleichsmieteFuerWohnflaecheProQm|number|false|none|none|
|verkehrswert|number|false|none|Hat den selben Inhalt wie das Feld marktwert. (Wird in v3 nicht mehr enthalten sein)|
|vorlaeufigerVerkehrswert|number|false|none|Diese Angabe ist produktanbieterspezifisch, sie wird nicht von allen Produktanbietern bei der Angebotsermittlung berücksichtigt.|
|wohnlage|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|bundesland|BADEN_WUERTTEMBERG|
|bundesland|BAYERN|
|bundesland|BERLIN|
|bundesland|BRANDENBURG|
|bundesland|BREMEN|
|bundesland|HAMBURG|
|bundesland|HESSEN|
|bundesland|MECKLENBURG_VORPOMMERN|
|bundesland|NIEDERSACHSEN|
|bundesland|NORDRHEIN_WESTFALEN|
|bundesland|RHEINLAND_PFALZ|
|bundesland|SAARLAND|
|bundesland|SACHSEN|
|bundesland|SACHSEN_ANHALT|
|bundesland|SCHLESWIG_HOLSTEIN|
|bundesland|THUERINGEN|
|immobilienEinsatz|KEIN_EINSATZ|
|immobilienEinsatz|VERKAUFEN|
|immobilienEinsatz|ALS_ZUSATZSICHERHEIT|
|objektArt|GRUNDSTUECK|
|objektArt|EIGENTUMSWOHNUNG|
|objektArt|HAUS|
|wohnlage|GEHOBEN|
|wohnlage|MITTEL|
|wohnlage|EINFACH|

<h2 id="tocSbestehenderbausparvertrag">BestehenderBausparvertrag</h2>

<a id="schemabestehenderbausparvertrag"></a>

```json
{
  "abschlussGebuehr": 0,
  "aktuellerWert": 0,
  "bausparSumme": 0,
  "einmalzahlung": 0,
  "ertrag": 0,
  "id": "string",
  "maximalAufzuloesenderBetrag": 0,
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "sonderZahlungen": [
    {
      "anzahl": 0,
      "betrag": 0,
      "termin": "2020-02-24",
      "zahlweise": "EINMALIG"
    }
  ],
  "sparBeitragMonatlich": 0,
  "tarif": "string",
  "typ": "string",
  "vermoegensEinsatz": "KEIN_EINSATZ",
  "vermoegensTyp": "VERMOEGEN",
  "vertragsBeginn": "2020-02-24",
  "vertragsNummer": "string",
  "verwaltungsgebuehrenJaehrlich": 0,
  "zahlungsTyp": "EINNAHME",
  "zukuenftigeEinnahmen": 0,
  "zuteilungsDatum": "2020-02-24"
}

```

*BestehenderBausparvertrag*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abschlussGebuehr|number|false|none|none|
|aktuellerWert|number|false|none|none|
|bausparSumme|number|false|none|none|
|einmalzahlung|number|false|none|none|
|ertrag|number|false|none|none|
|id|string|false|none|none|
|maximalAufzuloesenderBetrag|number|false|none|none|
|produktAnbieter|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|sonderZahlungen|[[SonderZahlung](#schemasonderzahlung)]|false|none|none|
|sparBeitragMonatlich|number|false|none|none|
|tarif|string|false|none|none|
|typ|string|false|none|none|
|vermoegensEinsatz|string|false|none|none|
|vermoegensTyp|string|false|none|Redundante Angabe des Vermögenstyp dient als zusätzliches Filterkriterium|
|vertragsBeginn|string(date)|false|none|none|
|vertragsNummer|string|false|none|none|
|verwaltungsgebuehrenJaehrlich|number|false|none|none|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|
|zukuenftigeEinnahmen|number|false|none|none|
|zuteilungsDatum|string(date)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|vermoegensEinsatz|KEIN_EINSATZ|
|vermoegensEinsatz|ABTRETEN|
|vermoegensEinsatz|AUFLOESEN|
|vermoegensTyp|VERMOEGEN|
|vermoegensTyp|VERBINDLICHKEIT|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSbestehendesdarlehen">BestehendesDarlehen</h2>

<a id="schemabestehendesdarlehen"></a>

```json
{
  "abzuloesendeRestschuld": 0,
  "aktuelleRestschuldWennNichtAbzuloesen": 0,
  "darlehensArt": "BAUSPARDARLEHEN",
  "darlehensBetrag": 0,
  "darlehensGeber": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "darlehensKontonummer": "string",
  "eingetrageneGrundschuld": 0,
  "grundschuldArt": "BRIEF_GRUNDSCHULD",
  "id": "string",
  "laufzeitEnde": "2020-02-24",
  "rateMonatlich": 0,
  "sollZins": 0,
  "sondertilgungZumZinsBindungsEnde": 0,
  "zinsBindungEndetAm": "2020-02-24"
}

```

*BestehendesDarlehen*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abzuloesendeRestschuld|number|false|none|none|
|aktuelleRestschuldWennNichtAbzuloesen|number|false|none|none|
|darlehensArt|string|false|none|Neue Ausprägungen können kurzfristig hinzukommen. Der Client muss daher mit unbekannten Werten umgehen können.|
|darlehensBetrag|number|false|none|none|
|darlehensGeber|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|darlehensKontonummer|string|false|none|none|
|eingetrageneGrundschuld|number|false|none|none|
|grundschuldArt|string|false|none|none|
|id|string|false|none|none|
|laufzeitEnde|string(date)|false|none|none|
|rateMonatlich|number|false|none|none|
|sollZins|number|false|none|none|
|sondertilgungZumZinsBindungsEnde|number|false|none|für Prolongation, d.h. technisch: Vorhaben verwendungszweck==ANSCHLUSSFINANZIERUNG|
|zinsBindungEndetAm|string(date)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|darlehensArt|BAUSPARDARLEHEN|
|darlehensArt|FOERDERDARLEHEN|
|darlehensArt|IMMOBILIENDARLEHEN|
|darlehensArt|PRIVATDARLEHEN|
|darlehensArt|SONSTIGES_DARLEHEN|
|grundschuldArt|BRIEF_GRUNDSCHULD|
|grundschuldArt|BUCH_GRUNDSCHULD|

<h2 id="tocSbestehendesdarlehendesfinanzierungsobjekts">BestehendesDarlehenDesFinanzierungsObjekts</h2>

<a id="schemabestehendesdarlehendesfinanzierungsobjekts"></a>

```json
{
  "abzuloesendeRestschuld": 0,
  "aktuelleRestschuldWennNichtAbzuloesen": 0,
  "darlehensArt": "BAUSPARDARLEHEN",
  "darlehensBetrag": 0,
  "darlehensGeber": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "darlehensKontonummer": "string",
  "eingetrageneGrundschuld": 0,
  "grundschuldArt": "BRIEF_GRUNDSCHULD",
  "id": "string",
  "laufzeitEnde": "2020-02-24",
  "rateMonatlich": 0,
  "sollZins": 0,
  "sondertilgungZumZinsBindungsEnde": 0,
  "verwendenAls": "ABLOESEN",
  "zinsBindungEndetAm": "2020-02-24"
}

```

*BestehendesDarlehenDesFinanzierungsObjekts*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abzuloesendeRestschuld|number|false|none|none|
|aktuelleRestschuldWennNichtAbzuloesen|number|false|none|none|
|darlehensArt|string|false|none|Neue Ausprägungen können kurzfristig hinzukommen. Der Client muss daher mit unbekannten Werten umgehen können.|
|darlehensBetrag|number|false|none|none|
|darlehensGeber|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|darlehensKontonummer|string|false|none|none|
|eingetrageneGrundschuld|number|false|none|none|
|grundschuldArt|string|false|none|none|
|id|string|false|none|none|
|laufzeitEnde|string(date)|false|none|none|
|rateMonatlich|number|false|none|none|
|sollZins|number|false|none|none|
|sondertilgungZumZinsBindungsEnde|number|false|none|für Prolongation, d.h. technisch: Vorhaben verwendungszweck==ANSCHLUSSFINANZIERUNG|
|verwendenAls|string|false|none|Beschreibt wie das Darlehen im Zusammenhang mit dem Vorhaben, behandelt werden soll.|
|zinsBindungEndetAm|string(date)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|darlehensArt|BAUSPARDARLEHEN|
|darlehensArt|FOERDERDARLEHEN|
|darlehensArt|IMMOBILIENDARLEHEN|
|darlehensArt|PRIVATDARLEHEN|
|darlehensArt|SONSTIGES_DARLEHEN|
|grundschuldArt|BRIEF_GRUNDSCHULD|
|grundschuldArt|BUCH_GRUNDSCHULD|
|verwendenAls|ABLOESEN|
|verwendenAls|TRITT_IM_RANG_ZURUECK|
|verwendenAls|TRITT_NICHT_IM_RANG_ZURUECK|

<h2 id="tocScharsequence">CharSequence</h2>

<a id="schemacharsequence"></a>

```json
{}

```

*CharSequence*

#### Properties

*None*

<h2 id="tocSdarlehen">Darlehen</h2>

<a id="schemadarlehen"></a>

```json
{
  "auszahlungsBetrag": 0,
  "auszahlungsDatum": "2020-02-24",
  "auszahlungsKurs": 0,
  "bereitstellung": {
    "bereitstellungsZins": 0,
    "bereitstellungsZinsFreieZeitInMonaten": 0
  },
  "darlehensBetrag": 0,
  "darlehensTyp": "ANNUITAETEN_DARLEHEN",
  "detailsZurVerwendung": "string",
  "effektivZins": 0,
  "effektivZinsRelevanteKosten": {
    "beratungsHonorar": 0,
    "grundbuchKosten": 0,
    "sonstigeKosten": 0,
    "tilgungsErsatzProduktKosten": 0,
    "wohnGebaeudeVersicherungsKosten": 0,
    "zinsabsicherungsKosten": 0,
    "zusatzSicherheitsKosten": 0
  },
  "forwardPeriodeInMonaten": 0,
  "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
  "kfwProgramm": "PROGRAMM_124",
  "konditionWurdeManuellAngepasst": true,
  "konditionsAnpassungsBegruendung": "string",
  "laufZeitInJahren": 0,
  "laufzeitInMonaten": 0,
  "maximaleLaufzeitInMonaten": 0,
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "rateMonatlich": 123.34,
  "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
  "sollZins": 2.05,
  "tilgung": {
    "anfaenglicheTilgung": 0,
    "sonderTilgungJaehrlich": 0,
    "tilgungsBeginnAm": "2020-02-24",
    "tilgungsErsatz": {
      "id": "string",
      "typ": "string"
    }
  },
  "tilgungsFreieAnlaufJahre": 0,
  "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
  "zinsBindung": {
    "endetAm": "2020-02-24",
    "jahre": 0,
    "monate": 0,
    "restschuldNachZinsBindungsEnde": 0
  },
  "zinsZahlungsBeginnAm": "2020-02-24"
}

```

*Darlehen*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|auszahlungsBetrag|number|false|none|none|
|auszahlungsDatum|string(date)|false|none|nur bei darlehensTyp IN [FORWARD_DARLEHEN, ANNUITAETEN_DARLEHEN]|
|auszahlungsKurs|number|false|none|none|
|bereitstellung|[Bereitstellung](#schemabereitstellung)|false|none|nicht bei darlehensTyp==PRIVAT_DARLEHEN|
|darlehensBetrag|number|false|none|none|
|darlehensTyp|string|false|none|none|
|detailsZurVerwendung|string|false|none|nur bei darlehensTyp==ZWISCHEN_FINANZIERUNG|
|effektivZins|number|false|none|none|
|effektivZinsRelevanteKosten|[EffektivZinsKosten](#schemaeffektivzinskosten)|false|none|none|
|forwardPeriodeInMonaten|integer(int32)|false|none|nur bei darlehensTyp==FORWARD_DARLEHEN|
|kfwEnergieEffizienzStandard|string|false|none|nur bei darlehensTyp==KFW_DARLEHEN. Nur bei KfW-Programm 153 relevant. Bei neuen Energieeffizienzstandards können auch weitere Werte zulässig werden.|
|kfwProgramm|string|false|none|Bei neu aufgelegten KfW-Programmen können auch weitere Werte zulässig werden.|
|konditionWurdeManuellAngepasst|boolean|false|none|none|
|konditionsAnpassungsBegruendung|string|false|none|Begründung, wenn die Kondition angepasst wurde|
|laufZeitInJahren|integer(int32)|false|none|none|
|laufzeitInMonaten|integer(int32)|false|none|nur bei darlehensTyp==PRIVAT_DARLEHEN|
|maximaleLaufzeitInMonaten|integer(int32)|false|none|nur bei darlehensTyp==ZWISCHEN_FINANZIERUNG|
|produktAnbieter|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|rateMonatlich|number|false|none|Die monatliche Rate in Euro|
|rateMonatlichInDerTilgungsfreienAnlaufzeit|number|false|none|nur bei darlehensTyp==KFW_DARLEHEN|
|sollZins|number|false|none|Der Sollzinssatz in Prozent|
|tilgung|[Tilgung](#schematilgung)|false|none|nicht bei darlehensTyp==ZWISCHEN_FINANZIERUNG|
|tilgungsFreieAnlaufJahre|integer(int32)|false|none|nur bei darlehensTyp==KFW_DARLEHEN|
|verwendungszweck|string|false|none|nur bei darlehensTyp==ZWISCHEN_FINANZIERUNG|
|zinsBindung|[ZinsBindung](#schemazinsbindung)|false|none|nicht bei darlehensTyp IN [VARIABLES_DARLEHEN,ZWISCHEN_FINANZIERUNG]|
|zinsZahlungsBeginnAm|string(date)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|darlehensTyp|ANNUITAETEN_DARLEHEN|
|darlehensTyp|FORWARD_DARLEHEN|
|darlehensTyp|KFW_DARLEHEN|
|darlehensTyp|PRIVAT_DARLEHEN|
|darlehensTyp|ZWISCHEN_FINANZIERUNG|
|darlehensTyp|VARIABLES_DARLEHEN|
|kfwEnergieEffizienzStandard|STANDARD_40_PLUS|
|kfwEnergieEffizienzStandard|STANDARD_40|
|kfwEnergieEffizienzStandard|STANDARD_55|
|kfwEnergieEffizienzStandard|STANDARD_70|
|kfwProgramm|PROGRAMM_124|
|kfwProgramm|PROGRAMM_141|
|kfwProgramm|PROGRAMM_151|
|kfwProgramm|PROGRAMM_152|
|kfwProgramm|PROGRAMM_153|
|kfwProgramm|PROGRAMM_155|
|kfwProgramm|PROGRAMM_159|
|kfwProgramm|PROGRAMM_167|
|verwendungszweck|VORFINANZIERUNG_OEFFENTLICHER_MITTEL|
|verwendungszweck|VERKAUF_EINES_ANDEREN_OBJEKTS|
|verwendungszweck|SONSTIGE_VERWENDUNG|

<h2 id="tocSdarlehenswunsch">DarlehensWunsch</h2>

<a id="schemadarlehenswunsch"></a>

```json
{
  "annuitaetenDarlehen": {
    "auszahlungsDatum": "2020-02-24",
    "bereitstellungsZinsFreieZeitInMonaten": 0,
    "darlehensBetrag": 0,
    "provision": 0,
    "sondertilgungOptionalJaehrlich": 0,
    "tilgungsWunsch": {
      "anfaenglicheTilgung": 0,
      "ausgesetztBerechnet": false,
      "ausgesetztEigenesAngebot": false,
      "bausparWunsch": {
        "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
        "bausparSummeAbsolut": 0,
        "bausparSummeRelativ": 0,
        "bausparTarif": [
          {
            "id": "string",
            "kurzName": "string",
            "langName": "string",
            "produktAnbieter": "string",
            "riesterFoerderung": true,
            "status": "AKTIV"
          }
        ],
        "bausparTarife": [
          "string"
        ],
        "id": "string",
        "sonderZahlungEinmalig": 0,
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparBeginn": "2020-02-24",
        "sparBeitragMonatlichAbsolut": 0,
        "sparBeitragMonatlichRelativ": 0,
        "tilgungsBeitragMonatlich": 0,
        "vertragsPartnerIds": [
          "string"
        ],
        "verwendung": "ZINS_ABSICHERUNG",
        "zuteilungsDatum": "2020-02-24"
      },
      "rate": 0,
      "tilgungsBeginn": "2020-02-24",
      "tilgungsErsatzProduktId": "string",
      "volltilgerWennAnnuitaetenOderForward": false
    },
    "zinsBindungInJahren": 0
  },
  "forwardDarlehen": {
    "auszahlungsDatum": "2020-02-24",
    "bereitstellungsZinsFreieZeitInMonaten": 0,
    "darlehensBetrag": 0,
    "provision": 0,
    "sondertilgungOptionalJaehrlich": 0,
    "tilgungsWunsch": {
      "anfaenglicheTilgung": 0,
      "ausgesetztBerechnet": false,
      "ausgesetztEigenesAngebot": false,
      "bausparWunsch": {
        "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
        "bausparSummeAbsolut": 0,
        "bausparSummeRelativ": 0,
        "bausparTarif": [
          {
            "id": "string",
            "kurzName": "string",
            "langName": "string",
            "produktAnbieter": "string",
            "riesterFoerderung": true,
            "status": "AKTIV"
          }
        ],
        "bausparTarife": [
          "string"
        ],
        "id": "string",
        "sonderZahlungEinmalig": 0,
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparBeginn": "2020-02-24",
        "sparBeitragMonatlichAbsolut": 0,
        "sparBeitragMonatlichRelativ": 0,
        "tilgungsBeitragMonatlich": 0,
        "vertragsPartnerIds": [
          "string"
        ],
        "verwendung": "ZINS_ABSICHERUNG",
        "zuteilungsDatum": "2020-02-24"
      },
      "rate": 0,
      "tilgungsBeginn": "2020-02-24",
      "tilgungsErsatzProduktId": "string",
      "volltilgerWennAnnuitaetenOderForward": false
    },
    "zinsBindungInJahren": 0
  },
  "id": "string",
  "kfwDarlehen": {
    "darlehensBetrag": 0,
    "kfwEndfaellig": "NEIN",
    "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
    "kfwProgramm": "PROGRAMM_124",
    "laufzeitInJahren": 0,
    "provision": 0,
    "tilgungsWunsch": {
      "anfaenglicheTilgung": 0,
      "ausgesetztBerechnet": false,
      "ausgesetztEigenesAngebot": false,
      "bausparWunsch": {
        "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
        "bausparSummeAbsolut": 0,
        "bausparSummeRelativ": 0,
        "bausparTarif": [
          {
            "id": "string",
            "kurzName": "string",
            "langName": "string",
            "produktAnbieter": "string",
            "riesterFoerderung": true,
            "status": "AKTIV"
          }
        ],
        "bausparTarife": [
          "string"
        ],
        "id": "string",
        "sonderZahlungEinmalig": 0,
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparBeginn": "2020-02-24",
        "sparBeitragMonatlichAbsolut": 0,
        "sparBeitragMonatlichRelativ": 0,
        "tilgungsBeitragMonatlich": 0,
        "vertragsPartnerIds": [
          "string"
        ],
        "verwendung": "ZINS_ABSICHERUNG",
        "zuteilungsDatum": "2020-02-24"
      },
      "rate": 0,
      "tilgungsBeginn": "2020-02-24",
      "tilgungsErsatzProduktId": "string",
      "volltilgerWennAnnuitaetenOderForward": false
    },
    "tilgungsfreieAnlaufjahre": 0,
    "zinsBindungInJahren": 0
  },
  "privatDarlehen": {
    "darlehensBetrag": 0,
    "laufzeitInMonaten": 0,
    "provision": 0
  },
  "variablesDarlehen": {
    "darlehensBetrag": 0,
    "provision": 0,
    "tilgungsWunsch": {
      "anfaenglicheTilgung": 0,
      "ausgesetztBerechnet": false,
      "ausgesetztEigenesAngebot": false,
      "bausparWunsch": {
        "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
        "bausparSummeAbsolut": 0,
        "bausparSummeRelativ": 0,
        "bausparTarif": [
          {
            "id": "string",
            "kurzName": "string",
            "langName": "string",
            "produktAnbieter": "string",
            "riesterFoerderung": true,
            "status": "AKTIV"
          }
        ],
        "bausparTarife": [
          "string"
        ],
        "id": "string",
        "sonderZahlungEinmalig": 0,
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparBeginn": "2020-02-24",
        "sparBeitragMonatlichAbsolut": 0,
        "sparBeitragMonatlichRelativ": 0,
        "tilgungsBeitragMonatlich": 0,
        "vertragsPartnerIds": [
          "string"
        ],
        "verwendung": "ZINS_ABSICHERUNG",
        "zuteilungsDatum": "2020-02-24"
      },
      "rate": 0,
      "tilgungsBeginn": "2020-02-24",
      "tilgungsErsatzProduktId": "string",
      "volltilgerWennAnnuitaetenOderForward": false
    }
  },
  "zwischenFinanzierung": {
    "darlehensBetrag": 0,
    "detailsZurVerwendung": "string",
    "maximaleLaufzeitInMonaten": 0,
    "provision": 0,
    "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
  }
}

```

*DarlehensWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|annuitaetenDarlehen|[AnnuitaetenDarlehensWunsch](#schemaannuitaetendarlehenswunsch)|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|forwardDarlehen|[ForwardDarlehensWunsch](#schemaforwarddarlehenswunsch)|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|id|string|false|none|none|
|kfwDarlehen|[KfwDarlehensWunsch](#schemakfwdarlehenswunsch)|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|privatDarlehen|[PrivatDarlehensWunsch](#schemaprivatdarlehenswunsch)|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|variablesDarlehen|[VariablesDarlehensWunsch](#schemavariablesdarlehenswunsch)|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|zwischenFinanzierung|[ZwischenFinanzierungsWunsch](#schemazwischenfinanzierungswunsch)|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|

<h2 id="tocSdokument">Dokument</h2>

<a id="schemadokument"></a>

```json
{
  "art": "string",
  "href": "string",
  "name": "string",
  "titel": "string",
  "type": "string"
}

```

*Dokument*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|art|string|false|none|ist nicht immer vorhanden|
|href|string|false|none|none|
|name|string|false|none|none|
|titel|string|false|none|Name des Dokuments|
|type|string|false|none|none|

<h2 id="tocSeffektivzinserhoehendekosten">EffektivZinsErhoehendeKosten</h2>

<a id="schemaeffektivzinserhoehendekosten"></a>

```json
{
  "anpassen": true,
  "grundbuchEintragungsKostenEinmalig": 0,
  "sonstigeKostenBezeichnung": "string",
  "sonstigeKostenEinmalig": 0,
  "wohnGebaeudeVersicherungsKostenJaehrlich": 0
}

```

*EffektivZinsErhoehendeKosten*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anpassen|boolean|false|none|none|
|grundbuchEintragungsKostenEinmalig|number|false|none|none|
|sonstigeKostenBezeichnung|string|false|none|none|
|sonstigeKostenEinmalig|number|false|none|none|
|wohnGebaeudeVersicherungsKostenJaehrlich|number|false|none|none|

<h2 id="tocSeffektivzinskosten">EffektivZinsKosten</h2>

<a id="schemaeffektivzinskosten"></a>

```json
{
  "beratungsHonorar": 0,
  "grundbuchKosten": 0,
  "sonstigeKosten": 0,
  "tilgungsErsatzProduktKosten": 0,
  "wohnGebaeudeVersicherungsKosten": 0,
  "zinsabsicherungsKosten": 0,
  "zusatzSicherheitsKosten": 0
}

```

*EffektivZinsKosten*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|beratungsHonorar|number|false|none|none|
|grundbuchKosten|number|false|none|none|
|sonstigeKosten|number|false|none|none|
|tilgungsErsatzProduktKosten|number|false|none|none|
|wohnGebaeudeVersicherungsKosten|number|false|none|none|
|zinsabsicherungsKosten|number|false|none|none|
|zusatzSicherheitsKosten|number|false|none|none|

<h2 id="tocSeinkuenfteausnebentaetigkeit">EinkuenfteAusNebentaetigkeit</h2>

<a id="schemaeinkuenfteausnebentaetigkeit"></a>

```json
{
  "beginnDerNebentaetigkeit": "2020-02-24",
  "einnahmenMonatlich": 0,
  "zahlungsTyp": "EINNAHME"
}

```

*EinkuenfteAusNebentaetigkeit*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|beginnDerNebentaetigkeit|string(date)|false|none|none|
|einnahmenMonatlich|number|false|none|none|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|

##### Enumerated Values

|Property|Value|
|---|---|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSeinnahmenmonatlich">EinnahmenMonatlich</h2>

<a id="schemaeinnahmenmonatlich"></a>

```json
{
  "einnahmenMonatlich": 0,
  "zahlungsTyp": "EINNAHME"
}

```

*EinnahmenMonatlich*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|einnahmenMonatlich|number|false|none|none|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|

##### Enumerated Values

|Property|Value|
|---|---|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSerbbaurecht">Erbbaurecht</h2>

<a id="schemaerbbaurecht"></a>

```json
{
  "erbbaurecht": true,
  "erbbauzinsJaehrlich": 0,
  "grundstuecksEigentuemer": "ANDERE",
  "laufzeitBisJahr": "string"
}

```

*Erbbaurecht*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|erbbaurecht|boolean|false|none|none|
|erbbauzinsJaehrlich|number|false|none|none|
|grundstuecksEigentuemer|string|false|none|none|
|laufzeitBisJahr|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|grundstuecksEigentuemer|ANDERE|
|grundstuecksEigentuemer|OEFFENTLICH_KIRCHLICH|

<h2 id="tocSerror">Error</h2>

<a id="schemaerror"></a>

```json
{
  "message": "string",
  "statusCode": 0,
  "statusMessage": "string",
  "timestamp": "string",
  "traceId": "string"
}

```

*Error*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message|string|false|none|none|
|statusCode|integer(int32)|false|none|none|
|statusMessage|string|false|none|none|
|timestamp|string|false|none|none|
|traceId|string|false|none|none|

<h2 id="tocSfinanzbedarf">Finanzbedarf</h2>

<a id="schemafinanzbedarf"></a>

```json
{
  "anzahlTeilzahlungen": 0,
  "aussenAnlagen": 0,
  "bauNebenkosten": 0,
  "beratungsHonorar": 0,
  "bereitsBeglichen": 0,
  "erschliessung": 0,
  "grunderwerbsteuer": 0,
  "grundstueckBereitsBezahlt": true,
  "grundstuecksKaufpreis": 0,
  "herstellung": 0,
  "kapitalBeschaffung": 0,
  "kapitalWirdBeschafft": true,
  "kaufpreis": 0,
  "maklergebuehr": 0,
  "mobiliar": 0,
  "modernisieren": true,
  "modernisierung": 0,
  "notargebuehr": 0,
  "renovierung": 0,
  "sonstigeKosten": 0,
  "zusaetzlichesKapital": 0
}

```

*Finanzbedarf*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anzahlTeilzahlungen|integer(int32)|false|none|Anzahl Teilzahlungen bei Neubau, Kauf vom Bauträger sowie Modernisierung|
|aussenAnlagen|number|false|none|none|
|bauNebenkosten|number|false|none|none|
|beratungsHonorar|number|false|none|none|
|bereitsBeglichen|number|false|none|none|
|erschliessung|number|false|none|none|
|grunderwerbsteuer|number|false|none|Nebenkosten|
|grundstueckBereitsBezahlt|boolean|false|none|none|
|grundstuecksKaufpreis|number|false|none|none|
|herstellung|number|false|none|inklusive Eigenleistungen|
|kapitalBeschaffung|number|false|none|none|
|kapitalWirdBeschafft|boolean|false|none|none|
|kaufpreis|number|false|none|inklusive Eigenleistungen|
|maklergebuehr|number|false|none|Nebenkosten|
|mobiliar|number|false|none|none|
|modernisieren|boolean|false|none|none|
|modernisierung|number|false|none|inklusive Eigenleistungen|
|notargebuehr|number|false|none|Nebenkosten|
|renovierung|number|false|none|none|
|sonstigeKosten|number|false|none|none|
|zusaetzlichesKapital|number|false|none|none|

<h2 id="tocSfinanzierungsobjekt">FinanzierungsObjekt</h2>

<a id="schemafinanzierungsobjekt"></a>

```json
{
  "adresse": {
    "hausnummer": "string",
    "ort": "string",
    "postleitzahl": "string",
    "strasse": "string"
  },
  "autostellplaetze": [
    {
      "mieteinnahmenMonatlich": 0,
      "typ": "STELLPLATZ"
    }
  ],
  "bestehendeDarlehen": [
    {
      "abzuloesendeRestschuld": 0,
      "aktuelleRestschuldWennNichtAbzuloesen": 0,
      "darlehensArt": "BAUSPARDARLEHEN",
      "darlehensBetrag": 0,
      "darlehensGeber": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "darlehensKontonummer": "string",
      "eingetrageneGrundschuld": 0,
      "grundschuldArt": "BRIEF_GRUNDSCHULD",
      "id": "string",
      "laufzeitEnde": "2020-02-24",
      "rateMonatlich": 0,
      "sollZins": 0,
      "sondertilgungZumZinsBindungsEnde": 0,
      "verwendenAls": "ABLOESEN",
      "zinsBindungEndetAm": "2020-02-24"
    }
  ],
  "bewirtschaftungsKostenJaehrlich": 0,
  "bodenRichtwert": 0,
  "bundesland": "BADEN_WUERTTEMBERG",
  "effektivZinsErhoehendeKosten": {
    "anpassen": true,
    "grundbuchEintragungsKostenEinmalig": 0,
    "sonstigeKostenBezeichnung": "string",
    "sonstigeKostenEinmalig": 0,
    "wohnGebaeudeVersicherungsKostenJaehrlich": 0
  },
  "erbbaurecht": {
    "erbbaurecht": true,
    "erbbauzinsJaehrlich": 0,
    "grundstuecksEigentuemer": "ANDERE",
    "laufzeitBisJahr": "string"
  },
  "gebaeude": {
    "anzahlDerGewerbeeinheiten": 0,
    "anzahlDerWohneinheitenImGebaeude": 0,
    "anzahlVollgeschosse": 0,
    "aufbauFinanzierung": true,
    "aufzugVorhanden": true,
    "ausstattung": "EINFACH",
    "baujahr": "2016",
    "bauweise": "FACHWERK_MIT_STROH_LEHM",
    "bezeichnungWohneinheit": "string",
    "dachgeschossAusbau": "FLACHDACH",
    "einliegerwohnungVorhanden": true,
    "geschossLage": "UNTERGESCHOSS",
    "gewerbeflaeche": {
      "gesamtGroesse": 0,
      "vermietungsInformationen": {
        "mieteinnahmenNettoKaltMonatlich": 0,
        "nutzungsArt": "EIGENGENUTZT",
        "vermieteteFlaeche": 0
      }
    },
    "hausAnordnung": "FREISTEHEND",
    "hausTyp": "DOPPELHAUSHAELFTE",
    "istFertighaus": true,
    "kellerausbau": "AUSGEBAUT",
    "kubatur": 0,
    "miteigentumsAnteil": {
      "anteil": 0,
      "gesamt": 0
    },
    "modernisierungsAngaben": {
      "badWc": true,
      "bodenWandTreppe": true,
      "dach": true,
      "fenster": true,
      "heizungZentral": true,
      "modernisierungsGrad": "GERING",
      "modernisierungsJahr": "string",
      "raumaufteilung": true,
      "stromAbwasserHeizkoerper": true,
      "waermedaemmung": true,
      "wurdeModernisiert": true
    },
    "unterkellerung": "NICHT_UNTERKELLERT",
    "wohnflaeche": {
      "gesamtGroesse": 0,
      "vermietungsInformationen": {
        "mieteinnahmenNettoKaltMonatlich": 0,
        "nutzungsArt": "EIGENGENUTZT",
        "vermieteteFlaeche": 0
      }
    },
    "zustand": "SEHR_GUT"
  },
  "grundbuchAngabe": {
    "anmerkungen": "string",
    "bandUndBlatt": "string",
    "flurstuecke": [
      {
        "anteil": {
          "anteil": 0,
          "gesamt": 0
        },
        "flur": "string",
        "flurstuecksNummer": "string",
        "groesse": 0
      }
    ],
    "ort": "string",
    "rechteInAbteilung2": {
      "beschreibung": "string",
      "betrag": 0,
      "vorhanden": true
    }
  },
  "grundstueck": {
    "groesse": 0,
    "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
  },
  "id": "string",
  "keinBaulandFlaecheInQm": 0,
  "marktueblicherKaufpreisProQm": 0,
  "marktwert": 0,
  "objektArt": "GRUNDSTUECK",
  "vergleichsmieteFuerGewerbeflaecheProQm": 0,
  "vergleichsmieteFuerWohnflaecheProQm": 0,
  "verkehrswert": 0,
  "vorlaeufigerVerkehrswert": 0,
  "wohnlage": "GEHOBEN"
}

```

*FinanzierungsObjekt*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|adresse|[Postadresse](#schemapostadresse)|false|none|none|
|autostellplaetze|[[Autostellplatz](#schemaautostellplatz)]|false|none|none|
|bestehendeDarlehen|[[BestehendesDarlehenDesFinanzierungsObjekts](#schemabestehendesdarlehendesfinanzierungsobjekts)]|false|none|none|
|bewirtschaftungsKostenJaehrlich|number|false|none|none|
|bodenRichtwert|number|false|none|none|
|bundesland|string|false|none|none|
|effektivZinsErhoehendeKosten|[EffektivZinsErhoehendeKosten](#schemaeffektivzinserhoehendekosten)|false|none|none|
|erbbaurecht|[Erbbaurecht](#schemaerbbaurecht)|false|none|none|
|gebaeude|[Gebaeude](#schemagebaeude)|false|none|none|
|grundbuchAngabe|[GrundbuchAngabe](#schemagrundbuchangabe)|false|none|none|
|grundstueck|[Grundstueck](#schemagrundstueck)|false|none|none|
|id|string|false|none|none|
|keinBaulandFlaecheInQm|number|false|none|none|
|marktueblicherKaufpreisProQm|number|false|none|none|
|marktwert|number|false|none|Nur relevant bei Finanzbedarf AnschlussFinanzierung, Modernisierung und Kapitalbeschaffung.|
|objektArt|string|false|none|none|
|vergleichsmieteFuerGewerbeflaecheProQm|number|false|none|none|
|vergleichsmieteFuerWohnflaecheProQm|number|false|none|none|
|verkehrswert|number|false|none|Hat den selben Inhalt wie das Feld marktwert. (Wird in v3 nicht mehr enthalten sein)|
|vorlaeufigerVerkehrswert|number|false|none|Diese Angabe ist produktanbieterspezifisch, sie wird nicht von allen Produktanbietern bei der Angebotsermittlung berücksichtigt.|
|wohnlage|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|bundesland|BADEN_WUERTTEMBERG|
|bundesland|BAYERN|
|bundesland|BERLIN|
|bundesland|BRANDENBURG|
|bundesland|BREMEN|
|bundesland|HAMBURG|
|bundesland|HESSEN|
|bundesland|MECKLENBURG_VORPOMMERN|
|bundesland|NIEDERSACHSEN|
|bundesland|NORDRHEIN_WESTFALEN|
|bundesland|RHEINLAND_PFALZ|
|bundesland|SAARLAND|
|bundesland|SACHSEN|
|bundesland|SACHSEN_ANHALT|
|bundesland|SCHLESWIG_HOLSTEIN|
|bundesland|THUERINGEN|
|objektArt|GRUNDSTUECK|
|objektArt|EIGENTUMSWOHNUNG|
|objektArt|HAUS|
|wohnlage|GEHOBEN|
|wohnlage|MITTEL|
|wohnlage|EINFACH|

<h2 id="tocSfinanzierungswunsch">Finanzierungswunsch</h2>

<a id="schemafinanzierungswunsch"></a>

```json
{
  "bausparWuensche": [
    {
      "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
      "bausparSummeAbsolut": 0,
      "bausparSummeRelativ": 0,
      "bausparTarif": [
        {
          "id": "string",
          "kurzName": "string",
          "langName": "string",
          "produktAnbieter": "string",
          "riesterFoerderung": true,
          "status": "AKTIV"
        }
      ],
      "bausparTarife": [
        "string"
      ],
      "id": "string",
      "sonderZahlungEinmalig": 0,
      "sonderZahlungen": [
        {
          "anzahl": 0,
          "betrag": 0,
          "termin": "2020-02-24",
          "zahlweise": "EINMALIG"
        }
      ],
      "sparBeginn": "2020-02-24",
      "sparBeitragMonatlichAbsolut": 0,
      "sparBeitragMonatlichRelativ": 0,
      "tilgungsBeitragMonatlich": 0,
      "vertragsPartnerIds": [
        "string"
      ],
      "verwendung": "ZINS_ABSICHERUNG",
      "zuteilungsDatum": "2020-02-24"
    }
  ],
  "darlehensWuensche": [
    {
      "annuitaetenDarlehen": {
        "auszahlungsDatum": "2020-02-24",
        "bereitstellungsZinsFreieZeitInMonaten": 0,
        "darlehensBetrag": 0,
        "provision": 0,
        "sondertilgungOptionalJaehrlich": 0,
        "tilgungsWunsch": {
          "anfaenglicheTilgung": 0,
          "ausgesetztBerechnet": false,
          "ausgesetztEigenesAngebot": false,
          "bausparWunsch": {
            "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
            "bausparSummeAbsolut": 0,
            "bausparSummeRelativ": 0,
            "bausparTarif": [
              {
                "id": "string",
                "kurzName": "string",
                "langName": "string",
                "produktAnbieter": "string",
                "riesterFoerderung": true,
                "status": "AKTIV"
              }
            ],
            "bausparTarife": [
              "string"
            ],
            "id": "string",
            "sonderZahlungEinmalig": 0,
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeginn": "2020-02-24",
            "sparBeitragMonatlichAbsolut": 0,
            "sparBeitragMonatlichRelativ": 0,
            "tilgungsBeitragMonatlich": 0,
            "vertragsPartnerIds": [
              "string"
            ],
            "verwendung": "ZINS_ABSICHERUNG",
            "zuteilungsDatum": "2020-02-24"
          },
          "rate": 0,
          "tilgungsBeginn": "2020-02-24",
          "tilgungsErsatzProduktId": "string",
          "volltilgerWennAnnuitaetenOderForward": false
        },
        "zinsBindungInJahren": 0
      },
      "forwardDarlehen": {
        "auszahlungsDatum": "2020-02-24",
        "bereitstellungsZinsFreieZeitInMonaten": 0,
        "darlehensBetrag": 0,
        "provision": 0,
        "sondertilgungOptionalJaehrlich": 0,
        "tilgungsWunsch": {
          "anfaenglicheTilgung": 0,
          "ausgesetztBerechnet": false,
          "ausgesetztEigenesAngebot": false,
          "bausparWunsch": {
            "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
            "bausparSummeAbsolut": 0,
            "bausparSummeRelativ": 0,
            "bausparTarif": [
              {
                "id": "string",
                "kurzName": "string",
                "langName": "string",
                "produktAnbieter": "string",
                "riesterFoerderung": true,
                "status": "AKTIV"
              }
            ],
            "bausparTarife": [
              "string"
            ],
            "id": "string",
            "sonderZahlungEinmalig": 0,
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeginn": "2020-02-24",
            "sparBeitragMonatlichAbsolut": 0,
            "sparBeitragMonatlichRelativ": 0,
            "tilgungsBeitragMonatlich": 0,
            "vertragsPartnerIds": [
              "string"
            ],
            "verwendung": "ZINS_ABSICHERUNG",
            "zuteilungsDatum": "2020-02-24"
          },
          "rate": 0,
          "tilgungsBeginn": "2020-02-24",
          "tilgungsErsatzProduktId": "string",
          "volltilgerWennAnnuitaetenOderForward": false
        },
        "zinsBindungInJahren": 0
      },
      "id": "string",
      "kfwDarlehen": {
        "darlehensBetrag": 0,
        "kfwEndfaellig": "NEIN",
        "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
        "kfwProgramm": "PROGRAMM_124",
        "laufzeitInJahren": 0,
        "provision": 0,
        "tilgungsWunsch": {
          "anfaenglicheTilgung": 0,
          "ausgesetztBerechnet": false,
          "ausgesetztEigenesAngebot": false,
          "bausparWunsch": {
            "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
            "bausparSummeAbsolut": 0,
            "bausparSummeRelativ": 0,
            "bausparTarif": [
              {
                "id": "string",
                "kurzName": "string",
                "langName": "string",
                "produktAnbieter": "string",
                "riesterFoerderung": true,
                "status": "AKTIV"
              }
            ],
            "bausparTarife": [
              "string"
            ],
            "id": "string",
            "sonderZahlungEinmalig": 0,
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeginn": "2020-02-24",
            "sparBeitragMonatlichAbsolut": 0,
            "sparBeitragMonatlichRelativ": 0,
            "tilgungsBeitragMonatlich": 0,
            "vertragsPartnerIds": [
              "string"
            ],
            "verwendung": "ZINS_ABSICHERUNG",
            "zuteilungsDatum": "2020-02-24"
          },
          "rate": 0,
          "tilgungsBeginn": "2020-02-24",
          "tilgungsErsatzProduktId": "string",
          "volltilgerWennAnnuitaetenOderForward": false
        },
        "tilgungsfreieAnlaufjahre": 0,
        "zinsBindungInJahren": 0
      },
      "privatDarlehen": {
        "darlehensBetrag": 0,
        "laufzeitInMonaten": 0,
        "provision": 0
      },
      "variablesDarlehen": {
        "darlehensBetrag": 0,
        "provision": 0,
        "tilgungsWunsch": {
          "anfaenglicheTilgung": 0,
          "ausgesetztBerechnet": false,
          "ausgesetztEigenesAngebot": false,
          "bausparWunsch": {
            "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
            "bausparSummeAbsolut": 0,
            "bausparSummeRelativ": 0,
            "bausparTarif": [
              {
                "id": "string",
                "kurzName": "string",
                "langName": "string",
                "produktAnbieter": "string",
                "riesterFoerderung": true,
                "status": "AKTIV"
              }
            ],
            "bausparTarife": [
              "string"
            ],
            "id": "string",
            "sonderZahlungEinmalig": 0,
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeginn": "2020-02-24",
            "sparBeitragMonatlichAbsolut": 0,
            "sparBeitragMonatlichRelativ": 0,
            "tilgungsBeitragMonatlich": 0,
            "vertragsPartnerIds": [
              "string"
            ],
            "verwendung": "ZINS_ABSICHERUNG",
            "zuteilungsDatum": "2020-02-24"
          },
          "rate": 0,
          "tilgungsBeginn": "2020-02-24",
          "tilgungsErsatzProduktId": "string",
          "volltilgerWennAnnuitaetenOderForward": false
        }
      },
      "zwischenFinanzierung": {
        "darlehensBetrag": 0,
        "detailsZurVerwendung": "string",
        "maximaleLaufzeitInMonaten": 0,
        "provision": 0,
        "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
      }
    }
  ],
  "id": "string"
}

```

*Finanzierungswunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bausparWuensche|[[BausparWunsch](#schemabausparwunsch)]|false|none|[Von den Feldern bausparSummeAbsolut, bausparSummeRelativ, sparBeitragMonatlichAbsolut, sparBeitragMonatlichRelativ, tilgungsBeitragMonatlich, zuteilungsDatum und sparBeginn können maximal drei befüllt sein.]|
|darlehensWuensche|[[DarlehensWunsch](#schemadarlehenswunsch)]|false|none|none|
|id|string|false|none|none|

<h2 id="tocSflurstueck">Flurstueck</h2>

<a id="schemaflurstueck"></a>

```json
{
  "anteil": {
    "anteil": 0,
    "gesamt": 0
  },
  "flur": "string",
  "flurstuecksNummer": "string",
  "groesse": 0
}

```

*Flurstueck*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anteil|[MiteigentumsAnteil](#schemamiteigentumsanteil)|false|none|none|
|flur|string|false|none|none|
|flurstuecksNummer|string|false|none|none|
|groesse|number|false|none|none|

<h2 id="tocSforwarddarlehenswunsch">ForwardDarlehensWunsch</h2>

<a id="schemaforwarddarlehenswunsch"></a>

```json
{
  "auszahlungsDatum": "2020-02-24",
  "bereitstellungsZinsFreieZeitInMonaten": 0,
  "darlehensBetrag": 0,
  "provision": 0,
  "sondertilgungOptionalJaehrlich": 0,
  "tilgungsWunsch": {
    "anfaenglicheTilgung": 0,
    "ausgesetztBerechnet": false,
    "ausgesetztEigenesAngebot": false,
    "bausparWunsch": {
      "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
      "bausparSummeAbsolut": 0,
      "bausparSummeRelativ": 0,
      "bausparTarif": [
        {
          "id": "string",
          "kurzName": "string",
          "langName": "string",
          "produktAnbieter": "string",
          "riesterFoerderung": true,
          "status": "AKTIV"
        }
      ],
      "bausparTarife": [
        "string"
      ],
      "id": "string",
      "sonderZahlungEinmalig": 0,
      "sonderZahlungen": [
        {
          "anzahl": 0,
          "betrag": 0,
          "termin": "2020-02-24",
          "zahlweise": "EINMALIG"
        }
      ],
      "sparBeginn": "2020-02-24",
      "sparBeitragMonatlichAbsolut": 0,
      "sparBeitragMonatlichRelativ": 0,
      "tilgungsBeitragMonatlich": 0,
      "vertragsPartnerIds": [
        "string"
      ],
      "verwendung": "ZINS_ABSICHERUNG",
      "zuteilungsDatum": "2020-02-24"
    },
    "rate": 0,
    "tilgungsBeginn": "2020-02-24",
    "tilgungsErsatzProduktId": "string",
    "volltilgerWennAnnuitaetenOderForward": false
  },
  "zinsBindungInJahren": 0
}

```

*ForwardDarlehensWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|auszahlungsDatum|string(date)|false|none|none|
|bereitstellungsZinsFreieZeitInMonaten|integer(int32)|false|none|none|
|darlehensBetrag|number|false|none|none|
|provision|number|false|none|none|
|sondertilgungOptionalJaehrlich|number|false|none|none|
|tilgungsWunsch|[TilgungsWunsch](#schematilgungswunsch)|false|none|none|
|zinsBindungInJahren|integer(int32)|false|none|none|

<h2 id="tocSgebaeude">Gebaeude</h2>

<a id="schemagebaeude"></a>

```json
{
  "anzahlDerGewerbeeinheiten": 0,
  "anzahlDerWohneinheitenImGebaeude": 0,
  "anzahlVollgeschosse": 0,
  "aufbauFinanzierung": true,
  "aufzugVorhanden": true,
  "ausstattung": "EINFACH",
  "baujahr": "2016",
  "bauweise": "FACHWERK_MIT_STROH_LEHM",
  "bezeichnungWohneinheit": "string",
  "dachgeschossAusbau": "FLACHDACH",
  "einliegerwohnungVorhanden": true,
  "geschossLage": "UNTERGESCHOSS",
  "gewerbeflaeche": {
    "gesamtGroesse": 0,
    "vermietungsInformationen": {
      "mieteinnahmenNettoKaltMonatlich": 0,
      "nutzungsArt": "EIGENGENUTZT",
      "vermieteteFlaeche": 0
    }
  },
  "hausAnordnung": "FREISTEHEND",
  "hausTyp": "DOPPELHAUSHAELFTE",
  "istFertighaus": true,
  "kellerausbau": "AUSGEBAUT",
  "kubatur": 0,
  "miteigentumsAnteil": {
    "anteil": 0,
    "gesamt": 0
  },
  "modernisierungsAngaben": {
    "badWc": true,
    "bodenWandTreppe": true,
    "dach": true,
    "fenster": true,
    "heizungZentral": true,
    "modernisierungsGrad": "GERING",
    "modernisierungsJahr": "string",
    "raumaufteilung": true,
    "stromAbwasserHeizkoerper": true,
    "waermedaemmung": true,
    "wurdeModernisiert": true
  },
  "unterkellerung": "NICHT_UNTERKELLERT",
  "wohnflaeche": {
    "gesamtGroesse": 0,
    "vermietungsInformationen": {
      "mieteinnahmenNettoKaltMonatlich": 0,
      "nutzungsArt": "EIGENGENUTZT",
      "vermieteteFlaeche": 0
    }
  },
  "zustand": "SEHR_GUT"
}

```

*Gebaeude*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anzahlDerGewerbeeinheiten|integer(int32)|false|none|none|
|anzahlDerWohneinheitenImGebaeude|integer(int32)|false|none|none|
|anzahlVollgeschosse|integer(int32)|false|none|none|
|aufbauFinanzierung|boolean|false|none|none|
|aufzugVorhanden|boolean|false|none|none|
|ausstattung|string|false|none|none|
|baujahr|string|false|none|Baujahr des Gebäudes. Bei Verwendungszweck != NEUBAU 2016|
|bauweise|string|false|none|none|
|bezeichnungWohneinheit|string|false|none|none|
|dachgeschossAusbau|string|false|none|none|
|einliegerwohnungVorhanden|boolean|false|none|none|
|geschossLage|string|false|none|none|
|gewerbeflaeche|[GebaeudeFlaeche](#schemagebaeudeflaeche)|false|none|none|
|hausAnordnung|string|false|none|none|
|hausTyp|string|false|none|none|
|istFertighaus|boolean|false|none|none|
|kellerausbau|string|false|none|none|
|kubatur|number|false|none|none|
|miteigentumsAnteil|[MiteigentumsAnteil](#schemamiteigentumsanteil)|false|none|none|
|modernisierungsAngaben|[ModernisierungsAngaben](#schemamodernisierungsangaben)|false|none|none|
|unterkellerung|string|false|none|none|
|wohnflaeche|[GebaeudeFlaeche](#schemagebaeudeflaeche)|false|none|none|
|zustand|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|ausstattung|EINFACH|
|ausstattung|MITTEL|
|ausstattung|GEHOBEN|
|ausstattung|STARK_GEHOBEN|
|bauweise|FACHWERK_MIT_STROH_LEHM|
|bauweise|FACHWERK_MIT_ZIEGELN|
|bauweise|GLAS_STAHL|
|bauweise|HOLZ|
|bauweise|MASSIV|
|dachgeschossAusbau|FLACHDACH|
|dachgeschossAusbau|NICHT_AUSGEBAUT|
|dachgeschossAusbau|TEILWEISE_AUSGEBAUT|
|dachgeschossAusbau|VOLL_AUSGEBAUT|
|geschossLage|UNTERGESCHOSS|
|geschossLage|ERDGESCHOSS|
|geschossLage|ERSTES_OBERGESCHOSS|
|geschossLage|ZWEITES_OBERGESCHOSS|
|geschossLage|DRITTES_BIS_FUENFTES_OBERGESCHOSS|
|geschossLage|AB_SECHSTES_OBERGESCHOSS|
|geschossLage|UNBEKANNT|
|hausAnordnung|FREISTEHEND|
|hausAnordnung|KOPFHAUS|
|hausAnordnung|MITTELHAUS|
|hausTyp|DOPPELHAUSHAELFTE|
|hausTyp|EINFAMILIENHAUS|
|hausTyp|MEHRFAMILIENHAUS|
|hausTyp|REIHENHAUS|
|hausTyp|ZWEIFAMILIENHAUS|
|kellerausbau|AUSGEBAUT|
|kellerausbau|TEILWEISE_AUSGEBAUT|
|kellerausbau|VORHANDEN|
|unterkellerung|NICHT_UNTERKELLERT|
|unterkellerung|TEILWEISE_UNTERKELLERT|
|unterkellerung|UNTERKELLERT|
|zustand|SEHR_GUT|
|zustand|GUT|
|zustand|MITTEL|
|zustand|MAESSIG|
|zustand|SCHLECHT|

<h2 id="tocSgebaeudeflaeche">GebaeudeFlaeche</h2>

<a id="schemagebaeudeflaeche"></a>

```json
{
  "gesamtGroesse": 0,
  "vermietungsInformationen": {
    "mieteinnahmenNettoKaltMonatlich": 0,
    "nutzungsArt": "EIGENGENUTZT",
    "vermieteteFlaeche": 0
  }
}

```

*GebaeudeFlaeche*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|gesamtGroesse|number|false|none|none|
|vermietungsInformationen|[VermietungsInformationen](#schemavermietungsinformationen)|false|none|none|

<h2 id="tocSgrundbuchangabe">GrundbuchAngabe</h2>

<a id="schemagrundbuchangabe"></a>

```json
{
  "anmerkungen": "string",
  "bandUndBlatt": "string",
  "flurstuecke": [
    {
      "anteil": {
        "anteil": 0,
        "gesamt": 0
      },
      "flur": "string",
      "flurstuecksNummer": "string",
      "groesse": 0
    }
  ],
  "ort": "string",
  "rechteInAbteilung2": {
    "beschreibung": "string",
    "betrag": 0,
    "vorhanden": true
  }
}

```

*GrundbuchAngabe*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anmerkungen|string|false|none|none|
|bandUndBlatt|string|false|none|Angabe von Band und Blatt|
|flurstuecke|[[Flurstueck](#schemaflurstueck)]|false|none|none|
|ort|string|false|none|Ort des als Grundbuchamt zuständigen Amtsgerichtes|
|rechteInAbteilung2|[RechteAbteilung2](#schemarechteabteilung2)|false|none|Belastungen und Beschränkungen in der Nutzbarkeit des Grundstücks. Leitungsrechte, Verzichte auf Abstandsflächen, Wegerechte, Insolvenzvermerke.|

<h2 id="tocSgrundstueck">Grundstueck</h2>

<a id="schemagrundstueck"></a>

```json
{
  "groesse": 0,
  "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
}

```

*Grundstueck*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|groesse|number|false|none|none|
|grundstuecksArt|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|grundstuecksArt|UNBEBAUTES_WOHNGRUNDSTUECK|
|grundstuecksArt|UNBEBAUTES_MISCHGRUNDSTUECK|
|grundstuecksArt|UNBEBAUTES_GEWERBEGRUNDSTUECK|
|grundstuecksArt|LANDWIRTSCHAFTLICHES_GRUNDSTUECK|
|grundstuecksArt|SONSTIGES_GRUNDSTUECK|

<h2 id="tocShaushalt">Haushalt</h2>

<a id="schemahaushalt"></a>

```json
{
  "antragsteller": [
    {
      "anrede": "FRAU",
      "anschrift": {
        "hausnummer": "string",
        "ort": "string",
        "postleitzahl": "string",
        "strasse": "string"
      },
      "arbeitserlaubnis": false,
      "arbeitserlaubnisBefristetBis": "2020-02-24",
      "aufenthaltsTitel": "VISUM",
      "aufenthaltsTitelBefristetBis": "2020-02-24",
      "beschaeftigung": {
        "anzahlGehaelterProJahr": 0,
        "arbeitgeber": "string",
        "arbeitgeberInDeutschlandAnsaessig": false,
        "arbeitgeberLand": {
          "isoCountryCode": "string",
          "name": "string"
        },
        "art": "ANGESTELLTER",
        "befristungsStatus": "BEFRISTET",
        "beruf": "string",
        "beschaeftigtSeit": "2020-02-24",
        "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
        "einkommenNettoJaehrlich": 0,
        "einkommenNettoMonatlich": 0,
        "firma": "string",
        "inProbezeit": false,
        "situationNachRenteneintritt": {
          "gesetzlicheRenteMonatlich": 0,
          "privateRenteMonatlich": 0,
          "rentenBeginn": "2020-02-24",
          "sonstigesEinkommenMonatlich": 0
        },
        "taetigkeit": "ALTENPFLEGER"
      },
      "bruttoVorjahresEinkommen": 0,
      "email": "max.mustermann@test.de",
      "externeAntragstellerId": "string",
      "familienstand": "GESCHIEDEN",
      "geburtsdatum": "2020-02-24",
      "geburtsort": "string",
      "guetertrennungVereinbartWennVerheiratet": false,
      "id": "string",
      "inDeutschlandSeit": "2020-02-24",
      "legitimationsDaten": {
        "ausstellendeBehoerde": "string",
        "ausstellungsdatum": "2020-02-24",
        "ausweisArt": "PERSONALAUSWEIS",
        "ausweisArtBeiAndererAusweis": "string",
        "ausweisNummer": "string"
      },
      "nachname": "string",
      "schufaErgebnis": {
        "antragstellerUnbekannt": false,
        "inManuellerNachbehandlung": false,
        "score": "string"
      },
      "staatsangehoerigkeit": {
        "isoCountryCode": "string",
        "name": "string"
      },
      "steuerId": "string",
      "telefonnummer": "string",
      "telefonnummerVorwahl": "string",
      "titel": [
        "DOKTOR"
      ],
      "titelDoktor": true,
      "titelProfessor": true,
      "vorAnschrift": {
        "hausnummer": "string",
        "ort": "string",
        "postleitzahl": "string",
        "strasse": "string"
      },
      "vorname": "string",
      "weitereKontaktMoeglichkeiten": "string",
      "wohnhaftSeit": "2020-02-24"
    }
  ],
  "anzahlErwachseneImHaushalt": 0,
  "anzahlKinderNichtImHaushalt": 0,
  "bestehendeImmobilien": [
    {
      "adresse": {
        "hausnummer": "string",
        "ort": "string",
        "postleitzahl": "string",
        "strasse": "string"
      },
      "autostellplaetze": [
        {
          "mieteinnahmenMonatlich": 0,
          "typ": "STELLPLATZ"
        }
      ],
      "bestehendeDarlehen": [
        {
          "abzuloesendeRestschuld": 0,
          "aktuelleRestschuldWennNichtAbzuloesen": 0,
          "darlehensArt": "BAUSPARDARLEHEN",
          "darlehensBetrag": 0,
          "darlehensGeber": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          },
          "darlehensKontonummer": "string",
          "eingetrageneGrundschuld": 0,
          "grundschuldArt": "BRIEF_GRUNDSCHULD",
          "id": "string",
          "laufzeitEnde": "2020-02-24",
          "rateMonatlich": 0,
          "sollZins": 0,
          "sondertilgungZumZinsBindungsEnde": 0,
          "zinsBindungEndetAm": "2020-02-24"
        }
      ],
      "bewirtschaftungsKostenJaehrlich": 0,
      "bodenRichtwert": 0,
      "bundesland": "BADEN_WUERTTEMBERG",
      "effektivZinsErhoehendeKosten": {
        "anpassen": true,
        "grundbuchEintragungsKostenEinmalig": 0,
        "sonstigeKostenBezeichnung": "string",
        "sonstigeKostenEinmalig": 0,
        "wohnGebaeudeVersicherungsKostenJaehrlich": 0
      },
      "erbbaurecht": {
        "erbbaurecht": true,
        "erbbauzinsJaehrlich": 0,
        "grundstuecksEigentuemer": "ANDERE",
        "laufzeitBisJahr": "string"
      },
      "gebaeude": {
        "anzahlDerGewerbeeinheiten": 0,
        "anzahlDerWohneinheitenImGebaeude": 0,
        "anzahlVollgeschosse": 0,
        "aufbauFinanzierung": true,
        "aufzugVorhanden": true,
        "ausstattung": "EINFACH",
        "baujahr": "2016",
        "bauweise": "FACHWERK_MIT_STROH_LEHM",
        "bezeichnungWohneinheit": "string",
        "dachgeschossAusbau": "FLACHDACH",
        "einliegerwohnungVorhanden": true,
        "geschossLage": "UNTERGESCHOSS",
        "gewerbeflaeche": {
          "gesamtGroesse": 0,
          "vermietungsInformationen": {
            "mieteinnahmenNettoKaltMonatlich": 0,
            "nutzungsArt": "EIGENGENUTZT",
            "vermieteteFlaeche": 0
          }
        },
        "hausAnordnung": "FREISTEHEND",
        "hausTyp": "DOPPELHAUSHAELFTE",
        "istFertighaus": true,
        "kellerausbau": "AUSGEBAUT",
        "kubatur": 0,
        "miteigentumsAnteil": {
          "anteil": 0,
          "gesamt": 0
        },
        "modernisierungsAngaben": {
          "badWc": true,
          "bodenWandTreppe": true,
          "dach": true,
          "fenster": true,
          "heizungZentral": true,
          "modernisierungsGrad": "GERING",
          "modernisierungsJahr": "string",
          "raumaufteilung": true,
          "stromAbwasserHeizkoerper": true,
          "waermedaemmung": true,
          "wurdeModernisiert": true
        },
        "unterkellerung": "NICHT_UNTERKELLERT",
        "wohnflaeche": {
          "gesamtGroesse": 0,
          "vermietungsInformationen": {
            "mieteinnahmenNettoKaltMonatlich": 0,
            "nutzungsArt": "EIGENGENUTZT",
            "vermieteteFlaeche": 0
          }
        },
        "zustand": "SEHR_GUT"
      },
      "grundbuchAngabe": {
        "anmerkungen": "string",
        "bandUndBlatt": "string",
        "flurstuecke": [
          {
            "anteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "flur": "string",
            "flurstuecksNummer": "string",
            "groesse": 0
          }
        ],
        "ort": "string",
        "rechteInAbteilung2": {
          "beschreibung": "string",
          "betrag": 0,
          "vorhanden": true
        }
      },
      "grundstueck": {
        "groesse": 0,
        "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
      },
      "id": "string",
      "immobilienEinsatz": "KEIN_EINSATZ",
      "keinBaulandFlaecheInQm": 0,
      "keineBestehendenDarlehenVorhanden": true,
      "marktueblicherKaufpreisProQm": 0,
      "marktwert": 0,
      "maximalEinzusetzenderBetragWennVerkauf": 0,
      "objektArt": "GRUNDSTUECK",
      "vergleichsmieteFuerGewerbeflaecheProQm": 0,
      "vergleichsmieteFuerWohnflaecheProQm": 0,
      "verkehrswert": 0,
      "vorlaeufigerVerkehrswert": 0,
      "wohnlage": "GEHOBEN"
    }
  ],
  "id": "string",
  "kfzAnzahl": 0,
  "kinder": [
    {
      "geburtsdatum": "2020-02-24",
      "id": "string",
      "kindergeldWirdBezogen": true,
      "name": "string",
      "unterhaltsEinnahmenBetragMonatlich": 0
    }
  ],
  "lebenshaltungsKostenMonatlich": 0,
  "obligo": {
    "vermoegenOderVerbindlichkeiten": [
      {
        "aktuellerWert": 0,
        "anrechnungFuerBlankoAnteil": 0,
        "bezeichner": "string",
        "kontonummer": "string",
        "vermoegensTyp": "VERMOEGEN"
      }
    ]
  },
  "positionen": {
    "bankUndSparguthaben": [
      {
        "aktuellerWert": 0,
        "ertrag": 0,
        "maximalAufzuloesenderWert": 0,
        "vermoegensEinsatz": "KEIN_EINSATZ",
        "vermoegensTyp": "VERMOEGEN",
        "zahlungsTyp": "EINNAHME",
        "zinsertragJaehrlich": 0,
        "zukuenftigeEinnahmen": 0
      }
    ],
    "bausparvertraege": [
      {
        "abschlussGebuehr": 0,
        "aktuellerWert": 0,
        "bausparSumme": 0,
        "einmalzahlung": 0,
        "ertrag": 0,
        "id": "string",
        "maximalAufzuloesenderBetrag": 0,
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparBeitragMonatlich": 0,
        "tarif": "string",
        "typ": "string",
        "vermoegensEinsatz": "KEIN_EINSATZ",
        "vermoegensTyp": "VERMOEGEN",
        "vertragsBeginn": "2020-02-24",
        "vertragsNummer": "string",
        "verwaltungsgebuehrenJaehrlich": 0,
        "zahlungsTyp": "EINNAHME",
        "zukuenftigeEinnahmen": 0,
        "zuteilungsDatum": "2020-02-24"
      }
    ],
    "ehegattenUnterhalt": [
      {
        "einnahmenMonatlich": 0,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "einkuenfteAusNebentaetigkeit": [
      {
        "beginnDerNebentaetigkeit": "2020-02-24",
        "einnahmenMonatlich": 0,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "kindergeld": [
      {
        "einnahmenMonatlich": 0,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "lebensUndRentenVersicherungen": [
      {
        "id": "string",
        "maximalAufzuloesenderBetrag": 0,
        "praemieMonatlich": 0,
        "rueckkaufsWertAktuell": 0,
        "tarif": "string",
        "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
        "vermoegensEinsatz": "KEIN_EINSATZ",
        "vermoegensTyp": "VERMOEGEN",
        "versicherungsGesellschaft": "string",
        "versicherungsSumme": 0,
        "vertragsBeginn": "2020-02-24",
        "vertragsEnde": "2020-02-24",
        "vertragsNummer": "string",
        "verwaltungsgebuehrenJaehrlich": 0,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "mietAusgaben": [
      {
        "ausgabenMonatlich": 0,
        "berechnungsHilfeVermoegen": {
          "betragNachFinanzierung": 0,
          "betragVorFinanzierung": 0
        },
        "entfallenMitFinanzierung": true,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "privateDarlehen": [
      {
        "glaeubiger": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "restschuld": 0,
        "vermoegensTyp": "VERMOEGEN",
        "wirdAbgeloest": true,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "privateKrankenversicherung": [
      {
        "ausgabenMonatlich": 0,
        "berechnungsHilfeVermoegen": {
          "betragNachFinanzierung": 0,
          "betragVorFinanzierung": 0
        },
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "ratenkredite": [
      {
        "glaeubiger": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "restschuld": 0,
        "vermoegensTyp": "VERMOEGEN",
        "wirdAbgeloest": true,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "sonstigeAusgaben": [
      {
        "ausgabenMonatlich": 0,
        "berechnungsHilfeVermoegen": {
          "betragNachFinanzierung": 0,
          "betragVorFinanzierung": 0
        },
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "sonstigeEinnahmen": [
      {
        "einnahmenMonatlich": 0,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "sonstigeVerbindlichkeiten": [
      {
        "glaeubiger": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "restschuld": 0,
        "vermoegensTyp": "VERMOEGEN",
        "wirdAbgeloest": true,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "sonstigeVermoegen": [
      {
        "aktuellerWert": 0,
        "ertrag": 0,
        "maximalAufzuloesenderWert": 0,
        "vermoegensEinsatz": "KEIN_EINSATZ",
        "vermoegensTyp": "VERMOEGEN",
        "zukuenftigeEinnahmen": 0
      }
    ],
    "sparplaene": [
      {
        "aktuellerWert": 0,
        "beitragMonatlich": 0,
        "ertrag": 0,
        "maximalAufzuloesenderWert": 0,
        "vermoegensEinsatz": "KEIN_EINSATZ",
        "vermoegensTyp": "VERMOEGEN",
        "zahlungsTyp": "EINNAHME",
        "zukuenftigeEinnahmen": 0
      }
    ],
    "unbefristeteZusatzRenten": [
      {
        "einnahmenMonatlich": 0,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "unterhaltsVerpflichtungen": [
      {
        "ausgabenMonatlich": 0,
        "berechnungsHilfeVermoegen": {
          "betragNachFinanzierung": 0,
          "betragVorFinanzierung": 0
        },
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "variableEinkuenfte": [
      {
        "einnahmenMonatlich": 0,
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "versicherungsAusgaben": [
      {
        "ausgabenMonatlich": 0,
        "berechnungsHilfeVermoegen": {
          "betragNachFinanzierung": 0,
          "betragVorFinanzierung": 0
        },
        "zahlungsTyp": "EINNAHME"
      }
    ],
    "wertpapiere": [
      {
        "aktuellerWert": 0,
        "dividendenJaehrlich": 0,
        "ertrag": 0,
        "maximalAufzuloesenderWert": 0,
        "vermoegensEinsatz": "KEIN_EINSATZ",
        "vermoegensTyp": "VERMOEGEN",
        "zahlungsTyp": "EINNAHME",
        "zukuenftigeEinnahmen": 0
      }
    ]
  }
}

```

*Haushalt*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|antragsteller|[[Antragsteller](#schemaantragsteller)]|false|none|none|
|anzahlErwachseneImHaushalt|integer(int32)|false|none|none|
|anzahlKinderNichtImHaushalt|integer(int32)|false|none|none|
|bestehendeImmobilien|[[BestehendeImmobilie](#schemabestehendeimmobilie)]|false|none|none|
|id|string|false|none|none|
|kfzAnzahl|integer(int32)|false|none|none|
|kinder|[[Kind](#schemakind)]|false|none|none|
|lebenshaltungsKostenMonatlich|number|false|none|none|
|obligo|[VermoegenVerbindlichkeiten](#schemavermoegenverbindlichkeiten)|false|none|Diese Angabe ist produktanbieterspezifisch, sie wird nicht von allen Produktanbietern bei der Angebotsermittlung berücksichtigt.|
|positionen|[HaushaltsPositionen](#schemahaushaltspositionen)|false|none|none|

<h2 id="tocShaushaltspositionen">HaushaltsPositionen</h2>

<a id="schemahaushaltspositionen"></a>

```json
{
  "bankUndSparguthaben": [
    {
      "aktuellerWert": 0,
      "ertrag": 0,
      "maximalAufzuloesenderWert": 0,
      "vermoegensEinsatz": "KEIN_EINSATZ",
      "vermoegensTyp": "VERMOEGEN",
      "zahlungsTyp": "EINNAHME",
      "zinsertragJaehrlich": 0,
      "zukuenftigeEinnahmen": 0
    }
  ],
  "bausparvertraege": [
    {
      "abschlussGebuehr": 0,
      "aktuellerWert": 0,
      "bausparSumme": 0,
      "einmalzahlung": 0,
      "ertrag": 0,
      "id": "string",
      "maximalAufzuloesenderBetrag": 0,
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "sonderZahlungen": [
        {
          "anzahl": 0,
          "betrag": 0,
          "termin": "2020-02-24",
          "zahlweise": "EINMALIG"
        }
      ],
      "sparBeitragMonatlich": 0,
      "tarif": "string",
      "typ": "string",
      "vermoegensEinsatz": "KEIN_EINSATZ",
      "vermoegensTyp": "VERMOEGEN",
      "vertragsBeginn": "2020-02-24",
      "vertragsNummer": "string",
      "verwaltungsgebuehrenJaehrlich": 0,
      "zahlungsTyp": "EINNAHME",
      "zukuenftigeEinnahmen": 0,
      "zuteilungsDatum": "2020-02-24"
    }
  ],
  "ehegattenUnterhalt": [
    {
      "einnahmenMonatlich": 0,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "einkuenfteAusNebentaetigkeit": [
    {
      "beginnDerNebentaetigkeit": "2020-02-24",
      "einnahmenMonatlich": 0,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "kindergeld": [
    {
      "einnahmenMonatlich": 0,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "lebensUndRentenVersicherungen": [
    {
      "id": "string",
      "maximalAufzuloesenderBetrag": 0,
      "praemieMonatlich": 0,
      "rueckkaufsWertAktuell": 0,
      "tarif": "string",
      "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
      "vermoegensEinsatz": "KEIN_EINSATZ",
      "vermoegensTyp": "VERMOEGEN",
      "versicherungsGesellschaft": "string",
      "versicherungsSumme": 0,
      "vertragsBeginn": "2020-02-24",
      "vertragsEnde": "2020-02-24",
      "vertragsNummer": "string",
      "verwaltungsgebuehrenJaehrlich": 0,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "mietAusgaben": [
    {
      "ausgabenMonatlich": 0,
      "berechnungsHilfeVermoegen": {
        "betragNachFinanzierung": 0,
        "betragVorFinanzierung": 0
      },
      "entfallenMitFinanzierung": true,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "privateDarlehen": [
    {
      "glaeubiger": "string",
      "laufzeitEnde": "2020-02-24",
      "rateMonatlich": 0,
      "restschuld": 0,
      "vermoegensTyp": "VERMOEGEN",
      "wirdAbgeloest": true,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "privateKrankenversicherung": [
    {
      "ausgabenMonatlich": 0,
      "berechnungsHilfeVermoegen": {
        "betragNachFinanzierung": 0,
        "betragVorFinanzierung": 0
      },
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "ratenkredite": [
    {
      "glaeubiger": "string",
      "laufzeitEnde": "2020-02-24",
      "rateMonatlich": 0,
      "restschuld": 0,
      "vermoegensTyp": "VERMOEGEN",
      "wirdAbgeloest": true,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "sonstigeAusgaben": [
    {
      "ausgabenMonatlich": 0,
      "berechnungsHilfeVermoegen": {
        "betragNachFinanzierung": 0,
        "betragVorFinanzierung": 0
      },
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "sonstigeEinnahmen": [
    {
      "einnahmenMonatlich": 0,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "sonstigeVerbindlichkeiten": [
    {
      "glaeubiger": "string",
      "laufzeitEnde": "2020-02-24",
      "rateMonatlich": 0,
      "restschuld": 0,
      "vermoegensTyp": "VERMOEGEN",
      "wirdAbgeloest": true,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "sonstigeVermoegen": [
    {
      "aktuellerWert": 0,
      "ertrag": 0,
      "maximalAufzuloesenderWert": 0,
      "vermoegensEinsatz": "KEIN_EINSATZ",
      "vermoegensTyp": "VERMOEGEN",
      "zukuenftigeEinnahmen": 0
    }
  ],
  "sparplaene": [
    {
      "aktuellerWert": 0,
      "beitragMonatlich": 0,
      "ertrag": 0,
      "maximalAufzuloesenderWert": 0,
      "vermoegensEinsatz": "KEIN_EINSATZ",
      "vermoegensTyp": "VERMOEGEN",
      "zahlungsTyp": "EINNAHME",
      "zukuenftigeEinnahmen": 0
    }
  ],
  "unbefristeteZusatzRenten": [
    {
      "einnahmenMonatlich": 0,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "unterhaltsVerpflichtungen": [
    {
      "ausgabenMonatlich": 0,
      "berechnungsHilfeVermoegen": {
        "betragNachFinanzierung": 0,
        "betragVorFinanzierung": 0
      },
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "variableEinkuenfte": [
    {
      "einnahmenMonatlich": 0,
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "versicherungsAusgaben": [
    {
      "ausgabenMonatlich": 0,
      "berechnungsHilfeVermoegen": {
        "betragNachFinanzierung": 0,
        "betragVorFinanzierung": 0
      },
      "zahlungsTyp": "EINNAHME"
    }
  ],
  "wertpapiere": [
    {
      "aktuellerWert": 0,
      "dividendenJaehrlich": 0,
      "ertrag": 0,
      "maximalAufzuloesenderWert": 0,
      "vermoegensEinsatz": "KEIN_EINSATZ",
      "vermoegensTyp": "VERMOEGEN",
      "zahlungsTyp": "EINNAHME",
      "zukuenftigeEinnahmen": 0
    }
  ]
}

```

*HaushaltsPositionen*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bankUndSparguthaben|[[BankUndSparguthaben](#schemabankundsparguthaben)]|false|none|none|
|bausparvertraege|[[BestehenderBausparvertrag](#schemabestehenderbausparvertrag)]|false|none|none|
|ehegattenUnterhalt|[[EinnahmenMonatlich](#schemaeinnahmenmonatlich)]|false|none|none|
|einkuenfteAusNebentaetigkeit|[[EinkuenfteAusNebentaetigkeit](#schemaeinkuenfteausnebentaetigkeit)]|false|none|none|
|kindergeld|[[EinnahmenMonatlich](#schemaeinnahmenmonatlich)]|false|none|Read-Only-Feld. Wird dynamisch aus den Angaben zu den Kindern berechnet. Pro kindergelderhaltendem Kind ein Listenelement.|
|lebensUndRentenVersicherungen|[[LebensOderRentenversicherungVermoegen](#schemalebensoderrentenversicherungvermoegen)]|false|none|none|
|mietAusgaben|[[MietAusgaben](#schemamietausgaben)]|false|none|none|
|privateDarlehen|[[Verbindlichkeit](#schemaverbindlichkeit)]|false|none|none|
|privateKrankenversicherung|[[AusgabenMonatlich](#schemaausgabenmonatlich)]|false|none|none|
|ratenkredite|[[Verbindlichkeit](#schemaverbindlichkeit)]|false|none|none|
|sonstigeAusgaben|[[AusgabenMonatlich](#schemaausgabenmonatlich)]|false|none|none|
|sonstigeEinnahmen|[[EinnahmenMonatlich](#schemaeinnahmenmonatlich)]|false|none|none|
|sonstigeVerbindlichkeiten|[[Verbindlichkeit](#schemaverbindlichkeit)]|false|none|none|
|sonstigeVermoegen|[[Vermoegen](#schemavermoegen)]|false|none|none|
|sparplaene|[[Sparplaene](#schemasparplaene)]|false|none|none|
|unbefristeteZusatzRenten|[[EinnahmenMonatlich](#schemaeinnahmenmonatlich)]|false|none|none|
|unterhaltsVerpflichtungen|[[AusgabenMonatlich](#schemaausgabenmonatlich)]|false|none|none|
|variableEinkuenfte|[[EinnahmenMonatlich](#schemaeinnahmenmonatlich)]|false|none|none|
|versicherungsAusgaben|[[AusgabenMonatlich](#schemaausgabenmonatlich)]|false|none|none|
|wertpapiere|[[Wertpapiere](#schemawertpapiere)]|false|none|none|

<h2 id="tocShoehederratepraeferenz">HoeheDerRatePraeferenz</h2>

<a id="schemahoehederratepraeferenz"></a>

```json
{
  "betrag": 0,
  "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
  "zusatzlicheKommentare": "string"
}

```

*HoeheDerRatePraeferenz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|betrag|number|false|none|none|
|praeferenzAuswahl|string|false|none|none|
|zusatzlicheKommentare|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praeferenzAuswahl|MEINE_MIETAUSGABEN_VON_HEUTE|
|praeferenzAuswahl|BETRAG|
|praeferenzAuswahl|MOEGLICHST_KLEIN|
|praeferenzAuswahl|VERFUEGBARES_EINKOMMEN_AUSSCHOEPFEN|
|praeferenzAuswahl|EGAL|

<h2 id="tocSimmobilieverknuepfung">ImmobilieVerknuepfung</h2>

<a id="schemaimmobilieverknuepfung"></a>

```json
{
  "id": "string"
}

```

*ImmobilieVerknuepfung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|

<h2 id="tocSkfwdarlehenswunsch">KfwDarlehensWunsch</h2>

<a id="schemakfwdarlehenswunsch"></a>

```json
{
  "darlehensBetrag": 0,
  "kfwEndfaellig": "NEIN",
  "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
  "kfwProgramm": "PROGRAMM_124",
  "laufzeitInJahren": 0,
  "provision": 0,
  "tilgungsWunsch": {
    "anfaenglicheTilgung": 0,
    "ausgesetztBerechnet": false,
    "ausgesetztEigenesAngebot": false,
    "bausparWunsch": {
      "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
      "bausparSummeAbsolut": 0,
      "bausparSummeRelativ": 0,
      "bausparTarif": [
        {
          "id": "string",
          "kurzName": "string",
          "langName": "string",
          "produktAnbieter": "string",
          "riesterFoerderung": true,
          "status": "AKTIV"
        }
      ],
      "bausparTarife": [
        "string"
      ],
      "id": "string",
      "sonderZahlungEinmalig": 0,
      "sonderZahlungen": [
        {
          "anzahl": 0,
          "betrag": 0,
          "termin": "2020-02-24",
          "zahlweise": "EINMALIG"
        }
      ],
      "sparBeginn": "2020-02-24",
      "sparBeitragMonatlichAbsolut": 0,
      "sparBeitragMonatlichRelativ": 0,
      "tilgungsBeitragMonatlich": 0,
      "vertragsPartnerIds": [
        "string"
      ],
      "verwendung": "ZINS_ABSICHERUNG",
      "zuteilungsDatum": "2020-02-24"
    },
    "rate": 0,
    "tilgungsBeginn": "2020-02-24",
    "tilgungsErsatzProduktId": "string",
    "volltilgerWennAnnuitaetenOderForward": false
  },
  "tilgungsfreieAnlaufjahre": 0,
  "zinsBindungInJahren": 0
}

```

*KfwDarlehensWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|darlehensBetrag|number|false|none|none|
|kfwEndfaellig|string|false|none|Für endfällige KfW-Darlehen wird die Quelle des Tilgungswunsches erfasst|
|kfwEnergieEffizienzStandard|string|false|none|Nur bei Programm 153. Wenn die KfW-Bank neue Standards anerkennt, sind die entsprechenden neuen Ausprägungen zulässig. Der Client muss daher mit unbekannten Werten umgehen können.|
|kfwProgramm|string|false|none|Bei neu aufgelegten KfW-Programmen können auch weitere Werte zulässig werden. Der Client muss daher mit unbekannten Werten umgehen können.|
|laufzeitInJahren|integer(int32)|false|none|none|
|provision|number|false|none|none|
|tilgungsWunsch|[TilgungsWunsch](#schematilgungswunsch)|false|none|Für endfällige KfW-Darlehen wird ein Tilgungswunsch erfasst|
|tilgungsfreieAnlaufjahre|integer(int32)|false|none|Erlaubt ist 1, 2, 3, 4, 5. Maximalwert abhängig von der Laufzeit. Wenn der Tilgungswunsch ausgesetzt ist, dann ist auch 10 erlaubt.|
|zinsBindungInJahren|integer(int32)|false|none|Programm 124: 5 oder 10, sonst: 10 oder 20|

##### Enumerated Values

|Property|Value|
|---|---|
|kfwEndfaellig|NEIN|
|kfwEndfaellig|ENDFAELLIG_BERECHNET|
|kfwEndfaellig|ENDFAELLIG_EIGENES_ANGEBOT|
|kfwEnergieEffizienzStandard|STANDARD_40_PLUS|
|kfwEnergieEffizienzStandard|STANDARD_40|
|kfwEnergieEffizienzStandard|STANDARD_55|
|kfwEnergieEffizienzStandard|STANDARD_70|
|kfwProgramm|PROGRAMM_124|
|kfwProgramm|PROGRAMM_141|
|kfwProgramm|PROGRAMM_151|
|kfwProgramm|PROGRAMM_152|
|kfwProgramm|PROGRAMM_153|
|kfwProgramm|PROGRAMM_155|
|kfwProgramm|PROGRAMM_159|
|kfwProgramm|PROGRAMM_167|

<h2 id="tocSkind">Kind</h2>

<a id="schemakind"></a>

```json
{
  "geburtsdatum": "2020-02-24",
  "id": "string",
  "kindergeldWirdBezogen": true,
  "name": "string",
  "unterhaltsEinnahmenBetragMonatlich": 0
}

```

*Kind*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|geburtsdatum|string(date)|false|none|none|
|id|string|false|none|none|
|kindergeldWirdBezogen|boolean|false|none|none|
|name|string|false|none|none|
|unterhaltsEinnahmenBetragMonatlich|number|false|none|none|

<h2 id="tocSlaufzeitpraeferenz">LaufzeitPraeferenz</h2>

<a id="schemalaufzeitpraeferenz"></a>

```json
{
  "bisZumJahr": "2016",
  "bisZurRenteImJahr": "2016",
  "inJahren": 0,
  "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
  "zusatzlicheKommentare": "string"
}

```

*LaufzeitPraeferenz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bisZumJahr|string|false|none|Nur relevant, wenn praeferenzAuswahl == BIS_ZUM_JAHR. Vierstellige Jahresangabe|
|bisZurRenteImJahr|string|false|none|Nur relevant, wenn praeferenzAuswahl == BIS_ZUR_RENTE_IM_JAHR. Vierstellige Jahresangabe|
|inJahren|integer(int32)|false|none|Nur relevant, wenn praeferenzAuswahl == IN_JAHREN.|
|praeferenzAuswahl|string|false|none|none|
|zusatzlicheKommentare|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praeferenzAuswahl|MOEGLICHST_SCHNELL|
|praeferenzAuswahl|IN_JAHREN|
|praeferenzAuswahl|BIS_ZUM_JAHR|
|praeferenzAuswahl|BIS_ZUR_RENTE_IM_JAHR|
|praeferenzAuswahl|EGAL|

<h2 id="tocSleadtracking">LeadTracking</h2>

<a id="schemaleadtracking"></a>

```json
{
  "kampagne": "string",
  "keyword": "string",
  "kundenBetreuerBenachrichtigen": true,
  "trackingId": "string"
}

```

*LeadTracking*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|kampagne|string|false|none|none|
|keyword|string|false|none|none|
|kundenBetreuerBenachrichtigen|boolean|false|none|none|
|trackingId|string|false|none|none|

<h2 id="tocSlebensoderrentenversicherungvermoegen">LebensOderRentenversicherungVermoegen</h2>

<a id="schemalebensoderrentenversicherungvermoegen"></a>

```json
{
  "id": "string",
  "maximalAufzuloesenderBetrag": 0,
  "praemieMonatlich": 0,
  "rueckkaufsWertAktuell": 0,
  "tarif": "string",
  "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
  "vermoegensEinsatz": "KEIN_EINSATZ",
  "vermoegensTyp": "VERMOEGEN",
  "versicherungsGesellschaft": "string",
  "versicherungsSumme": 0,
  "vertragsBeginn": "2020-02-24",
  "vertragsEnde": "2020-02-24",
  "vertragsNummer": "string",
  "verwaltungsgebuehrenJaehrlich": 0,
  "zahlungsTyp": "EINNAHME"
}

```

*LebensOderRentenversicherungVermoegen*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|maximalAufzuloesenderBetrag|number|false|none|none|
|praemieMonatlich|number|false|none|none|
|rueckkaufsWertAktuell|number|false|none|none|
|tarif|string|false|none|none|
|typ|string|false|none|none|
|vermoegensEinsatz|string|false|none|none|
|vermoegensTyp|string|false|none|Redundante Angabe des Vermögenstyp dient als zusätzliches Filterkriterium|
|versicherungsGesellschaft|string|false|none|none|
|versicherungsSumme|number|false|none|none|
|vertragsBeginn|string(date)|false|none|none|
|vertragsEnde|string(date)|false|none|none|
|vertragsNummer|string|false|none|none|
|verwaltungsgebuehrenJaehrlich|number|false|none|none|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|

##### Enumerated Values

|Property|Value|
|---|---|
|typ|KAPITALBILDENDE_LEBENSVERSICHERUNG|
|typ|FONDSGEBUNDENE_LEBENSVERSICHERUNG|
|typ|KAPITALBILDENDE_RENTENVERSICHERUNG|
|typ|FONDSGEBUNDENE_RENTENVERSICHERUNG|
|typ|RISIKO_LEBENSVERSICHERUNG|
|vermoegensEinsatz|KEIN_EINSATZ|
|vermoegensEinsatz|ABTRETEN|
|vermoegensEinsatz|AUFLOESEN|
|vermoegensTyp|VERMOEGEN|
|vermoegensTyp|VERBINDLICHKEIT|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSlegitimationsdaten">LegitimationsDaten</h2>

<a id="schemalegitimationsdaten"></a>

```json
{
  "ausstellendeBehoerde": "string",
  "ausstellungsdatum": "2020-02-24",
  "ausweisArt": "PERSONALAUSWEIS",
  "ausweisArtBeiAndererAusweis": "string",
  "ausweisNummer": "string"
}

```

*LegitimationsDaten*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ausstellendeBehoerde|string|false|none|none|
|ausstellungsdatum|string(date)|false|none|none|
|ausweisArt|string|false|none|none|
|ausweisArtBeiAndererAusweis|string|false|none|Nur wenn ausweisArt = ANDERE|
|ausweisNummer|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|ausweisArt|PERSONALAUSWEIS|
|ausweisArt|REISEPASS|
|ausweisArt|ANDERE|

<h2 id="tocSlink">Link</h2>

<a id="schemalink"></a>

```json
{
  "href": "string",
  "type": "string"
}

```

*Link*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|href|string|false|none|none|
|type|string|false|none|none|

<h2 id="tocSlinks">Links</h2>

<a id="schemalinks"></a>

```json
{
  "self": {
    "href": "string",
    "type": "string"
  }
}

```

*Links*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|self|[Link](#schemalink)|false|none|none|

<h2 id="tocSmeldung">Meldung</h2>

<a id="schemameldung"></a>

```json
{
  "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
  "kreditEntscheider": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "produktAnbieter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "produktAnbieterId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string"
  },
  "text": "string"
}

```

*Meldung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|kategorie|string|false|none|Neue Ausprägungen können kurzfristig hinzukommen. Der Client muss daher mit unbekannten Werten umgehen können.|
|kreditEntscheider|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|produktAnbieter|[ProduktAnbieter](#schemaproduktanbieter)|false|none|none|
|text|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|kategorie|AUSZAHLUNGS_VORAUSSETZUNG|
|kategorie|MACHBAR|
|kategorie|MACHBARKEITS_HINWEIS|
|kategorie|ANPASSUNG_KUNDENWUNSCH|
|kategorie|ANPASSUNG_VERTRIEBSWUNSCH|
|kategorie|UNBERUECKSICHTIGTE_ANGABE|
|kategorie|KONDITIONEN_UNTER_VORBEHALT_VOLLSTAENDIGER_DATEN|
|kategorie|KONDITIONEN_UNTER_VORBEHALT_EXTERNER_SCHNITTSTELLEN|
|kategorie|MACHBARKEIT_UNTER_VORBEHALT_VOLLSTAENDIGER_DATEN|
|kategorie|MACHBARKEIT_UNTER_VORBEHALT_EXTERNER_SCHNITTSTELLEN|
|kategorie|MACHBAR_UNTER_VORBEHALT_PRODUZENT|
|kategorie|NICHT_MACHBAR|
|kategorie|NICHT_ANBIETBAR|

<h2 id="tocSmietausgaben">MietAusgaben</h2>

<a id="schemamietausgaben"></a>

```json
{
  "ausgabenMonatlich": 0,
  "berechnungsHilfeVermoegen": {
    "betragNachFinanzierung": 0,
    "betragVorFinanzierung": 0
  },
  "entfallenMitFinanzierung": true,
  "zahlungsTyp": "EINNAHME"
}

```

*MietAusgaben*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ausgabenMonatlich|number|false|none|none|
|berechnungsHilfeVermoegen|[BerechnungsHilfeBetrag](#schemaberechnungshilfebetrag)|false|none|none|
|entfallenMitFinanzierung|boolean|false|none|none|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|

##### Enumerated Values

|Property|Value|
|---|---|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSmiteigentumsanteil">MiteigentumsAnteil</h2>

<a id="schemamiteigentumsanteil"></a>

```json
{
  "anteil": 0,
  "gesamt": 0
}

```

*MiteigentumsAnteil*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anteil|number(double)|false|none|none|
|gesamt|integer(int32)|false|none|none|

<h2 id="tocSmodernisierungsangaben">ModernisierungsAngaben</h2>

<a id="schemamodernisierungsangaben"></a>

```json
{
  "badWc": true,
  "bodenWandTreppe": true,
  "dach": true,
  "fenster": true,
  "heizungZentral": true,
  "modernisierungsGrad": "GERING",
  "modernisierungsJahr": "string",
  "raumaufteilung": true,
  "stromAbwasserHeizkoerper": true,
  "waermedaemmung": true,
  "wurdeModernisiert": true
}

```

*ModernisierungsAngaben*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|badWc|boolean|false|none|none|
|bodenWandTreppe|boolean|false|none|none|
|dach|boolean|false|none|none|
|fenster|boolean|false|none|none|
|heizungZentral|boolean|false|none|none|
|modernisierungsGrad|string|false|none|none|
|modernisierungsJahr|string|false|none|none|
|raumaufteilung|boolean|false|none|none|
|stromAbwasserHeizkoerper|boolean|false|none|none|
|waermedaemmung|boolean|false|none|none|
|wurdeModernisiert|boolean|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|modernisierungsGrad|GERING|
|modernisierungsGrad|MITTEL|
|modernisierungsGrad|HOCH|

<h2 id="tocSnachrangigesexternesdarlehen">NachrangigesExternesDarlehen</h2>

<a id="schemanachrangigesexternesdarlehen"></a>

```json
{
  "darlehensBetrag": 0,
  "darlehensGeber": "string",
  "id": "string",
  "laufzeitEnde": "2020-02-24",
  "rateMonatlich": 0,
  "typ": "ARBEITGEBERDARLEHEN",
  "zinsBindung": {
    "endetAm": "2020-02-24",
    "jahre": 0,
    "monate": 0,
    "restschuldNachZinsBindungsEnde": 0
  }
}

```

*NachrangigesExternesDarlehen*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|darlehensBetrag|number|false|none|none|
|darlehensGeber|string|false|none|Der Name des externen Darlehensgebers (Firmierung). Es gibt keine entsprechende Beziehung zu einem Partner auf der Europace-Plattform.|
|id|string|false|none|none|
|laufzeitEnde|string(date)|false|none|Wenn die Laufzeit bei einem externen Darlehen angegeben wurde, dann ist das Feld gesetzt.|
|rateMonatlich|number|false|none|none|
|typ|string|false|none|Neue Ausprägungen können kurzfristig hinzukommen. Der Client muss daher mit unbekannten Werten umgehen können.|
|zinsBindung|[ZinsBindung](#schemazinsbindung)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|typ|ARBEITGEBERDARLEHEN|
|typ|BAUSPARDARLEHEN|
|typ|OEFFENTLICHES_DARLEHEN|
|typ|RATENKREDIT|

<h2 id="tocSpaginationlinks">PaginationLinks</h2>

<a id="schemapaginationlinks"></a>

```json
{
  "next": {
    "href": "string",
    "type": "string"
  },
  "prev": {
    "href": "string",
    "type": "string"
  },
  "self": {
    "href": "string",
    "type": "string"
  }
}

```

*PaginationLinks*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|next|[Link](#schemalink)|false|none|none|
|prev|[Link](#schemalink)|false|none|none|
|self|[Link](#schemalink)|false|none|none|

<h2 id="tocSpartner">Partner</h2>

<a id="schemapartner"></a>

```json
{
  "anrede": "FRAU",
  "anschrift": {
    "hausnummer": "string",
    "ort": "string",
    "postleitzahl": "string",
    "strasse": "string"
  },
  "email": "string",
  "externePartnerId": "string",
  "externerKreditSachbearbeiterId": "string",
  "fax": "string",
  "firmenNameZusatz": "string",
  "firmierung": "string",
  "geburtsdatum": "2020-02-24",
  "id": "string",
  "kreditsachbearbeiter": true,
  "mobilTelefon": "string",
  "nachname": "string",
  "partnerId": "string",
  "telefonnummer": "string",
  "vertriebsOrganisation": {
    "firma": "string",
    "name": "string",
    "vertriebsOrganisationsId": "string"
  },
  "vorname": "string",
  "webseite": "string",
  "_links": {
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}

```

*Partner*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anrede|string|false|none|none|
|anschrift|[Postadresse](#schemapostadresse)|false|none|none|
|email|string|false|none|none|
|externePartnerId|string|false|none|none|
|externerKreditSachbearbeiterId|string|false|none|none|
|fax|string|false|none|none|
|firmenNameZusatz|string|false|none|none|
|firmierung|string|false|none|none|
|geburtsdatum|string(date)|false|none|none|
|id|string|false|none|none|
|kreditsachbearbeiter|boolean|false|none|none|
|mobilTelefon|string|false|none|none|
|nachname|string|false|none|none|
|partnerId|string|false|none|none|
|telefonnummer|string|false|none|none|
|vertriebsOrganisation|[VertriebsOrganisation](#schemavertriebsorganisation)|false|none|none|
|vorname|string|false|none|none|
|webseite|string|false|none|none|
|_links|[Links](#schemalinks)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|anrede|FRAU|
|anrede|HERR|

<h2 id="tocSpartnerdto">PartnerDTO</h2>

<a id="schemapartnerdto"></a>

```json
{
  "partnerId": "string"
}

```

*PartnerDTO*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|partnerId|string|false|none|none|

<h2 id="tocSpatchoperation">PatchOperation</h2>

<a id="schemapatchoperation"></a>

```json
{
  "from": "string",
  "op": "add",
  "path": "string",
  "value": {}
}

```

*PatchOperation*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|from|string|false|none|none|
|op|string|false|none|none|
|path|string|false|none|none|
|value|object|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|op|add|
|op|remove|
|op|replace|
|op|move|
|op|copy|
|op|test|

<h2 id="tocSpostadresse">Postadresse</h2>

<a id="schemapostadresse"></a>

```json
{
  "hausnummer": "string",
  "ort": "string",
  "postleitzahl": "string",
  "strasse": "string"
}

```

*Postadresse*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|hausnummer|string|false|none|none|
|ort|string|false|none|none|
|postleitzahl|string|false|none|none|
|strasse|string|false|none|none|

<h2 id="tocSpraeferenzen">Praeferenzen</h2>

<a id="schemapraeferenzen"></a>

```json
{
  "bereitstellungsZinsFreieZeit": {
    "darlehenBenoetigtInMonaten": 0,
    "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
    "zusatzlicheKommentare": "string"
  },
  "bestandteileDerFinanzierung": {
    "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
    "zusatzlicheKommentare": "string"
  },
  "hoeheDerRate": {
    "betrag": 0,
    "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
    "zusatzlicheKommentare": "string"
  },
  "laufzeit": {
    "bisZumJahr": "2016",
    "bisZurRenteImJahr": "2016",
    "inJahren": 0,
    "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
    "zusatzlicheKommentare": "string"
  },
  "sondertilgung": {
    "betragEinmalig": 0,
    "betragJaehrlich": 0,
    "praeferenzAuswahl": "JAEHRLICH",
    "zusatzlicheKommentare": "string"
  },
  "tilgungsSatzWechsel": {
    "mindestensBenoetigt": 0,
    "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
    "zusatzlicheKommentare": "string"
  },
  "weiterePraeferenz": "string",
  "zeitlicherRahmen": {
    "finanzierungszusageBis": "2020-02-24",
    "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
    "zusatzlicheKommentare": "string"
  },
  "zinsBindung": {
    "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
    "zinsBindungBisJahren": 0,
    "zinsBindungVonJahren": 0,
    "zinsBindungZwischenJahren": 0,
    "zusatzlicheKommentare": "string"
  }
}

```

*Praeferenzen*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bereitstellungsZinsFreieZeit|[BereitstellungsZinsFreieZeitPraeferenz](#schemabereitstellungszinsfreiezeitpraeferenz)|false|none|none|
|bestandteileDerFinanzierung|[BestandteileDerFinanzierungPraeferenz](#schemabestandteilederfinanzierungpraeferenz)|false|none|none|
|hoeheDerRate|[HoeheDerRatePraeferenz](#schemahoehederratepraeferenz)|false|none|none|
|laufzeit|[LaufzeitPraeferenz](#schemalaufzeitpraeferenz)|false|none|none|
|sondertilgung|[SondertilgungPraeferenz](#schemasondertilgungpraeferenz)|false|none|none|
|tilgungsSatzWechsel|[TilgungsSatzWechselPraeferenz](#schematilgungssatzwechselpraeferenz)|false|none|none|
|weiterePraeferenz|string|false|none|none|
|zeitlicherRahmen|[ZeitlicherRahmenPraeferenz](#schemazeitlicherrahmenpraeferenz)|false|none|none|
|zinsBindung|[ZinsBindungPraeferenz](#schemazinsbindungpraeferenz)|false|none|none|

<h2 id="tocSprivatdarlehenswunsch">PrivatDarlehensWunsch</h2>

<a id="schemaprivatdarlehenswunsch"></a>

```json
{
  "darlehensBetrag": 0,
  "laufzeitInMonaten": 0,
  "provision": 0
}

```

*PrivatDarlehensWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|darlehensBetrag|number|false|none|none|
|laufzeitInMonaten|integer(int32)|false|none|none|
|provision|number|false|none|none|

<h2 id="tocSproduktanbieter">ProduktAnbieter</h2>

<a id="schemaproduktanbieter"></a>

```json
{
  "anrede": "FRAU",
  "anschrift": {
    "hausnummer": "string",
    "ort": "string",
    "postleitzahl": "string",
    "strasse": "string"
  },
  "email": "string",
  "externePartnerId": "string",
  "externerKreditSachbearbeiterId": "string",
  "fax": "string",
  "firmenNameZusatz": "string",
  "firmierung": "string",
  "geburtsdatum": "2020-02-24",
  "id": "string",
  "kreditsachbearbeiter": true,
  "mobilTelefon": "string",
  "nachname": "string",
  "partnerId": "string",
  "produktAnbieterId": "string",
  "telefonnummer": "string",
  "vertriebsOrganisation": {
    "firma": "string",
    "name": "string",
    "vertriebsOrganisationsId": "string"
  },
  "vorname": "string",
  "webseite": "string"
}

```

*ProduktAnbieter*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anrede|string|false|none|none|
|anschrift|[Postadresse](#schemapostadresse)|false|none|none|
|email|string|false|none|none|
|externePartnerId|string|false|none|none|
|externerKreditSachbearbeiterId|string|false|none|none|
|fax|string|false|none|none|
|firmenNameZusatz|string|false|none|none|
|firmierung|string|false|none|none|
|geburtsdatum|string(date)|false|none|none|
|id|string|false|none|none|
|kreditsachbearbeiter|boolean|false|none|none|
|mobilTelefon|string|false|none|none|
|nachname|string|false|none|none|
|partnerId|string|false|none|none|
|produktAnbieterId|string|false|none|none|
|telefonnummer|string|false|none|none|
|vertriebsOrganisation|[VertriebsOrganisation](#schemavertriebsorganisation)|false|none|none|
|vorname|string|false|none|none|
|webseite|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|anrede|FRAU|
|anrede|HERR|

<h2 id="tocSrechteabteilung2">RechteAbteilung2</h2>

<a id="schemarechteabteilung2"></a>

```json
{
  "beschreibung": "string",
  "betrag": 0,
  "vorhanden": true
}

```

*RechteAbteilung2*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|beschreibung|string|false|none|none|
|betrag|number|false|none|none|
|vorhanden|boolean|false|none|none|

<h2 id="tocSrisikoabsicherung">RisikoAbsicherung</h2>

<a id="schemarisikoabsicherung"></a>

```json
{
  "abgesichertesRisiko": "TODESFALL",
  "auszahlungsBetrag": 0,
  "auszahlungsTurnus": "EINMALIG",
  "praemienAnteil": 0
}

```

*RisikoAbsicherung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abgesichertesRisiko|string|false|none|none|
|auszahlungsBetrag|number|false|none|none|
|auszahlungsTurnus|string|false|none|none|
|praemienAnteil|number|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|abgesichertesRisiko|TODESFALL|
|abgesichertesRisiko|ARBEITSLOSIGKEIT|
|abgesichertesRisiko|ARBEITSUNFAEHIGKEIT|
|abgesichertesRisiko|INVALIDITAET|
|auszahlungsTurnus|EINMALIG|
|auszahlungsTurnus|MONATLICH|
|auszahlungsTurnus|VIERTELJAEHRLICH|
|auszahlungsTurnus|HALBJAEHRLICH|
|auszahlungsTurnus|JAEHRLICH|

<h2 id="tocSrisikoabsicherungswunsch">RisikoAbsicherungsWunsch</h2>

<a id="schemarisikoabsicherungswunsch"></a>

```json
{
  "abzusicherndesRisiko": "TODESFALL",
  "versicherteRate": 0,
  "versicherungsSumme": 0
}

```

*RisikoAbsicherungsWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|abzusicherndesRisiko|string|false|none|none|
|versicherteRate|number|false|none|nur bei abzusicherndesRisiko==ARBEITSUNFAEHIGKEIT,ARBEITSLOSIGKEIT|
|versicherungsSumme|number|false|none|nur bei abzusicherndesRisiko==TODESFALL|

##### Enumerated Values

|Property|Value|
|---|---|
|abzusicherndesRisiko|TODESFALL|
|abzusicherndesRisiko|ARBEITSUNFAEHIGKEIT|
|abzusicherndesRisiko|ARBEITSLOSIGKEIT|

<h2 id="tocSschufaergebnis">SchufaErgebnis</h2>

<a id="schemaschufaergebnis"></a>

```json
{
  "antragstellerUnbekannt": false,
  "inManuellerNachbehandlung": false,
  "score": "string"
}

```

*SchufaErgebnis*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|antragstellerUnbekannt|boolean|false|none|Der Antragsteller ist bei der Schufa unbekannt.|
|inManuellerNachbehandlung|boolean|false|none|Die Ermittlung des Schufa-Scores verzögert sich, wenn sich die Anfrage bei der Schufa in manueller Nachbehandlung befindet.|
|score|string|false|none|none|

<h2 id="tocSselfrelandereignisse">SelfRelAndEreignisse</h2>

<a id="schemaselfrelandereignisse"></a>

```json
{
  "antraege": {
    "href": "string",
    "type": "string"
  },
  "ereignisse": {
    "href": "string",
    "type": "string"
  },
  "self": {
    "href": "string",
    "type": "string"
  }
}

```

*SelfRelAndEreignisse*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|antraege|[Link](#schemalink)|false|none|none|
|ereignisse|[Link](#schemalink)|false|none|none|
|self|[Link](#schemalink)|false|none|none|

<h2 id="tocSsituationnachrenteneintritt">SituationNachRenteneintritt</h2>

<a id="schemasituationnachrenteneintritt"></a>

```json
{
  "gesetzlicheRenteMonatlich": 0,
  "privateRenteMonatlich": 0,
  "rentenBeginn": "2020-02-24",
  "sonstigesEinkommenMonatlich": 0
}

```

*SituationNachRenteneintritt*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|gesetzlicheRenteMonatlich|number|false|none|none|
|privateRenteMonatlich|number|false|none|none|
|rentenBeginn|string(date)|false|none|none|
|sonstigesEinkommenMonatlich|number|false|none|none|

<h2 id="tocSsonderzahlung">SonderZahlung</h2>

<a id="schemasonderzahlung"></a>

```json
{
  "anzahl": 0,
  "betrag": 0,
  "termin": "2020-02-24",
  "zahlweise": "EINMALIG"
}

```

*SonderZahlung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anzahl|integer(int32)|false|none|Gesamtanzahl der Zahlungen|
|betrag|number|false|none|Betrag in EUR über die Höhe der einzelnen Zahlung|
|termin|string(date)|false|none|Termin der Einmalzahlung (optional) oder Beginn der regelmäßigen Zahlungen|
|zahlweise|string|false|none|Festlegung von einmaligen oder regelmäßigen Zahlungen|

##### Enumerated Values

|Property|Value|
|---|---|
|zahlweise|EINMALIG|
|zahlweise|MONATLICH|
|zahlweise|VIERTELJAEHRLICH|
|zahlweise|HALBJAEHRLICH|
|zahlweise|JAEHRLICH|

<h2 id="tocSsondertilgungpraeferenz">SondertilgungPraeferenz</h2>

<a id="schemasondertilgungpraeferenz"></a>

```json
{
  "betragEinmalig": 0,
  "betragJaehrlich": 0,
  "praeferenzAuswahl": "JAEHRLICH",
  "zusatzlicheKommentare": "string"
}

```

*SondertilgungPraeferenz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|betragEinmalig|number|false|none|wenn praeferenzAuswahl == EINMALIG|
|betragJaehrlich|number|false|none|wenn praeferenzAuswahl == JAEHRLICH|
|praeferenzAuswahl|string|false|none|none|
|zusatzlicheKommentare|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praeferenzAuswahl|JAEHRLICH|
|praeferenzAuswahl|EINMALIG|
|praeferenzAuswahl|DERZEIT_NICHT_GEPLANT|
|praeferenzAuswahl|EGAL|

<h2 id="tocSsparphase">SparPhase</h2>

<a id="schemasparphase"></a>

```json
{
  "guthabenBeiZuteilung": 0,
  "sparBeitragMonatlich": 0,
  "sparPhaseInJahren": 0
}

```

*SparPhase*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|guthabenBeiZuteilung|number|false|none|none|
|sparBeitragMonatlich|number|false|none|none|
|sparPhaseInJahren|integer(int32)|false|none|none|

<h2 id="tocSsparplaene">Sparplaene</h2>

<a id="schemasparplaene"></a>

```json
{
  "aktuellerWert": 0,
  "beitragMonatlich": 0,
  "ertrag": 0,
  "maximalAufzuloesenderWert": 0,
  "vermoegensEinsatz": "KEIN_EINSATZ",
  "vermoegensTyp": "VERMOEGEN",
  "zahlungsTyp": "EINNAHME",
  "zukuenftigeEinnahmen": 0
}

```

*Sparplaene*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|aktuellerWert|number|false|none|none|
|beitragMonatlich|number|false|none|none|
|ertrag|number|false|none|none|
|maximalAufzuloesenderWert|number|false|none|none|
|vermoegensEinsatz|string|false|none|none|
|vermoegensTyp|string|false|none|Redundante Angabe des Vermögenstyp dient als zusätzliches Filterkriterium|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|
|zukuenftigeEinnahmen|number|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|vermoegensEinsatz|KEIN_EINSATZ|
|vermoegensEinsatz|ABTRETEN|
|vermoegensEinsatz|AUFLOESEN|
|vermoegensTyp|VERMOEGEN|
|vermoegensTyp|VERBINDLICHKEIT|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSstaat">Staat</h2>

<a id="schemastaat"></a>

```json
{
  "isoCountryCode": "string",
  "name": "string"
}

```

*Staat*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|isoCountryCode|string|false|none|none|
|name|string|false|none|none|

<h2 id="tocSstatusdto">StatusDTO</h2>

<a id="schemastatusdto"></a>

```json
{
  "ablehnungsgrund": "FINANZIELLE_SITUATION",
  "antragsteller": "BEANTRAGT",
  "kommentar": "string",
  "produktAnbieter": "NICHT_BEARBEITET"
}

```

*StatusDTO*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ablehnungsgrund|string|false|none|none|
|antragsteller|string|true|none|none|
|kommentar|string|false|none|none|
|produktAnbieter|string|true|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|ablehnungsgrund|FINANZIELLE_SITUATION|
|ablehnungsgrund|NEGATIV_MERKMAL|
|ablehnungsgrund|WERTERMITTLUNG|
|ablehnungsgrund|KRITERIEN|
|ablehnungsgrund|UNTERLAGEN_UNVOLLSTAENDIG|
|ablehnungsgrund|GEGENANGEBOT|
|ablehnungsgrund|KEINE_ANGABE|
|antragsteller|BEANTRAGT|
|antragsteller|UNTERSCHRIEBEN|
|antragsteller|NICHT_ANGENOMMEN|
|antragsteller|WIDERRUFEN|
|produktAnbieter|NICHT_BEARBEITET|
|produktAnbieter|UNTERSCHRIEBEN|
|produktAnbieter|ABGELEHNT|
|produktAnbieter|ZURUECKGESTELLT|

<h2 id="tocStilgung">Tilgung</h2>

<a id="schematilgung"></a>

```json
{
  "anfaenglicheTilgung": 0,
  "sonderTilgungJaehrlich": 0,
  "tilgungsBeginnAm": "2020-02-24",
  "tilgungsErsatz": {
    "id": "string",
    "typ": "string"
  }
}

```

*Tilgung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anfaenglicheTilgung|number|false|none|wenn null oder 0: tilgungsausgesetzt|
|sonderTilgungJaehrlich|number|false|none|nur wenn darlehensArt IN [ANNUITAETEN_DARLEHEN,FORWARD_DARLEHEN] und KEIN tilgungsErsatz|
|tilgungsBeginnAm|string(date)|false|none|nullable|
|tilgungsErsatz|[TilgungsErsatz](#schematilgungsersatz)|false|none|nicht bei PRIVAT_DARLEHEN|

<h2 id="tocStilgungsersatz">TilgungsErsatz</h2>

<a id="schematilgungsersatz"></a>

```json
{
  "id": "string",
  "typ": "string"
}

```

*TilgungsErsatz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|Id des Tilgungsersatzproduktes, das in den Vermögenswerten des Haushalts oder in den Bausparangeboten des Angebotes zu finden ist.|
|typ|string|false|none|Menschenlesbarer Hinweis auf den Typ, z.B. BAUSPARVERTRAG oder KAPITALBILDENDE_LEBENSVERSICHERUNG|

<h2 id="tocStilgungsphase">TilgungsPhase</h2>

<a id="schematilgungsphase"></a>

```json
{
  "bausparDarlehenSumme": 0,
  "sollZinsNachZuteilung": 0,
  "tilgungsBeitragMonatlich": 0,
  "tilgungsPhaseInJahren": 0
}

```

*TilgungsPhase*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bausparDarlehenSumme|number|false|none|none|
|sollZinsNachZuteilung|number|false|none|none|
|tilgungsBeitragMonatlich|number|false|none|none|
|tilgungsPhaseInJahren|integer(int32)|false|none|none|

<h2 id="tocStilgungssatzwechselpraeferenz">TilgungsSatzWechselPraeferenz</h2>

<a id="schematilgungssatzwechselpraeferenz"></a>

```json
{
  "mindestensBenoetigt": 0,
  "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
  "zusatzlicheKommentare": "string"
}

```

*TilgungsSatzWechselPraeferenz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|mindestensBenoetigt|integer(int32)|false|none|wenn praeferenzAuswahl == MINDESTENS_BENOETIGT|
|praeferenzAuswahl|string|false|none|none|
|zusatzlicheKommentare|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praeferenzAuswahl|MINDESTENS_BENOETIGT|
|praeferenzAuswahl|NICHT_EINGEPLANT_ODER_ABSEHBAR|
|praeferenzAuswahl|EGAL|

<h2 id="tocStilgungswunsch">TilgungsWunsch</h2>

<a id="schematilgungswunsch"></a>

```json
{
  "anfaenglicheTilgung": 0,
  "ausgesetztBerechnet": false,
  "ausgesetztEigenesAngebot": false,
  "bausparWunsch": {
    "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
    "bausparSummeAbsolut": 0,
    "bausparSummeRelativ": 0,
    "bausparTarif": [
      {
        "id": "string",
        "kurzName": "string",
        "langName": "string",
        "produktAnbieter": "string",
        "riesterFoerderung": true,
        "status": "AKTIV"
      }
    ],
    "bausparTarife": [
      "string"
    ],
    "id": "string",
    "sonderZahlungEinmalig": 0,
    "sonderZahlungen": [
      {
        "anzahl": 0,
        "betrag": 0,
        "termin": "2020-02-24",
        "zahlweise": "EINMALIG"
      }
    ],
    "sparBeginn": "2020-02-24",
    "sparBeitragMonatlichAbsolut": 0,
    "sparBeitragMonatlichRelativ": 0,
    "tilgungsBeitragMonatlich": 0,
    "vertragsPartnerIds": [
      "string"
    ],
    "verwendung": "ZINS_ABSICHERUNG",
    "zuteilungsDatum": "2020-02-24"
  },
  "rate": 0,
  "tilgungsBeginn": "2020-02-24",
  "tilgungsErsatzProduktId": "string",
  "volltilgerWennAnnuitaetenOderForward": false
}

```

*TilgungsWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anfaenglicheTilgung|number|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|ausgesetztBerechnet|boolean|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|ausgesetztEigenesAngebot|boolean|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|bausparWunsch|[BausparWunsch](#schemabausparwunsch)|false|none|Von den Feldern bausparSummeAbsolut, bausparSummeRelativ, sparBeitragMonatlichAbsolut, sparBeitragMonatlichRelativ, tilgungsBeitragMonatlich, zuteilungsDatum und sparBeginn können maximal drei befüllt sein.|
|rate|number|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|
|tilgungsBeginn|string(date)|false|none|none|
|tilgungsErsatzProduktId|string|false|none|none|
|volltilgerWennAnnuitaetenOderForward|boolean|false|none|muss leer sein, wenn eines der anderen Attribute gefüllt ist|

<h2 id="tocSvariablesdarlehenswunsch">VariablesDarlehensWunsch</h2>

<a id="schemavariablesdarlehenswunsch"></a>

```json
{
  "darlehensBetrag": 0,
  "provision": 0,
  "tilgungsWunsch": {
    "anfaenglicheTilgung": 0,
    "ausgesetztBerechnet": false,
    "ausgesetztEigenesAngebot": false,
    "bausparWunsch": {
      "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
      "bausparSummeAbsolut": 0,
      "bausparSummeRelativ": 0,
      "bausparTarif": [
        {
          "id": "string",
          "kurzName": "string",
          "langName": "string",
          "produktAnbieter": "string",
          "riesterFoerderung": true,
          "status": "AKTIV"
        }
      ],
      "bausparTarife": [
        "string"
      ],
      "id": "string",
      "sonderZahlungEinmalig": 0,
      "sonderZahlungen": [
        {
          "anzahl": 0,
          "betrag": 0,
          "termin": "2020-02-24",
          "zahlweise": "EINMALIG"
        }
      ],
      "sparBeginn": "2020-02-24",
      "sparBeitragMonatlichAbsolut": 0,
      "sparBeitragMonatlichRelativ": 0,
      "tilgungsBeitragMonatlich": 0,
      "vertragsPartnerIds": [
        "string"
      ],
      "verwendung": "ZINS_ABSICHERUNG",
      "zuteilungsDatum": "2020-02-24"
    },
    "rate": 0,
    "tilgungsBeginn": "2020-02-24",
    "tilgungsErsatzProduktId": "string",
    "volltilgerWennAnnuitaetenOderForward": false
  }
}

```

*VariablesDarlehensWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|darlehensBetrag|number|false|none|none|
|provision|number|false|none|none|
|tilgungsWunsch|[TilgungsWunsch](#schematilgungswunsch)|false|none|none|

<h2 id="tocSverbindlichkeit">Verbindlichkeit</h2>

<a id="schemaverbindlichkeit"></a>

```json
{
  "glaeubiger": "string",
  "laufzeitEnde": "2020-02-24",
  "rateMonatlich": 0,
  "restschuld": 0,
  "vermoegensTyp": "VERMOEGEN",
  "wirdAbgeloest": true,
  "zahlungsTyp": "EINNAHME"
}

```

*Verbindlichkeit*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|glaeubiger|string|false|none|none|
|laufzeitEnde|string(date)|false|none|none|
|rateMonatlich|number|false|none|none|
|restschuld|number|false|none|none|
|vermoegensTyp|string|false|none|Redundante Angabe des Vermögenstyp dient als zusätzliches Filterkriterium|
|wirdAbgeloest|boolean|false|none|none|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|

##### Enumerated Values

|Property|Value|
|---|---|
|vermoegensTyp|VERMOEGEN|
|vermoegensTyp|VERBINDLICHKEIT|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSvermietungsinformationen">VermietungsInformationen</h2>

<a id="schemavermietungsinformationen"></a>

```json
{
  "mieteinnahmenNettoKaltMonatlich": 0,
  "nutzungsArt": "EIGENGENUTZT",
  "vermieteteFlaeche": 0
}

```

*VermietungsInformationen*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|mieteinnahmenNettoKaltMonatlich|number|false|none|none|
|nutzungsArt|string|false|none|none|
|vermieteteFlaeche|number|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|nutzungsArt|EIGENGENUTZT|
|nutzungsArt|TEIL_VERMIETET|
|nutzungsArt|VERMIETET|

<h2 id="tocSvermoegen">Vermoegen</h2>

<a id="schemavermoegen"></a>

```json
{
  "aktuellerWert": 0,
  "ertrag": 0,
  "maximalAufzuloesenderWert": 0,
  "vermoegensEinsatz": "KEIN_EINSATZ",
  "vermoegensTyp": "VERMOEGEN",
  "zukuenftigeEinnahmen": 0
}

```

*Vermoegen*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|aktuellerWert|number|false|none|none|
|ertrag|number|false|none|none|
|maximalAufzuloesenderWert|number|false|none|none|
|vermoegensEinsatz|string|false|none|none|
|vermoegensTyp|string|false|none|Redundante Angabe des Vermögenstyp dient als zusätzliches Filterkriterium|
|zukuenftigeEinnahmen|number|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|vermoegensEinsatz|KEIN_EINSATZ|
|vermoegensEinsatz|ABTRETEN|
|vermoegensEinsatz|AUFLOESEN|
|vermoegensTyp|VERMOEGEN|
|vermoegensTyp|VERBINDLICHKEIT|

<h2 id="tocSvermoegenverbindlichkeit">VermoegenVerbindlichkeit</h2>

<a id="schemavermoegenverbindlichkeit"></a>

```json
{
  "aktuellerWert": 0,
  "anrechnungFuerBlankoAnteil": 0,
  "bezeichner": "string",
  "kontonummer": "string",
  "vermoegensTyp": "VERMOEGEN"
}

```

*VermoegenVerbindlichkeit*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|aktuellerWert|number|false|none|none|
|anrechnungFuerBlankoAnteil|number|false|none|none|
|bezeichner|string|false|none|none|
|kontonummer|string|false|none|none|
|vermoegensTyp|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|vermoegensTyp|VERMOEGEN|
|vermoegensTyp|VERBINDLICHKEIT|

<h2 id="tocSvermoegenverbindlichkeiten">VermoegenVerbindlichkeiten</h2>

<a id="schemavermoegenverbindlichkeiten"></a>

```json
{
  "vermoegenOderVerbindlichkeiten": [
    {
      "aktuellerWert": 0,
      "anrechnungFuerBlankoAnteil": 0,
      "bezeichner": "string",
      "kontonummer": "string",
      "vermoegensTyp": "VERMOEGEN"
    }
  ]
}

```

*VermoegenVerbindlichkeiten*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|vermoegenOderVerbindlichkeiten|[[VermoegenVerbindlichkeit](#schemavermoegenverbindlichkeit)]|false|none|none|

<h2 id="tocSversicherungswunsch">VersicherungsWunsch</h2>

<a id="schemaversicherungswunsch"></a>

```json
{
  "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
  "id": "string",
  "praemienZahlungsweise": "EINMALIG",
  "risikoAbsicherungsWuensche": [
    {
      "abzusicherndesRisiko": "TODESFALL",
      "versicherteRate": 0,
      "versicherungsSumme": 0
    }
  ],
  "versichertePersonId": "string",
  "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
  "versicherungsBeginn": "2020-02-24",
  "versicherungsDauerInMonaten": 0
}

```

*VersicherungsWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|finanzierungsWeise|string|false|none|nur bei praemienZahlungsweise==EINMALIG|
|id|string|false|none|none|
|praemienZahlungsweise|string|false|none|none|
|risikoAbsicherungsWuensche|[[RisikoAbsicherungsWunsch](#schemarisikoabsicherungswunsch)]|false|none|none|
|versichertePersonId|string|false|none|none|
|versicherungsArt|string|false|none|none|
|versicherungsBeginn|string(date)|false|none|none|
|versicherungsDauerInMonaten|integer(int32)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|finanzierungsWeise|DURCH_HAUPTDARLEHEN|
|finanzierungsWeise|INDIVIDUELL|
|praemienZahlungsweise|EINMALIG|
|praemienZahlungsweise|MONATLICH|
|praemienZahlungsweise|VIERTELJAEHRLICH|
|praemienZahlungsweise|HALBJAEHRLICH|
|praemienZahlungsweise|JAEHRLICH|
|versicherungsArt|RATENSCHUTZVERSICHERUNG|

<h2 id="tocSversicherungszeitraum">VersicherungsZeitraum</h2>

<a id="schemaversicherungszeitraum"></a>

```json
{
  "beginn": "2020-02-24",
  "dauerInMonaten": 0,
  "ende": "2020-02-24"
}

```

*VersicherungsZeitraum*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|beginn|string(date)|false|none|none|
|dauerInMonaten|integer(int32)|false|none|none|
|ende|string(date)|false|none|none|

<h2 id="tocSvertriebsorganisation">VertriebsOrganisation</h2>

<a id="schemavertriebsorganisation"></a>

```json
{
  "firma": "string",
  "name": "string",
  "vertriebsOrganisationsId": "string"
}

```

*VertriebsOrganisation*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|firma|string|false|none|none|
|name|string|false|none|none|
|vertriebsOrganisationsId|string|false|none|none|

<h2 id="tocSvorgaenge">Vorgaenge</h2>

<a id="schemavorgaenge"></a>

```json
{
  "vorgaenge": [
    {
      "datenKontext": "TEST_MODUS",
      "externeVorgangsNummer": "string",
      "letzteAenderung": "2020-02-24T11:55:47Z",
      "letztesEreignis": "2020-02-24T11:55:47Z",
      "vorgangsNummer": "string",
      "_links": {
        "self": {
          "href": "string",
          "type": "string"
        }
      }
    }
  ],
  "_links": {
    "next": {
      "href": "string",
      "type": "string"
    },
    "prev": {
      "href": "string",
      "type": "string"
    },
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}

```

*Vorgaenge*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|vorgaenge|[[VorgaengeResourceListItem](#schemavorgaengeresourcelistitem)]|false|none|none|
|_links|[PaginationLinks](#schemapaginationlinks)|false|none|none|

<h2 id="tocSvorgaengeresourcelistitem">VorgaengeResourceListItem</h2>

<a id="schemavorgaengeresourcelistitem"></a>

```json
{
  "datenKontext": "TEST_MODUS",
  "externeVorgangsNummer": "string",
  "letzteAenderung": "2020-02-24T11:55:47Z",
  "letztesEreignis": "2020-02-24T11:55:47Z",
  "vorgangsNummer": "string",
  "_links": {
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}

```

*VorgaengeResourceListItem*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|datenKontext|string|false|none|none|
|externeVorgangsNummer|string|false|none|none|
|letzteAenderung|string(date-time)|false|none|none|
|letztesEreignis|string(date-time)|false|none|none|
|vorgangsNummer|string|false|none|none|
|_links|[Links](#schemalinks)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|datenKontext|TEST_MODUS|
|datenKontext|ECHT_GESCHAEFT|

<h2 id="tocSvorgang">Vorgang</h2>

<a id="schemavorgang"></a>

```json
{
  "antraege": [
    {
      "angebot": {
        "absicherungen": [
          {
            "abgesicherteRisiken": [
              {
                "abgesichertesRisiko": "TODESFALL",
                "auszahlungsBetrag": 0,
                "auszahlungsTurnus": "EINMALIG",
                "praemienAnteil": 0
              }
            ],
            "gesamtPraemie": 0,
            "praemienZahlungsweise": "EINMALIG",
            "tarifBezeichnung": "string",
            "tarifKennung": "string",
            "versichertePersonId": "string",
            "versicherungsArt": "string",
            "versicherungsNummer": "string",
            "versicherungsZeitraum": {
              "beginn": "2020-02-24",
              "dauerInMonaten": 0,
              "ende": "2020-02-24"
            }
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "angebotsHinweisFuerAntragsteller": "string",
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "gesamtLaufzeitInJahren": 0,
            "id": "string",
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparPhase": {
              "guthabenBeiZuteilung": 0,
              "sparBeitragMonatlich": 0,
              "sparPhaseInJahren": 0
            },
            "tarif": "string",
            "tilgungsPhase": {
              "bausparDarlehenSumme": 0,
              "sollZinsNachZuteilung": 0,
              "tilgungsBeitragMonatlich": 0,
              "tilgungsPhaseInJahren": 0
            },
            "typ": "string",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "beleihungsRechnung": {
          "beleihungsAuslauf": 0,
          "beleihungsWerte": [
            {
              "beleihungsWert": 0,
              "immobilie": {
                "id": "string"
              }
            }
          ],
          "beleihungsWerteSumme": 0,
          "produktAnbieter": {
            "anrede": "FRAU",
            "anschrift": {
              "hausnummer": "string",
              "ort": "string",
              "postleitzahl": "string",
              "strasse": "string"
            },
            "email": "string",
            "externePartnerId": "string",
            "externerKreditSachbearbeiterId": "string",
            "fax": "string",
            "firmenNameZusatz": "string",
            "firmierung": "string",
            "geburtsdatum": "2020-02-24",
            "id": "string",
            "kreditsachbearbeiter": true,
            "mobilTelefon": "string",
            "nachname": "string",
            "partnerId": "string",
            "produktAnbieterId": "string",
            "telefonnummer": "string",
            "vertriebsOrganisation": {
              "firma": "string",
              "name": "string",
              "vertriebsOrganisationsId": "string"
            },
            "vorname": "string",
            "webseite": "string"
          }
        },
        "bewertungDesAngebots": "ANGEBOT_ENTSPRICHT_DER_EMPFEHLUNG_DES_KUNDENBETREUERS",
        "darlehen": [
          {
            "auszahlungsBetrag": 0,
            "auszahlungsDatum": "2020-02-24",
            "auszahlungsKurs": 0,
            "bereitstellung": {
              "bereitstellungsZins": 0,
              "bereitstellungsZinsFreieZeitInMonaten": 0
            },
            "darlehensBetrag": 0,
            "darlehensTyp": "ANNUITAETEN_DARLEHEN",
            "detailsZurVerwendung": "string",
            "effektivZins": 0,
            "effektivZinsRelevanteKosten": {
              "beratungsHonorar": 0,
              "grundbuchKosten": 0,
              "sonstigeKosten": 0,
              "tilgungsErsatzProduktKosten": 0,
              "wohnGebaeudeVersicherungsKosten": 0,
              "zinsabsicherungsKosten": 0,
              "zusatzSicherheitsKosten": 0
            },
            "forwardPeriodeInMonaten": 0,
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "konditionWurdeManuellAngepasst": true,
            "konditionsAnpassungsBegruendung": "string",
            "laufZeitInJahren": 0,
            "laufzeitInMonaten": 0,
            "maximaleLaufzeitInMonaten": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "rateMonatlich": 123.34,
            "rateMonatlichInDerTilgungsfreienAnlaufzeit": 0,
            "sollZins": 2.05,
            "tilgung": {
              "anfaenglicheTilgung": 0,
              "sonderTilgungJaehrlich": 0,
              "tilgungsBeginnAm": "2020-02-24",
              "tilgungsErsatz": {
                "id": "string",
                "typ": "string"
              }
            },
            "tilgungsFreieAnlaufJahre": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL",
            "zinsBindung": {
              "endetAm": "2020-02-24",
              "jahre": 0,
              "monate": 0,
              "restschuldNachZinsBindungsEnde": 0
            },
            "zinsZahlungsBeginnAm": "2020-02-24"
          }
        ],
        "erzeugtAm": "2020-02-24T11:55:47Z",
        "kennung": "string",
        "machbarkeitsStatus": "MACHBAR",
        "meldungen": [
          {
            "kategorie": "AUSZAHLUNGS_VORAUSSETZUNG",
            "kreditEntscheider": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "text": "string"
          }
        ],
        "pruefungsErgebnisse": [
          {
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "weitereAngaben": "string"
          }
        ],
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "ansprechpartner": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "antragsNummer": "string",
      "beratung": {
        "art": "PRAESENZ_GESCHAEFT",
        "hinweisFuerProduktAnbieter": "string",
        "istKundenBetreuerVerkaeuferOderMaklerDerImmobilie": false
      },
      "datenKontext": "TEST_MODUS",
      "dokumente": [
        {
          "art": "string",
          "href": "string",
          "name": "string",
          "titel": "string",
          "type": "string"
        }
      ],
      "kreditSachbearbeiter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "status": {
        "ablehnungsgrund": "FINANZIELLE_SITUATION",
        "antragsteller": "BEANTRAGT",
        "bearbeitungsFortschritt": "NICHT_VON_PRODUKTANBIETER_BESTAETIGT",
        "produktAnbieter": "NICHT_BEARBEITET"
      },
      "vermittler": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string",
        "_links": {
          "self": {
            "href": "string",
            "type": "string"
          }
        }
      },
      "zeitpunktDerAnnahme": "2020-02-24T11:55:47Z",
      "zugrundeliegendeDaten": {
        "bankverbindung": {
          "bic": "string",
          "iban": "string",
          "id": "string",
          "kontoinhaberIds": [
            "string"
          ],
          "kontoinhaberName": "string",
          "kreditinstitut": "string"
        },
        "finanzierungsObjekt": {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "verwendenAls": "ABLOESEN",
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "keinBaulandFlaecheInQm": 0,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        },
        "haushalte": [
          {
            "antragsteller": [
              {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "arbeitserlaubnis": false,
                "arbeitserlaubnisBefristetBis": "2020-02-24",
                "aufenthaltsTitel": "VISUM",
                "aufenthaltsTitelBefristetBis": "2020-02-24",
                "beschaeftigung": {
                  "anzahlGehaelterProJahr": 0,
                  "arbeitgeber": "string",
                  "arbeitgeberInDeutschlandAnsaessig": false,
                  "arbeitgeberLand": {
                    "isoCountryCode": "string",
                    "name": "string"
                  },
                  "art": "ANGESTELLTER",
                  "befristungsStatus": "BEFRISTET",
                  "beruf": "string",
                  "beschaeftigtSeit": "2020-02-24",
                  "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
                  "einkommenNettoJaehrlich": 0,
                  "einkommenNettoMonatlich": 0,
                  "firma": "string",
                  "inProbezeit": false,
                  "situationNachRenteneintritt": {
                    "gesetzlicheRenteMonatlich": 0,
                    "privateRenteMonatlich": 0,
                    "rentenBeginn": "2020-02-24",
                    "sonstigesEinkommenMonatlich": 0
                  },
                  "taetigkeit": "ALTENPFLEGER"
                },
                "bruttoVorjahresEinkommen": 0,
                "email": "max.mustermann@test.de",
                "externeAntragstellerId": "string",
                "familienstand": "GESCHIEDEN",
                "geburtsdatum": "2020-02-24",
                "geburtsort": "string",
                "guetertrennungVereinbartWennVerheiratet": false,
                "id": "string",
                "inDeutschlandSeit": "2020-02-24",
                "legitimationsDaten": {
                  "ausstellendeBehoerde": "string",
                  "ausstellungsdatum": "2020-02-24",
                  "ausweisArt": "PERSONALAUSWEIS",
                  "ausweisArtBeiAndererAusweis": "string",
                  "ausweisNummer": "string"
                },
                "nachname": "string",
                "schufaErgebnis": {
                  "antragstellerUnbekannt": false,
                  "inManuellerNachbehandlung": false,
                  "score": "string"
                },
                "staatsangehoerigkeit": {
                  "isoCountryCode": "string",
                  "name": "string"
                },
                "steuerId": "string",
                "telefonnummer": "string",
                "telefonnummerVorwahl": "string",
                "titel": [
                  "DOKTOR"
                ],
                "titelDoktor": true,
                "titelProfessor": true,
                "vorAnschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "vorname": "string",
                "weitereKontaktMoeglichkeiten": "string",
                "wohnhaftSeit": "2020-02-24"
              }
            ],
            "anzahlErwachseneImHaushalt": 0,
            "anzahlKinderNichtImHaushalt": 0,
            "bestehendeImmobilien": [
              {
                "adresse": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "autostellplaetze": [
                  {
                    "mieteinnahmenMonatlich": 0,
                    "typ": "STELLPLATZ"
                  }
                ],
                "bestehendeDarlehen": [
                  {
                    "abzuloesendeRestschuld": 0,
                    "aktuelleRestschuldWennNichtAbzuloesen": 0,
                    "darlehensArt": "BAUSPARDARLEHEN",
                    "darlehensBetrag": 0,
                    "darlehensGeber": {},
                    "darlehensKontonummer": "string",
                    "eingetrageneGrundschuld": 0,
                    "grundschuldArt": "BRIEF_GRUNDSCHULD",
                    "id": "string",
                    "laufzeitEnde": "2020-02-24",
                    "rateMonatlich": 0,
                    "sollZins": 0,
                    "sondertilgungZumZinsBindungsEnde": 0,
                    "zinsBindungEndetAm": "2020-02-24"
                  }
                ],
                "bewirtschaftungsKostenJaehrlich": 0,
                "bodenRichtwert": 0,
                "bundesland": "BADEN_WUERTTEMBERG",
                "effektivZinsErhoehendeKosten": {
                  "anpassen": true,
                  "grundbuchEintragungsKostenEinmalig": 0,
                  "sonstigeKostenBezeichnung": "string",
                  "sonstigeKostenEinmalig": 0,
                  "wohnGebaeudeVersicherungsKostenJaehrlich": 0
                },
                "erbbaurecht": {
                  "erbbaurecht": true,
                  "erbbauzinsJaehrlich": 0,
                  "grundstuecksEigentuemer": "ANDERE",
                  "laufzeitBisJahr": "string"
                },
                "gebaeude": {
                  "anzahlDerGewerbeeinheiten": 0,
                  "anzahlDerWohneinheitenImGebaeude": 0,
                  "anzahlVollgeschosse": 0,
                  "aufbauFinanzierung": true,
                  "aufzugVorhanden": true,
                  "ausstattung": "EINFACH",
                  "baujahr": "2016",
                  "bauweise": "FACHWERK_MIT_STROH_LEHM",
                  "bezeichnungWohneinheit": "string",
                  "dachgeschossAusbau": "FLACHDACH",
                  "einliegerwohnungVorhanden": true,
                  "geschossLage": "UNTERGESCHOSS",
                  "gewerbeflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "hausAnordnung": "FREISTEHEND",
                  "hausTyp": "DOPPELHAUSHAELFTE",
                  "istFertighaus": true,
                  "kellerausbau": "AUSGEBAUT",
                  "kubatur": 0,
                  "miteigentumsAnteil": {
                    "anteil": 0,
                    "gesamt": 0
                  },
                  "modernisierungsAngaben": {
                    "badWc": true,
                    "bodenWandTreppe": true,
                    "dach": true,
                    "fenster": true,
                    "heizungZentral": true,
                    "modernisierungsGrad": "GERING",
                    "modernisierungsJahr": "string",
                    "raumaufteilung": true,
                    "stromAbwasserHeizkoerper": true,
                    "waermedaemmung": true,
                    "wurdeModernisiert": true
                  },
                  "unterkellerung": "NICHT_UNTERKELLERT",
                  "wohnflaeche": {
                    "gesamtGroesse": 0,
                    "vermietungsInformationen": {}
                  },
                  "zustand": "SEHR_GUT"
                },
                "grundbuchAngabe": {
                  "anmerkungen": "string",
                  "bandUndBlatt": "string",
                  "flurstuecke": [
                    {}
                  ],
                  "ort": "string",
                  "rechteInAbteilung2": {
                    "beschreibung": "string",
                    "betrag": 0,
                    "vorhanden": true
                  }
                },
                "grundstueck": {
                  "groesse": 0,
                  "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
                },
                "id": "string",
                "immobilienEinsatz": "KEIN_EINSATZ",
                "keinBaulandFlaecheInQm": 0,
                "keineBestehendenDarlehenVorhanden": true,
                "marktueblicherKaufpreisProQm": 0,
                "marktwert": 0,
                "maximalEinzusetzenderBetragWennVerkauf": 0,
                "objektArt": "GRUNDSTUECK",
                "vergleichsmieteFuerGewerbeflaecheProQm": 0,
                "vergleichsmieteFuerWohnflaecheProQm": 0,
                "verkehrswert": 0,
                "vorlaeufigerVerkehrswert": 0,
                "wohnlage": "GEHOBEN"
              }
            ],
            "id": "string",
            "kfzAnzahl": 0,
            "kinder": [
              {
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kindergeldWirdBezogen": true,
                "name": "string",
                "unterhaltsEinnahmenBetragMonatlich": 0
              }
            ],
            "lebenshaltungsKostenMonatlich": 0,
            "obligo": {
              "vermoegenOderVerbindlichkeiten": [
                {
                  "aktuellerWert": 0,
                  "anrechnungFuerBlankoAnteil": 0,
                  "bezeichner": "string",
                  "kontonummer": "string",
                  "vermoegensTyp": "VERMOEGEN"
                }
              ]
            },
            "positionen": {
              "bankUndSparguthaben": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zinsertragJaehrlich": 0,
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "bausparvertraege": [
                {
                  "abschlussGebuehr": 0,
                  "aktuellerWert": 0,
                  "bausparSumme": 0,
                  "einmalzahlung": 0,
                  "ertrag": 0,
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "produktAnbieter": {
                    "anrede": "FRAU",
                    "anschrift": {},
                    "email": "string",
                    "externePartnerId": "string",
                    "externerKreditSachbearbeiterId": "string",
                    "fax": "string",
                    "firmenNameZusatz": "string",
                    "firmierung": "string",
                    "geburtsdatum": "2020-02-24",
                    "id": "string",
                    "kreditsachbearbeiter": true,
                    "mobilTelefon": "string",
                    "nachname": "string",
                    "partnerId": "string",
                    "produktAnbieterId": "string",
                    "telefonnummer": "string",
                    "vertriebsOrganisation": {},
                    "vorname": "string",
                    "webseite": "string"
                  },
                  "sonderZahlungen": [
                    {}
                  ],
                  "sparBeitragMonatlich": 0,
                  "tarif": "string",
                  "typ": "string",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "vertragsBeginn": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0,
                  "zuteilungsDatum": "2020-02-24"
                }
              ],
              "ehegattenUnterhalt": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "einkuenfteAusNebentaetigkeit": [
                {
                  "beginnDerNebentaetigkeit": "2020-02-24",
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "kindergeld": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "lebensUndRentenVersicherungen": [
                {
                  "id": "string",
                  "maximalAufzuloesenderBetrag": 0,
                  "praemieMonatlich": 0,
                  "rueckkaufsWertAktuell": 0,
                  "tarif": "string",
                  "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "versicherungsGesellschaft": "string",
                  "versicherungsSumme": 0,
                  "vertragsBeginn": "2020-02-24",
                  "vertragsEnde": "2020-02-24",
                  "vertragsNummer": "string",
                  "verwaltungsgebuehrenJaehrlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "mietAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "entfallenMitFinanzierung": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateDarlehen": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "privateKrankenversicherung": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "ratenkredite": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeEinnahmen": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVerbindlichkeiten": [
                {
                  "glaeubiger": "string",
                  "laufzeitEnde": "2020-02-24",
                  "rateMonatlich": 0,
                  "restschuld": 0,
                  "vermoegensTyp": "VERMOEGEN",
                  "wirdAbgeloest": true,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "sonstigeVermoegen": [
                {
                  "aktuellerWert": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "sparplaene": [
                {
                  "aktuellerWert": 0,
                  "beitragMonatlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ],
              "unbefristeteZusatzRenten": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "unterhaltsVerpflichtungen": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "variableEinkuenfte": [
                {
                  "einnahmenMonatlich": 0,
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "versicherungsAusgaben": [
                {
                  "ausgabenMonatlich": 0,
                  "berechnungsHilfeVermoegen": {
                    "betragNachFinanzierung": 0,
                    "betragVorFinanzierung": 0
                  },
                  "zahlungsTyp": "EINNAHME"
                }
              ],
              "wertpapiere": [
                {
                  "aktuellerWert": 0,
                  "dividendenJaehrlich": 0,
                  "ertrag": 0,
                  "maximalAufzuloesenderWert": 0,
                  "vermoegensEinsatz": "KEIN_EINSATZ",
                  "vermoegensTyp": "VERMOEGEN",
                  "zahlungsTyp": "EINNAHME",
                  "zukuenftigeEinnahmen": 0
                }
              ]
            }
          }
        ],
        "vorhaben": {
          "absicherungswunsch": {
            "id": "string",
            "versicherungsWuensche": [
              {
                "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
                "id": "string",
                "praemienZahlungsweise": "EINMALIG",
                "risikoAbsicherungsWuensche": [
                  {
                    "abzusicherndesRisiko": "TODESFALL",
                    "versicherteRate": 0,
                    "versicherungsSumme": 0
                  }
                ],
                "versichertePersonId": "string",
                "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
                "versicherungsBeginn": "2020-02-24",
                "versicherungsDauerInMonaten": 0
              }
            ]
          },
          "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
          "externeBausparAngebote": [
            {
              "abschlussGebuehr": 0,
              "angebotsHinweisFuerAntragsteller": "string",
              "bausparSumme": 0,
              "einmalzahlung": 0,
              "id": "string",
              "produktAnbieter": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparPhase": {
                "guthabenBeiZuteilung": 0,
                "sparBeitragMonatlich": 0,
                "sparPhaseInJahren": 0
              },
              "tarif": "string",
              "tilgungsPhase": {
                "bausparDarlehenSumme": 0,
                "sollZinsNachZuteilung": 0,
                "tilgungsBeitragMonatlich": 0,
                "tilgungsPhaseInJahren": 0
              },
              "typ": "string",
              "vertragsBeginn": "2020-02-24",
              "vertragsNummer": "string",
              "verwaltungsgebuehrenJaehrlich": 0,
              "zuteilungsDatum": "2020-02-24"
            }
          ],
          "finanzbedarf": {
            "anzahlTeilzahlungen": 0,
            "aussenAnlagen": 0,
            "bauNebenkosten": 0,
            "beratungsHonorar": 0,
            "bereitsBeglichen": 0,
            "erschliessung": 0,
            "grunderwerbsteuer": 0,
            "grundstueckBereitsBezahlt": true,
            "grundstuecksKaufpreis": 0,
            "herstellung": 0,
            "kapitalBeschaffung": 0,
            "kapitalWirdBeschafft": true,
            "kaufpreis": 0,
            "maklergebuehr": 0,
            "mobiliar": 0,
            "modernisieren": true,
            "modernisierung": 0,
            "notargebuehr": 0,
            "renovierung": 0,
            "sonstigeKosten": 0,
            "zusaetzlichesKapital": 0
          },
          "finanzierungswunsch": {
            "bausparWuensche": [
              {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              }
            ],
            "darlehensWuensche": [
              {
                "annuitaetenDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "forwardDarlehen": {
                  "auszahlungsDatum": "2020-02-24",
                  "bereitstellungsZinsFreieZeitInMonaten": 0,
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "sondertilgungOptionalJaehrlich": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "zinsBindungInJahren": 0
                },
                "id": "string",
                "kfwDarlehen": {
                  "darlehensBetrag": 0,
                  "kfwEndfaellig": "NEIN",
                  "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
                  "kfwProgramm": "PROGRAMM_124",
                  "laufzeitInJahren": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  },
                  "tilgungsfreieAnlaufjahre": 0,
                  "zinsBindungInJahren": 0
                },
                "privatDarlehen": {
                  "darlehensBetrag": 0,
                  "laufzeitInMonaten": 0,
                  "provision": 0
                },
                "variablesDarlehen": {
                  "darlehensBetrag": 0,
                  "provision": 0,
                  "tilgungsWunsch": {
                    "anfaenglicheTilgung": 0,
                    "ausgesetztBerechnet": false,
                    "ausgesetztEigenesAngebot": false,
                    "bausparWunsch": {},
                    "rate": 0,
                    "tilgungsBeginn": "2020-02-24",
                    "tilgungsErsatzProduktId": "string",
                    "volltilgerWennAnnuitaetenOderForward": false
                  }
                },
                "zwischenFinanzierung": {
                  "darlehensBetrag": 0,
                  "detailsZurVerwendung": "string",
                  "maximaleLaufzeitInMonaten": 0,
                  "provision": 0,
                  "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
                }
              }
            ],
            "id": "string"
          },
          "id": "string",
          "nachfinanzierung": true,
          "nachrangigeExterneDarlehen": [
            {
              "darlehensBetrag": 0,
              "darlehensGeber": "string",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "typ": "ARBEITGEBERDARLEHEN",
              "zinsBindung": {
                "endetAm": "2020-02-24",
                "jahre": 0,
                "monate": 0,
                "restschuldNachZinsBindungsEnde": 0
              }
            }
          ],
          "praeferenzen": {
            "bereitstellungsZinsFreieZeit": {
              "darlehenBenoetigtInMonaten": 0,
              "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
              "zusatzlicheKommentare": "string"
            },
            "bestandteileDerFinanzierung": {
              "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
              "zusatzlicheKommentare": "string"
            },
            "hoeheDerRate": {
              "betrag": 0,
              "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
              "zusatzlicheKommentare": "string"
            },
            "laufzeit": {
              "bisZumJahr": "2016",
              "bisZurRenteImJahr": "2016",
              "inJahren": 0,
              "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
              "zusatzlicheKommentare": "string"
            },
            "sondertilgung": {
              "betragEinmalig": 0,
              "betragJaehrlich": 0,
              "praeferenzAuswahl": "JAEHRLICH",
              "zusatzlicheKommentare": "string"
            },
            "tilgungsSatzWechsel": {
              "mindestensBenoetigt": 0,
              "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
              "zusatzlicheKommentare": "string"
            },
            "weiterePraeferenz": "string",
            "zeitlicherRahmen": {
              "finanzierungszusageBis": "2020-02-24",
              "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
              "zusatzlicheKommentare": "string"
            },
            "zinsBindung": {
              "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
              "zinsBindungBisJahren": 0,
              "zinsBindungVonJahren": 0,
              "zinsBindungZwischenJahren": 0,
              "zusatzlicheKommentare": "string"
            }
          },
          "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
        }
      },
      "_links": {
        "self": {
          "href": "string",
          "type": "string"
        }
      }
    }
  ],
  "archivierung": {
    "grund": "VORGANG_ERFOLGREICH_ABGESCHLOSSEN",
    "kommentar": "string"
  },
  "aufbewahrungBis": "2020-02-24",
  "bankverbindung": {
    "bic": "string",
    "iban": "string",
    "id": "string",
    "kontoinhaberIds": [
      "string"
    ],
    "kontoinhaberName": "string",
    "kreditinstitut": "string"
  },
  "datenKontext": "TEST_MODUS",
  "erstelltAm": "2020-02-24",
  "externeVorgangsNummer": "string",
  "finanzierungsObjekt": {
    "adresse": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "autostellplaetze": [
      {
        "mieteinnahmenMonatlich": 0,
        "typ": "STELLPLATZ"
      }
    ],
    "bestehendeDarlehen": [
      {
        "abzuloesendeRestschuld": 0,
        "aktuelleRestschuldWennNichtAbzuloesen": 0,
        "darlehensArt": "BAUSPARDARLEHEN",
        "darlehensBetrag": 0,
        "darlehensGeber": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "darlehensKontonummer": "string",
        "eingetrageneGrundschuld": 0,
        "grundschuldArt": "BRIEF_GRUNDSCHULD",
        "id": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "sollZins": 0,
        "sondertilgungZumZinsBindungsEnde": 0,
        "verwendenAls": "ABLOESEN",
        "zinsBindungEndetAm": "2020-02-24"
      }
    ],
    "bewirtschaftungsKostenJaehrlich": 0,
    "bodenRichtwert": 0,
    "bundesland": "BADEN_WUERTTEMBERG",
    "effektivZinsErhoehendeKosten": {
      "anpassen": true,
      "grundbuchEintragungsKostenEinmalig": 0,
      "sonstigeKostenBezeichnung": "string",
      "sonstigeKostenEinmalig": 0,
      "wohnGebaeudeVersicherungsKostenJaehrlich": 0
    },
    "erbbaurecht": {
      "erbbaurecht": true,
      "erbbauzinsJaehrlich": 0,
      "grundstuecksEigentuemer": "ANDERE",
      "laufzeitBisJahr": "string"
    },
    "gebaeude": {
      "anzahlDerGewerbeeinheiten": 0,
      "anzahlDerWohneinheitenImGebaeude": 0,
      "anzahlVollgeschosse": 0,
      "aufbauFinanzierung": true,
      "aufzugVorhanden": true,
      "ausstattung": "EINFACH",
      "baujahr": "2016",
      "bauweise": "FACHWERK_MIT_STROH_LEHM",
      "bezeichnungWohneinheit": "string",
      "dachgeschossAusbau": "FLACHDACH",
      "einliegerwohnungVorhanden": true,
      "geschossLage": "UNTERGESCHOSS",
      "gewerbeflaeche": {
        "gesamtGroesse": 0,
        "vermietungsInformationen": {
          "mieteinnahmenNettoKaltMonatlich": 0,
          "nutzungsArt": "EIGENGENUTZT",
          "vermieteteFlaeche": 0
        }
      },
      "hausAnordnung": "FREISTEHEND",
      "hausTyp": "DOPPELHAUSHAELFTE",
      "istFertighaus": true,
      "kellerausbau": "AUSGEBAUT",
      "kubatur": 0,
      "miteigentumsAnteil": {
        "anteil": 0,
        "gesamt": 0
      },
      "modernisierungsAngaben": {
        "badWc": true,
        "bodenWandTreppe": true,
        "dach": true,
        "fenster": true,
        "heizungZentral": true,
        "modernisierungsGrad": "GERING",
        "modernisierungsJahr": "string",
        "raumaufteilung": true,
        "stromAbwasserHeizkoerper": true,
        "waermedaemmung": true,
        "wurdeModernisiert": true
      },
      "unterkellerung": "NICHT_UNTERKELLERT",
      "wohnflaeche": {
        "gesamtGroesse": 0,
        "vermietungsInformationen": {
          "mieteinnahmenNettoKaltMonatlich": 0,
          "nutzungsArt": "EIGENGENUTZT",
          "vermieteteFlaeche": 0
        }
      },
      "zustand": "SEHR_GUT"
    },
    "grundbuchAngabe": {
      "anmerkungen": "string",
      "bandUndBlatt": "string",
      "flurstuecke": [
        {
          "anteil": {
            "anteil": 0,
            "gesamt": 0
          },
          "flur": "string",
          "flurstuecksNummer": "string",
          "groesse": 0
        }
      ],
      "ort": "string",
      "rechteInAbteilung2": {
        "beschreibung": "string",
        "betrag": 0,
        "vorhanden": true
      }
    },
    "grundstueck": {
      "groesse": 0,
      "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
    },
    "id": "string",
    "keinBaulandFlaecheInQm": 0,
    "marktueblicherKaufpreisProQm": 0,
    "marktwert": 0,
    "objektArt": "GRUNDSTUECK",
    "vergleichsmieteFuerGewerbeflaecheProQm": 0,
    "vergleichsmieteFuerWohnflaecheProQm": 0,
    "verkehrswert": 0,
    "vorlaeufigerVerkehrswert": 0,
    "wohnlage": "GEHOBEN"
  },
  "geschlossenAm": "2020-02-24",
  "haushalte": [
    {
      "antragsteller": [
        {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "arbeitserlaubnis": false,
          "arbeitserlaubnisBefristetBis": "2020-02-24",
          "aufenthaltsTitel": "VISUM",
          "aufenthaltsTitelBefristetBis": "2020-02-24",
          "beschaeftigung": {
            "anzahlGehaelterProJahr": 0,
            "arbeitgeber": "string",
            "arbeitgeberInDeutschlandAnsaessig": false,
            "arbeitgeberLand": {
              "isoCountryCode": "string",
              "name": "string"
            },
            "art": "ANGESTELLTER",
            "befristungsStatus": "BEFRISTET",
            "beruf": "string",
            "beschaeftigtSeit": "2020-02-24",
            "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
            "einkommenNettoJaehrlich": 0,
            "einkommenNettoMonatlich": 0,
            "firma": "string",
            "inProbezeit": false,
            "situationNachRenteneintritt": {
              "gesetzlicheRenteMonatlich": 0,
              "privateRenteMonatlich": 0,
              "rentenBeginn": "2020-02-24",
              "sonstigesEinkommenMonatlich": 0
            },
            "taetigkeit": "ALTENPFLEGER"
          },
          "bruttoVorjahresEinkommen": 0,
          "email": "max.mustermann@test.de",
          "externeAntragstellerId": "string",
          "familienstand": "GESCHIEDEN",
          "geburtsdatum": "2020-02-24",
          "geburtsort": "string",
          "guetertrennungVereinbartWennVerheiratet": false,
          "id": "string",
          "inDeutschlandSeit": "2020-02-24",
          "legitimationsDaten": {
            "ausstellendeBehoerde": "string",
            "ausstellungsdatum": "2020-02-24",
            "ausweisArt": "PERSONALAUSWEIS",
            "ausweisArtBeiAndererAusweis": "string",
            "ausweisNummer": "string"
          },
          "nachname": "string",
          "schufaErgebnis": {
            "antragstellerUnbekannt": false,
            "inManuellerNachbehandlung": false,
            "score": "string"
          },
          "staatsangehoerigkeit": {
            "isoCountryCode": "string",
            "name": "string"
          },
          "steuerId": "string",
          "telefonnummer": "string",
          "telefonnummerVorwahl": "string",
          "titel": [
            "DOKTOR"
          ],
          "titelDoktor": true,
          "titelProfessor": true,
          "vorAnschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "vorname": "string",
          "weitereKontaktMoeglichkeiten": "string",
          "wohnhaftSeit": "2020-02-24"
        }
      ],
      "anzahlErwachseneImHaushalt": 0,
      "anzahlKinderNichtImHaushalt": 0,
      "bestehendeImmobilien": [
        {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "immobilienEinsatz": "KEIN_EINSATZ",
          "keinBaulandFlaecheInQm": 0,
          "keineBestehendenDarlehenVorhanden": true,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "maximalEinzusetzenderBetragWennVerkauf": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        }
      ],
      "id": "string",
      "kfzAnzahl": 0,
      "kinder": [
        {
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kindergeldWirdBezogen": true,
          "name": "string",
          "unterhaltsEinnahmenBetragMonatlich": 0
        }
      ],
      "lebenshaltungsKostenMonatlich": 0,
      "obligo": {
        "vermoegenOderVerbindlichkeiten": [
          {
            "aktuellerWert": 0,
            "anrechnungFuerBlankoAnteil": 0,
            "bezeichner": "string",
            "kontonummer": "string",
            "vermoegensTyp": "VERMOEGEN"
          }
        ]
      },
      "positionen": {
        "bankUndSparguthaben": [
          {
            "aktuellerWert": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zinsertragJaehrlich": 0,
            "zukuenftigeEinnahmen": 0
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "aktuellerWert": 0,
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "ertrag": 0,
            "id": "string",
            "maximalAufzuloesenderBetrag": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeitragMonatlich": 0,
            "tarif": "string",
            "typ": "string",
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "ehegattenUnterhalt": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "einkuenfteAusNebentaetigkeit": [
          {
            "beginnDerNebentaetigkeit": "2020-02-24",
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "kindergeld": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "lebensUndRentenVersicherungen": [
          {
            "id": "string",
            "maximalAufzuloesenderBetrag": 0,
            "praemieMonatlich": 0,
            "rueckkaufsWertAktuell": 0,
            "tarif": "string",
            "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "versicherungsGesellschaft": "string",
            "versicherungsSumme": 0,
            "vertragsBeginn": "2020-02-24",
            "vertragsEnde": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "mietAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "entfallenMitFinanzierung": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "privateDarlehen": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "privateKrankenversicherung": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "ratenkredite": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeEinnahmen": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeVerbindlichkeiten": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeVermoegen": [
          {
            "aktuellerWert": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zukuenftigeEinnahmen": 0
          }
        ],
        "sparplaene": [
          {
            "aktuellerWert": 0,
            "beitragMonatlich": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0
          }
        ],
        "unbefristeteZusatzRenten": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "unterhaltsVerpflichtungen": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "variableEinkuenfte": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "versicherungsAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "wertpapiere": [
          {
            "aktuellerWert": 0,
            "dividendenJaehrlich": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0
          }
        ]
      }
    }
  ],
  "importQuelle": "string",
  "kundenBetreuer": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "leadTracking": {
    "kampagne": "string",
    "keyword": "string",
    "kundenBetreuerBenachrichtigen": true,
    "trackingId": "string"
  },
  "letztesEreignis": "2020-02-24T11:55:47Z",
  "phase": "string",
  "prioritaet": "NIEDRIG",
  "status": "string",
  "tippGeber": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "vorgangsBearbeiter": {
    "anrede": "FRAU",
    "anschrift": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "email": "string",
    "externePartnerId": "string",
    "externerKreditSachbearbeiterId": "string",
    "fax": "string",
    "firmenNameZusatz": "string",
    "firmierung": "string",
    "geburtsdatum": "2020-02-24",
    "id": "string",
    "kreditsachbearbeiter": true,
    "mobilTelefon": "string",
    "nachname": "string",
    "partnerId": "string",
    "telefonnummer": "string",
    "vertriebsOrganisation": {
      "firma": "string",
      "name": "string",
      "vertriebsOrganisationsId": "string"
    },
    "vorname": "string",
    "webseite": "string",
    "_links": {
      "self": {
        "href": "string",
        "type": "string"
      }
    }
  },
  "vorgangsNummer": "string",
  "vorhaben": {
    "absicherungswunsch": {
      "id": "string",
      "versicherungsWuensche": [
        {
          "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
          "id": "string",
          "praemienZahlungsweise": "EINMALIG",
          "risikoAbsicherungsWuensche": [
            {
              "abzusicherndesRisiko": "TODESFALL",
              "versicherteRate": 0,
              "versicherungsSumme": 0
            }
          ],
          "versichertePersonId": "string",
          "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
          "versicherungsBeginn": "2020-02-24",
          "versicherungsDauerInMonaten": 0
        }
      ]
    },
    "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
    "externeBausparAngebote": [
      {
        "abschlussGebuehr": 0,
        "angebotsHinweisFuerAntragsteller": "string",
        "bausparSumme": 0,
        "einmalzahlung": 0,
        "id": "string",
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparPhase": {
          "guthabenBeiZuteilung": 0,
          "sparBeitragMonatlich": 0,
          "sparPhaseInJahren": 0
        },
        "tarif": "string",
        "tilgungsPhase": {
          "bausparDarlehenSumme": 0,
          "sollZinsNachZuteilung": 0,
          "tilgungsBeitragMonatlich": 0,
          "tilgungsPhaseInJahren": 0
        },
        "typ": "string",
        "vertragsBeginn": "2020-02-24",
        "vertragsNummer": "string",
        "verwaltungsgebuehrenJaehrlich": 0,
        "zuteilungsDatum": "2020-02-24"
      }
    ],
    "finanzbedarf": {
      "anzahlTeilzahlungen": 0,
      "aussenAnlagen": 0,
      "bauNebenkosten": 0,
      "beratungsHonorar": 0,
      "bereitsBeglichen": 0,
      "erschliessung": 0,
      "grunderwerbsteuer": 0,
      "grundstueckBereitsBezahlt": true,
      "grundstuecksKaufpreis": 0,
      "herstellung": 0,
      "kapitalBeschaffung": 0,
      "kapitalWirdBeschafft": true,
      "kaufpreis": 0,
      "maklergebuehr": 0,
      "mobiliar": 0,
      "modernisieren": true,
      "modernisierung": 0,
      "notargebuehr": 0,
      "renovierung": 0,
      "sonstigeKosten": 0,
      "zusaetzlichesKapital": 0
    },
    "finanzierungswunsch": {
      "bausparWuensche": [
        {
          "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
          "bausparSummeAbsolut": 0,
          "bausparSummeRelativ": 0,
          "bausparTarif": [
            {
              "id": "string",
              "kurzName": "string",
              "langName": "string",
              "produktAnbieter": "string",
              "riesterFoerderung": true,
              "status": "AKTIV"
            }
          ],
          "bausparTarife": [
            "string"
          ],
          "id": "string",
          "sonderZahlungEinmalig": 0,
          "sonderZahlungen": [
            {
              "anzahl": 0,
              "betrag": 0,
              "termin": "2020-02-24",
              "zahlweise": "EINMALIG"
            }
          ],
          "sparBeginn": "2020-02-24",
          "sparBeitragMonatlichAbsolut": 0,
          "sparBeitragMonatlichRelativ": 0,
          "tilgungsBeitragMonatlich": 0,
          "vertragsPartnerIds": [
            "string"
          ],
          "verwendung": "ZINS_ABSICHERUNG",
          "zuteilungsDatum": "2020-02-24"
        }
      ],
      "darlehensWuensche": [
        {
          "annuitaetenDarlehen": {
            "auszahlungsDatum": "2020-02-24",
            "bereitstellungsZinsFreieZeitInMonaten": 0,
            "darlehensBetrag": 0,
            "provision": 0,
            "sondertilgungOptionalJaehrlich": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "zinsBindungInJahren": 0
          },
          "forwardDarlehen": {
            "auszahlungsDatum": "2020-02-24",
            "bereitstellungsZinsFreieZeitInMonaten": 0,
            "darlehensBetrag": 0,
            "provision": 0,
            "sondertilgungOptionalJaehrlich": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "zinsBindungInJahren": 0
          },
          "id": "string",
          "kfwDarlehen": {
            "darlehensBetrag": 0,
            "kfwEndfaellig": "NEIN",
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "laufzeitInJahren": 0,
            "provision": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "tilgungsfreieAnlaufjahre": 0,
            "zinsBindungInJahren": 0
          },
          "privatDarlehen": {
            "darlehensBetrag": 0,
            "laufzeitInMonaten": 0,
            "provision": 0
          },
          "variablesDarlehen": {
            "darlehensBetrag": 0,
            "provision": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            }
          },
          "zwischenFinanzierung": {
            "darlehensBetrag": 0,
            "detailsZurVerwendung": "string",
            "maximaleLaufzeitInMonaten": 0,
            "provision": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
          }
        }
      ],
      "id": "string"
    },
    "id": "string",
    "nachfinanzierung": true,
    "nachrangigeExterneDarlehen": [
      {
        "darlehensBetrag": 0,
        "darlehensGeber": "string",
        "id": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "typ": "ARBEITGEBERDARLEHEN",
        "zinsBindung": {
          "endetAm": "2020-02-24",
          "jahre": 0,
          "monate": 0,
          "restschuldNachZinsBindungsEnde": 0
        }
      }
    ],
    "praeferenzen": {
      "bereitstellungsZinsFreieZeit": {
        "darlehenBenoetigtInMonaten": 0,
        "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
        "zusatzlicheKommentare": "string"
      },
      "bestandteileDerFinanzierung": {
        "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
        "zusatzlicheKommentare": "string"
      },
      "hoeheDerRate": {
        "betrag": 0,
        "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
        "zusatzlicheKommentare": "string"
      },
      "laufzeit": {
        "bisZumJahr": "2016",
        "bisZurRenteImJahr": "2016",
        "inJahren": 0,
        "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
        "zusatzlicheKommentare": "string"
      },
      "sondertilgung": {
        "betragEinmalig": 0,
        "betragJaehrlich": 0,
        "praeferenzAuswahl": "JAEHRLICH",
        "zusatzlicheKommentare": "string"
      },
      "tilgungsSatzWechsel": {
        "mindestensBenoetigt": 0,
        "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
        "zusatzlicheKommentare": "string"
      },
      "weiterePraeferenz": "string",
      "zeitlicherRahmen": {
        "finanzierungszusageBis": "2020-02-24",
        "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
        "zusatzlicheKommentare": "string"
      },
      "zinsBindung": {
        "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
        "zinsBindungBisJahren": 0,
        "zinsBindungVonJahren": 0,
        "zinsBindungZwischenJahren": 0,
        "zusatzlicheKommentare": "string"
      }
    },
    "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
  },
  "_links": {
    "antraege": {
      "href": "string",
      "type": "string"
    },
    "ereignisse": {
      "href": "string",
      "type": "string"
    },
    "self": {
      "href": "string",
      "type": "string"
    }
  }
}

```

*Vorgang*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|antraege|[[Antrag](#schemaantrag)]|false|none|[Diese Resource repräsentiert einen Antrag in Baufi Smart.]|
|archivierung|[Archivierung](#schemaarchivierung)|false|none|none|
|aufbewahrungBis|string(date)|false|none|Datum, bis wann dieser Vorgang nach DSGVO aufbewahrt werden muss. Nach diesem Datum wird der Vorgang automatisch gelöscht.|
|bankverbindung|[Bankverbindung](#schemabankverbindung)|false|none|none|
|datenKontext|string|false|none|none|
|erstelltAm|string(date)|false|none|none|
|externeVorgangsNummer|string|false|none|none|
|finanzierungsObjekt|[FinanzierungsObjekt](#schemafinanzierungsobjekt)|false|none|none|
|geschlossenAm|string(date)|false|none|none|
|haushalte|[[Haushalt](#schemahaushalt)]|false|none|none|
|importQuelle|string|false|none|none|
|kundenBetreuer|[Partner](#schemapartner)|false|none|none|
|leadTracking|[LeadTracking](#schemaleadtracking)|false|none|none|
|letztesEreignis|string(date-time)|false|none|none|
|phase|string|false|none|none|
|prioritaet|string|false|none|Priorität des Vorgangs, Werte: [NIEDRIG,NEUTRAL,HOCH]|
|status|string|false|none|Status des Vorgangs, Werte: [AKTIV,ARCHIVIERT]|
|tippGeber|[Partner](#schemapartner)|false|none|none|
|vorgangsBearbeiter|[Partner](#schemapartner)|false|none|none|
|vorgangsNummer|string|false|none|none|
|vorhaben|[Vorhaben](#schemavorhaben)|false|none|none|
|_links|[SelfRelAndEreignisse](#schemaselfrelandereignisse)|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|datenKontext|TEST_MODUS|
|datenKontext|ECHT_GESCHAEFT|
|prioritaet|NIEDRIG|
|prioritaet|NEUTRAL|
|prioritaet|HOCH|

<h2 id="tocSvorhaben">Vorhaben</h2>

<a id="schemavorhaben"></a>

```json
{
  "absicherungswunsch": {
    "id": "string",
    "versicherungsWuensche": [
      {
        "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
        "id": "string",
        "praemienZahlungsweise": "EINMALIG",
        "risikoAbsicherungsWuensche": [
          {
            "abzusicherndesRisiko": "TODESFALL",
            "versicherteRate": 0,
            "versicherungsSumme": 0
          }
        ],
        "versichertePersonId": "string",
        "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
        "versicherungsBeginn": "2020-02-24",
        "versicherungsDauerInMonaten": 0
      }
    ]
  },
  "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
  "externeBausparAngebote": [
    {
      "abschlussGebuehr": 0,
      "angebotsHinweisFuerAntragsteller": "string",
      "bausparSumme": 0,
      "einmalzahlung": 0,
      "id": "string",
      "produktAnbieter": {
        "anrede": "FRAU",
        "anschrift": {
          "hausnummer": "string",
          "ort": "string",
          "postleitzahl": "string",
          "strasse": "string"
        },
        "email": "string",
        "externePartnerId": "string",
        "externerKreditSachbearbeiterId": "string",
        "fax": "string",
        "firmenNameZusatz": "string",
        "firmierung": "string",
        "geburtsdatum": "2020-02-24",
        "id": "string",
        "kreditsachbearbeiter": true,
        "mobilTelefon": "string",
        "nachname": "string",
        "partnerId": "string",
        "produktAnbieterId": "string",
        "telefonnummer": "string",
        "vertriebsOrganisation": {
          "firma": "string",
          "name": "string",
          "vertriebsOrganisationsId": "string"
        },
        "vorname": "string",
        "webseite": "string"
      },
      "sonderZahlungen": [
        {
          "anzahl": 0,
          "betrag": 0,
          "termin": "2020-02-24",
          "zahlweise": "EINMALIG"
        }
      ],
      "sparPhase": {
        "guthabenBeiZuteilung": 0,
        "sparBeitragMonatlich": 0,
        "sparPhaseInJahren": 0
      },
      "tarif": "string",
      "tilgungsPhase": {
        "bausparDarlehenSumme": 0,
        "sollZinsNachZuteilung": 0,
        "tilgungsBeitragMonatlich": 0,
        "tilgungsPhaseInJahren": 0
      },
      "typ": "string",
      "vertragsBeginn": "2020-02-24",
      "vertragsNummer": "string",
      "verwaltungsgebuehrenJaehrlich": 0,
      "zuteilungsDatum": "2020-02-24"
    }
  ],
  "finanzbedarf": {
    "anzahlTeilzahlungen": 0,
    "aussenAnlagen": 0,
    "bauNebenkosten": 0,
    "beratungsHonorar": 0,
    "bereitsBeglichen": 0,
    "erschliessung": 0,
    "grunderwerbsteuer": 0,
    "grundstueckBereitsBezahlt": true,
    "grundstuecksKaufpreis": 0,
    "herstellung": 0,
    "kapitalBeschaffung": 0,
    "kapitalWirdBeschafft": true,
    "kaufpreis": 0,
    "maklergebuehr": 0,
    "mobiliar": 0,
    "modernisieren": true,
    "modernisierung": 0,
    "notargebuehr": 0,
    "renovierung": 0,
    "sonstigeKosten": 0,
    "zusaetzlichesKapital": 0
  },
  "finanzierungswunsch": {
    "bausparWuensche": [
      {
        "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
        "bausparSummeAbsolut": 0,
        "bausparSummeRelativ": 0,
        "bausparTarif": [
          {
            "id": "string",
            "kurzName": "string",
            "langName": "string",
            "produktAnbieter": "string",
            "riesterFoerderung": true,
            "status": "AKTIV"
          }
        ],
        "bausparTarife": [
          "string"
        ],
        "id": "string",
        "sonderZahlungEinmalig": 0,
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparBeginn": "2020-02-24",
        "sparBeitragMonatlichAbsolut": 0,
        "sparBeitragMonatlichRelativ": 0,
        "tilgungsBeitragMonatlich": 0,
        "vertragsPartnerIds": [
          "string"
        ],
        "verwendung": "ZINS_ABSICHERUNG",
        "zuteilungsDatum": "2020-02-24"
      }
    ],
    "darlehensWuensche": [
      {
        "annuitaetenDarlehen": {
          "auszahlungsDatum": "2020-02-24",
          "bereitstellungsZinsFreieZeitInMonaten": 0,
          "darlehensBetrag": 0,
          "provision": 0,
          "sondertilgungOptionalJaehrlich": 0,
          "tilgungsWunsch": {
            "anfaenglicheTilgung": 0,
            "ausgesetztBerechnet": false,
            "ausgesetztEigenesAngebot": false,
            "bausparWunsch": {
              "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
              "bausparSummeAbsolut": 0,
              "bausparSummeRelativ": 0,
              "bausparTarif": [
                {
                  "id": "string",
                  "kurzName": "string",
                  "langName": "string",
                  "produktAnbieter": "string",
                  "riesterFoerderung": true,
                  "status": "AKTIV"
                }
              ],
              "bausparTarife": [
                "string"
              ],
              "id": "string",
              "sonderZahlungEinmalig": 0,
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparBeginn": "2020-02-24",
              "sparBeitragMonatlichAbsolut": 0,
              "sparBeitragMonatlichRelativ": 0,
              "tilgungsBeitragMonatlich": 0,
              "vertragsPartnerIds": [
                "string"
              ],
              "verwendung": "ZINS_ABSICHERUNG",
              "zuteilungsDatum": "2020-02-24"
            },
            "rate": 0,
            "tilgungsBeginn": "2020-02-24",
            "tilgungsErsatzProduktId": "string",
            "volltilgerWennAnnuitaetenOderForward": false
          },
          "zinsBindungInJahren": 0
        },
        "forwardDarlehen": {
          "auszahlungsDatum": "2020-02-24",
          "bereitstellungsZinsFreieZeitInMonaten": 0,
          "darlehensBetrag": 0,
          "provision": 0,
          "sondertilgungOptionalJaehrlich": 0,
          "tilgungsWunsch": {
            "anfaenglicheTilgung": 0,
            "ausgesetztBerechnet": false,
            "ausgesetztEigenesAngebot": false,
            "bausparWunsch": {
              "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
              "bausparSummeAbsolut": 0,
              "bausparSummeRelativ": 0,
              "bausparTarif": [
                {
                  "id": "string",
                  "kurzName": "string",
                  "langName": "string",
                  "produktAnbieter": "string",
                  "riesterFoerderung": true,
                  "status": "AKTIV"
                }
              ],
              "bausparTarife": [
                "string"
              ],
              "id": "string",
              "sonderZahlungEinmalig": 0,
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparBeginn": "2020-02-24",
              "sparBeitragMonatlichAbsolut": 0,
              "sparBeitragMonatlichRelativ": 0,
              "tilgungsBeitragMonatlich": 0,
              "vertragsPartnerIds": [
                "string"
              ],
              "verwendung": "ZINS_ABSICHERUNG",
              "zuteilungsDatum": "2020-02-24"
            },
            "rate": 0,
            "tilgungsBeginn": "2020-02-24",
            "tilgungsErsatzProduktId": "string",
            "volltilgerWennAnnuitaetenOderForward": false
          },
          "zinsBindungInJahren": 0
        },
        "id": "string",
        "kfwDarlehen": {
          "darlehensBetrag": 0,
          "kfwEndfaellig": "NEIN",
          "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
          "kfwProgramm": "PROGRAMM_124",
          "laufzeitInJahren": 0,
          "provision": 0,
          "tilgungsWunsch": {
            "anfaenglicheTilgung": 0,
            "ausgesetztBerechnet": false,
            "ausgesetztEigenesAngebot": false,
            "bausparWunsch": {
              "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
              "bausparSummeAbsolut": 0,
              "bausparSummeRelativ": 0,
              "bausparTarif": [
                {
                  "id": "string",
                  "kurzName": "string",
                  "langName": "string",
                  "produktAnbieter": "string",
                  "riesterFoerderung": true,
                  "status": "AKTIV"
                }
              ],
              "bausparTarife": [
                "string"
              ],
              "id": "string",
              "sonderZahlungEinmalig": 0,
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparBeginn": "2020-02-24",
              "sparBeitragMonatlichAbsolut": 0,
              "sparBeitragMonatlichRelativ": 0,
              "tilgungsBeitragMonatlich": 0,
              "vertragsPartnerIds": [
                "string"
              ],
              "verwendung": "ZINS_ABSICHERUNG",
              "zuteilungsDatum": "2020-02-24"
            },
            "rate": 0,
            "tilgungsBeginn": "2020-02-24",
            "tilgungsErsatzProduktId": "string",
            "volltilgerWennAnnuitaetenOderForward": false
          },
          "tilgungsfreieAnlaufjahre": 0,
          "zinsBindungInJahren": 0
        },
        "privatDarlehen": {
          "darlehensBetrag": 0,
          "laufzeitInMonaten": 0,
          "provision": 0
        },
        "variablesDarlehen": {
          "darlehensBetrag": 0,
          "provision": 0,
          "tilgungsWunsch": {
            "anfaenglicheTilgung": 0,
            "ausgesetztBerechnet": false,
            "ausgesetztEigenesAngebot": false,
            "bausparWunsch": {
              "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
              "bausparSummeAbsolut": 0,
              "bausparSummeRelativ": 0,
              "bausparTarif": [
                {
                  "id": "string",
                  "kurzName": "string",
                  "langName": "string",
                  "produktAnbieter": "string",
                  "riesterFoerderung": true,
                  "status": "AKTIV"
                }
              ],
              "bausparTarife": [
                "string"
              ],
              "id": "string",
              "sonderZahlungEinmalig": 0,
              "sonderZahlungen": [
                {
                  "anzahl": 0,
                  "betrag": 0,
                  "termin": "2020-02-24",
                  "zahlweise": "EINMALIG"
                }
              ],
              "sparBeginn": "2020-02-24",
              "sparBeitragMonatlichAbsolut": 0,
              "sparBeitragMonatlichRelativ": 0,
              "tilgungsBeitragMonatlich": 0,
              "vertragsPartnerIds": [
                "string"
              ],
              "verwendung": "ZINS_ABSICHERUNG",
              "zuteilungsDatum": "2020-02-24"
            },
            "rate": 0,
            "tilgungsBeginn": "2020-02-24",
            "tilgungsErsatzProduktId": "string",
            "volltilgerWennAnnuitaetenOderForward": false
          }
        },
        "zwischenFinanzierung": {
          "darlehensBetrag": 0,
          "detailsZurVerwendung": "string",
          "maximaleLaufzeitInMonaten": 0,
          "provision": 0,
          "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
        }
      }
    ],
    "id": "string"
  },
  "id": "string",
  "nachfinanzierung": true,
  "nachrangigeExterneDarlehen": [
    {
      "darlehensBetrag": 0,
      "darlehensGeber": "string",
      "id": "string",
      "laufzeitEnde": "2020-02-24",
      "rateMonatlich": 0,
      "typ": "ARBEITGEBERDARLEHEN",
      "zinsBindung": {
        "endetAm": "2020-02-24",
        "jahre": 0,
        "monate": 0,
        "restschuldNachZinsBindungsEnde": 0
      }
    }
  ],
  "praeferenzen": {
    "bereitstellungsZinsFreieZeit": {
      "darlehenBenoetigtInMonaten": 0,
      "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
      "zusatzlicheKommentare": "string"
    },
    "bestandteileDerFinanzierung": {
      "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
      "zusatzlicheKommentare": "string"
    },
    "hoeheDerRate": {
      "betrag": 0,
      "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
      "zusatzlicheKommentare": "string"
    },
    "laufzeit": {
      "bisZumJahr": "2016",
      "bisZurRenteImJahr": "2016",
      "inJahren": 0,
      "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
      "zusatzlicheKommentare": "string"
    },
    "sondertilgung": {
      "betragEinmalig": 0,
      "betragJaehrlich": 0,
      "praeferenzAuswahl": "JAEHRLICH",
      "zusatzlicheKommentare": "string"
    },
    "tilgungsSatzWechsel": {
      "mindestensBenoetigt": 0,
      "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
      "zusatzlicheKommentare": "string"
    },
    "weiterePraeferenz": "string",
    "zeitlicherRahmen": {
      "finanzierungszusageBis": "2020-02-24",
      "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
      "zusatzlicheKommentare": "string"
    },
    "zinsBindung": {
      "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
      "zinsBindungBisJahren": 0,
      "zinsBindungVonJahren": 0,
      "zinsBindungZwischenJahren": 0,
      "zusatzlicheKommentare": "string"
    }
  },
  "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
}

```

*Vorhaben*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|absicherungswunsch|[Absicherungswunsch](#schemaabsicherungswunsch)|false|none|none|
|eigenleistungWennNeubauOderModernisierungsmassnahmen|number|false|none|none|
|externeBausparAngebote|[[BausparAngebot](#schemabausparangebot)]|false|none|none|
|finanzbedarf|[Finanzbedarf](#schemafinanzbedarf)|false|none|none|
|finanzierungswunsch|[Finanzierungswunsch](#schemafinanzierungswunsch)|false|none|none|
|id|string|false|none|none|
|nachfinanzierung|boolean|false|none|none|
|nachrangigeExterneDarlehen|[[NachrangigesExternesDarlehen](#schemanachrangigesexternesdarlehen)]|false|none|none|
|praeferenzen|[Praeferenzen](#schemapraeferenzen)|false|none|none|
|verwendungszweck|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|verwendungszweck|ANSCHLUSSFINANZIERUNG|
|verwendungszweck|KAUF|
|verwendungszweck|KAUF_NEUBAU_VOM_BAUTRAEGER|
|verwendungszweck|MODERNISIERUNG_UMBAU_ANBAU|
|verwendungszweck|NEUBAU|
|verwendungszweck|KAPITALBESCHAFFUNG|

<h2 id="tocSwertpapiere">Wertpapiere</h2>

<a id="schemawertpapiere"></a>

```json
{
  "aktuellerWert": 0,
  "dividendenJaehrlich": 0,
  "ertrag": 0,
  "maximalAufzuloesenderWert": 0,
  "vermoegensEinsatz": "KEIN_EINSATZ",
  "vermoegensTyp": "VERMOEGEN",
  "zahlungsTyp": "EINNAHME",
  "zukuenftigeEinnahmen": 0
}

```

*Wertpapiere*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|aktuellerWert|number|false|none|none|
|dividendenJaehrlich|number|false|none|none|
|ertrag|number|false|none|none|
|maximalAufzuloesenderWert|number|false|none|none|
|vermoegensEinsatz|string|false|none|none|
|vermoegensTyp|string|false|none|Redundante Angabe des Vermögenstyp dient als zusätzliches Filterkriterium|
|zahlungsTyp|string|false|none|Redundante Angabe des Zahlungstyps dient als zusätzliches Filterkriterium|
|zukuenftigeEinnahmen|number|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|vermoegensEinsatz|KEIN_EINSATZ|
|vermoegensEinsatz|ABTRETEN|
|vermoegensEinsatz|AUFLOESEN|
|vermoegensTyp|VERMOEGEN|
|vermoegensTyp|VERBINDLICHKEIT|
|zahlungsTyp|EINNAHME|
|zahlungsTyp|AUSGABE|

<h2 id="tocSzeitlicherrahmenpraeferenz">ZeitlicherRahmenPraeferenz</h2>

<a id="schemazeitlicherrahmenpraeferenz"></a>

```json
{
  "finanzierungszusageBis": "2020-02-24",
  "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
  "zusatzlicheKommentare": "string"
}

```

*ZeitlicherRahmenPraeferenz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|finanzierungszusageBis|string(date)|false|none|wenn praeferenzAuswahl == ZUSAGE_BIS|
|praeferenzAuswahl|string|false|none|none|
|zusatzlicheKommentare|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praeferenzAuswahl|NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN|
|praeferenzAuswahl|ZUSAGE_BIS|
|praeferenzAuswahl|SO_SCHNELL_WIE_MOEGLICH|
|praeferenzAuswahl|EGAL|

<h2 id="tocSzinsbindung">ZinsBindung</h2>

<a id="schemazinsbindung"></a>

```json
{
  "endetAm": "2020-02-24",
  "jahre": 0,
  "monate": 0,
  "restschuldNachZinsBindungsEnde": 0
}

```

*ZinsBindung*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|endetAm|string(date)|false|none|none|
|jahre|integer(int32)|false|none|none|
|monate|integer(int32)|false|none|none|
|restschuldNachZinsBindungsEnde|number|false|none|none|

<h2 id="tocSzinsbindungpraeferenz">ZinsBindungPraeferenz</h2>

<a id="schemazinsbindungpraeferenz"></a>

```json
{
  "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
  "zinsBindungBisJahren": 0,
  "zinsBindungVonJahren": 0,
  "zinsBindungZwischenJahren": 0,
  "zusatzlicheKommentare": "string"
}

```

*ZinsBindungPraeferenz*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|praeferenzAuswahl|string|false|none|none|
|zinsBindungBisJahren|integer(int32)|false|none|wenn praeferenzAuswahl == ZWISCHEN_BIS_JAHREN|
|zinsBindungVonJahren|integer(int32)|false|none|wenn praeferenzAuswahl == ZINSBINDUNG_VON_JAHREN|
|zinsBindungZwischenJahren|integer(int32)|false|none|wenn praeferenzAuswahl == ZWISCHEN_BIS_JAHREN|
|zusatzlicheKommentare|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|praeferenzAuswahl|ZINSBINDUNG_VON_JAHREN|
|praeferenzAuswahl|ZWISCHEN_BIS_JAHREN|
|praeferenzAuswahl|FLEXIBEL_KURZFRISTIG_HANDLUNGSFAEHIG|
|praeferenzAuswahl|LANGE_ZINSSICHERHEIT|
|praeferenzAuswahl|EGAL|

<h2 id="tocSzugrundeliegendedaten">ZugrundeliegendeDaten</h2>

<a id="schemazugrundeliegendedaten"></a>

```json
{
  "bankverbindung": {
    "bic": "string",
    "iban": "string",
    "id": "string",
    "kontoinhaberIds": [
      "string"
    ],
    "kontoinhaberName": "string",
    "kreditinstitut": "string"
  },
  "finanzierungsObjekt": {
    "adresse": {
      "hausnummer": "string",
      "ort": "string",
      "postleitzahl": "string",
      "strasse": "string"
    },
    "autostellplaetze": [
      {
        "mieteinnahmenMonatlich": 0,
        "typ": "STELLPLATZ"
      }
    ],
    "bestehendeDarlehen": [
      {
        "abzuloesendeRestschuld": 0,
        "aktuelleRestschuldWennNichtAbzuloesen": 0,
        "darlehensArt": "BAUSPARDARLEHEN",
        "darlehensBetrag": 0,
        "darlehensGeber": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "darlehensKontonummer": "string",
        "eingetrageneGrundschuld": 0,
        "grundschuldArt": "BRIEF_GRUNDSCHULD",
        "id": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "sollZins": 0,
        "sondertilgungZumZinsBindungsEnde": 0,
        "verwendenAls": "ABLOESEN",
        "zinsBindungEndetAm": "2020-02-24"
      }
    ],
    "bewirtschaftungsKostenJaehrlich": 0,
    "bodenRichtwert": 0,
    "bundesland": "BADEN_WUERTTEMBERG",
    "effektivZinsErhoehendeKosten": {
      "anpassen": true,
      "grundbuchEintragungsKostenEinmalig": 0,
      "sonstigeKostenBezeichnung": "string",
      "sonstigeKostenEinmalig": 0,
      "wohnGebaeudeVersicherungsKostenJaehrlich": 0
    },
    "erbbaurecht": {
      "erbbaurecht": true,
      "erbbauzinsJaehrlich": 0,
      "grundstuecksEigentuemer": "ANDERE",
      "laufzeitBisJahr": "string"
    },
    "gebaeude": {
      "anzahlDerGewerbeeinheiten": 0,
      "anzahlDerWohneinheitenImGebaeude": 0,
      "anzahlVollgeschosse": 0,
      "aufbauFinanzierung": true,
      "aufzugVorhanden": true,
      "ausstattung": "EINFACH",
      "baujahr": "2016",
      "bauweise": "FACHWERK_MIT_STROH_LEHM",
      "bezeichnungWohneinheit": "string",
      "dachgeschossAusbau": "FLACHDACH",
      "einliegerwohnungVorhanden": true,
      "geschossLage": "UNTERGESCHOSS",
      "gewerbeflaeche": {
        "gesamtGroesse": 0,
        "vermietungsInformationen": {
          "mieteinnahmenNettoKaltMonatlich": 0,
          "nutzungsArt": "EIGENGENUTZT",
          "vermieteteFlaeche": 0
        }
      },
      "hausAnordnung": "FREISTEHEND",
      "hausTyp": "DOPPELHAUSHAELFTE",
      "istFertighaus": true,
      "kellerausbau": "AUSGEBAUT",
      "kubatur": 0,
      "miteigentumsAnteil": {
        "anteil": 0,
        "gesamt": 0
      },
      "modernisierungsAngaben": {
        "badWc": true,
        "bodenWandTreppe": true,
        "dach": true,
        "fenster": true,
        "heizungZentral": true,
        "modernisierungsGrad": "GERING",
        "modernisierungsJahr": "string",
        "raumaufteilung": true,
        "stromAbwasserHeizkoerper": true,
        "waermedaemmung": true,
        "wurdeModernisiert": true
      },
      "unterkellerung": "NICHT_UNTERKELLERT",
      "wohnflaeche": {
        "gesamtGroesse": 0,
        "vermietungsInformationen": {
          "mieteinnahmenNettoKaltMonatlich": 0,
          "nutzungsArt": "EIGENGENUTZT",
          "vermieteteFlaeche": 0
        }
      },
      "zustand": "SEHR_GUT"
    },
    "grundbuchAngabe": {
      "anmerkungen": "string",
      "bandUndBlatt": "string",
      "flurstuecke": [
        {
          "anteil": {
            "anteil": 0,
            "gesamt": 0
          },
          "flur": "string",
          "flurstuecksNummer": "string",
          "groesse": 0
        }
      ],
      "ort": "string",
      "rechteInAbteilung2": {
        "beschreibung": "string",
        "betrag": 0,
        "vorhanden": true
      }
    },
    "grundstueck": {
      "groesse": 0,
      "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
    },
    "id": "string",
    "keinBaulandFlaecheInQm": 0,
    "marktueblicherKaufpreisProQm": 0,
    "marktwert": 0,
    "objektArt": "GRUNDSTUECK",
    "vergleichsmieteFuerGewerbeflaecheProQm": 0,
    "vergleichsmieteFuerWohnflaecheProQm": 0,
    "verkehrswert": 0,
    "vorlaeufigerVerkehrswert": 0,
    "wohnlage": "GEHOBEN"
  },
  "haushalte": [
    {
      "antragsteller": [
        {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "arbeitserlaubnis": false,
          "arbeitserlaubnisBefristetBis": "2020-02-24",
          "aufenthaltsTitel": "VISUM",
          "aufenthaltsTitelBefristetBis": "2020-02-24",
          "beschaeftigung": {
            "anzahlGehaelterProJahr": 0,
            "arbeitgeber": "string",
            "arbeitgeberInDeutschlandAnsaessig": false,
            "arbeitgeberLand": {
              "isoCountryCode": "string",
              "name": "string"
            },
            "art": "ANGESTELLTER",
            "befristungsStatus": "BEFRISTET",
            "beruf": "string",
            "beschaeftigtSeit": "2020-02-24",
            "branche": "LANDWIRTSCHAFT_FORSTWIRTSCHAFT_FISCHEREI",
            "einkommenNettoJaehrlich": 0,
            "einkommenNettoMonatlich": 0,
            "firma": "string",
            "inProbezeit": false,
            "situationNachRenteneintritt": {
              "gesetzlicheRenteMonatlich": 0,
              "privateRenteMonatlich": 0,
              "rentenBeginn": "2020-02-24",
              "sonstigesEinkommenMonatlich": 0
            },
            "taetigkeit": "ALTENPFLEGER"
          },
          "bruttoVorjahresEinkommen": 0,
          "email": "max.mustermann@test.de",
          "externeAntragstellerId": "string",
          "familienstand": "GESCHIEDEN",
          "geburtsdatum": "2020-02-24",
          "geburtsort": "string",
          "guetertrennungVereinbartWennVerheiratet": false,
          "id": "string",
          "inDeutschlandSeit": "2020-02-24",
          "legitimationsDaten": {
            "ausstellendeBehoerde": "string",
            "ausstellungsdatum": "2020-02-24",
            "ausweisArt": "PERSONALAUSWEIS",
            "ausweisArtBeiAndererAusweis": "string",
            "ausweisNummer": "string"
          },
          "nachname": "string",
          "schufaErgebnis": {
            "antragstellerUnbekannt": false,
            "inManuellerNachbehandlung": false,
            "score": "string"
          },
          "staatsangehoerigkeit": {
            "isoCountryCode": "string",
            "name": "string"
          },
          "steuerId": "string",
          "telefonnummer": "string",
          "telefonnummerVorwahl": "string",
          "titel": [
            "DOKTOR"
          ],
          "titelDoktor": true,
          "titelProfessor": true,
          "vorAnschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "vorname": "string",
          "weitereKontaktMoeglichkeiten": "string",
          "wohnhaftSeit": "2020-02-24"
        }
      ],
      "anzahlErwachseneImHaushalt": 0,
      "anzahlKinderNichtImHaushalt": 0,
      "bestehendeImmobilien": [
        {
          "adresse": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "autostellplaetze": [
            {
              "mieteinnahmenMonatlich": 0,
              "typ": "STELLPLATZ"
            }
          ],
          "bestehendeDarlehen": [
            {
              "abzuloesendeRestschuld": 0,
              "aktuelleRestschuldWennNichtAbzuloesen": 0,
              "darlehensArt": "BAUSPARDARLEHEN",
              "darlehensBetrag": 0,
              "darlehensGeber": {
                "anrede": "FRAU",
                "anschrift": {
                  "hausnummer": "string",
                  "ort": "string",
                  "postleitzahl": "string",
                  "strasse": "string"
                },
                "email": "string",
                "externePartnerId": "string",
                "externerKreditSachbearbeiterId": "string",
                "fax": "string",
                "firmenNameZusatz": "string",
                "firmierung": "string",
                "geburtsdatum": "2020-02-24",
                "id": "string",
                "kreditsachbearbeiter": true,
                "mobilTelefon": "string",
                "nachname": "string",
                "partnerId": "string",
                "produktAnbieterId": "string",
                "telefonnummer": "string",
                "vertriebsOrganisation": {
                  "firma": "string",
                  "name": "string",
                  "vertriebsOrganisationsId": "string"
                },
                "vorname": "string",
                "webseite": "string"
              },
              "darlehensKontonummer": "string",
              "eingetrageneGrundschuld": 0,
              "grundschuldArt": "BRIEF_GRUNDSCHULD",
              "id": "string",
              "laufzeitEnde": "2020-02-24",
              "rateMonatlich": 0,
              "sollZins": 0,
              "sondertilgungZumZinsBindungsEnde": 0,
              "zinsBindungEndetAm": "2020-02-24"
            }
          ],
          "bewirtschaftungsKostenJaehrlich": 0,
          "bodenRichtwert": 0,
          "bundesland": "BADEN_WUERTTEMBERG",
          "effektivZinsErhoehendeKosten": {
            "anpassen": true,
            "grundbuchEintragungsKostenEinmalig": 0,
            "sonstigeKostenBezeichnung": "string",
            "sonstigeKostenEinmalig": 0,
            "wohnGebaeudeVersicherungsKostenJaehrlich": 0
          },
          "erbbaurecht": {
            "erbbaurecht": true,
            "erbbauzinsJaehrlich": 0,
            "grundstuecksEigentuemer": "ANDERE",
            "laufzeitBisJahr": "string"
          },
          "gebaeude": {
            "anzahlDerGewerbeeinheiten": 0,
            "anzahlDerWohneinheitenImGebaeude": 0,
            "anzahlVollgeschosse": 0,
            "aufbauFinanzierung": true,
            "aufzugVorhanden": true,
            "ausstattung": "EINFACH",
            "baujahr": "2016",
            "bauweise": "FACHWERK_MIT_STROH_LEHM",
            "bezeichnungWohneinheit": "string",
            "dachgeschossAusbau": "FLACHDACH",
            "einliegerwohnungVorhanden": true,
            "geschossLage": "UNTERGESCHOSS",
            "gewerbeflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "hausAnordnung": "FREISTEHEND",
            "hausTyp": "DOPPELHAUSHAELFTE",
            "istFertighaus": true,
            "kellerausbau": "AUSGEBAUT",
            "kubatur": 0,
            "miteigentumsAnteil": {
              "anteil": 0,
              "gesamt": 0
            },
            "modernisierungsAngaben": {
              "badWc": true,
              "bodenWandTreppe": true,
              "dach": true,
              "fenster": true,
              "heizungZentral": true,
              "modernisierungsGrad": "GERING",
              "modernisierungsJahr": "string",
              "raumaufteilung": true,
              "stromAbwasserHeizkoerper": true,
              "waermedaemmung": true,
              "wurdeModernisiert": true
            },
            "unterkellerung": "NICHT_UNTERKELLERT",
            "wohnflaeche": {
              "gesamtGroesse": 0,
              "vermietungsInformationen": {
                "mieteinnahmenNettoKaltMonatlich": 0,
                "nutzungsArt": "EIGENGENUTZT",
                "vermieteteFlaeche": 0
              }
            },
            "zustand": "SEHR_GUT"
          },
          "grundbuchAngabe": {
            "anmerkungen": "string",
            "bandUndBlatt": "string",
            "flurstuecke": [
              {
                "anteil": {
                  "anteil": 0,
                  "gesamt": 0
                },
                "flur": "string",
                "flurstuecksNummer": "string",
                "groesse": 0
              }
            ],
            "ort": "string",
            "rechteInAbteilung2": {
              "beschreibung": "string",
              "betrag": 0,
              "vorhanden": true
            }
          },
          "grundstueck": {
            "groesse": 0,
            "grundstuecksArt": "UNBEBAUTES_WOHNGRUNDSTUECK"
          },
          "id": "string",
          "immobilienEinsatz": "KEIN_EINSATZ",
          "keinBaulandFlaecheInQm": 0,
          "keineBestehendenDarlehenVorhanden": true,
          "marktueblicherKaufpreisProQm": 0,
          "marktwert": 0,
          "maximalEinzusetzenderBetragWennVerkauf": 0,
          "objektArt": "GRUNDSTUECK",
          "vergleichsmieteFuerGewerbeflaecheProQm": 0,
          "vergleichsmieteFuerWohnflaecheProQm": 0,
          "verkehrswert": 0,
          "vorlaeufigerVerkehrswert": 0,
          "wohnlage": "GEHOBEN"
        }
      ],
      "id": "string",
      "kfzAnzahl": 0,
      "kinder": [
        {
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kindergeldWirdBezogen": true,
          "name": "string",
          "unterhaltsEinnahmenBetragMonatlich": 0
        }
      ],
      "lebenshaltungsKostenMonatlich": 0,
      "obligo": {
        "vermoegenOderVerbindlichkeiten": [
          {
            "aktuellerWert": 0,
            "anrechnungFuerBlankoAnteil": 0,
            "bezeichner": "string",
            "kontonummer": "string",
            "vermoegensTyp": "VERMOEGEN"
          }
        ]
      },
      "positionen": {
        "bankUndSparguthaben": [
          {
            "aktuellerWert": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zinsertragJaehrlich": 0,
            "zukuenftigeEinnahmen": 0
          }
        ],
        "bausparvertraege": [
          {
            "abschlussGebuehr": 0,
            "aktuellerWert": 0,
            "bausparSumme": 0,
            "einmalzahlung": 0,
            "ertrag": 0,
            "id": "string",
            "maximalAufzuloesenderBetrag": 0,
            "produktAnbieter": {
              "anrede": "FRAU",
              "anschrift": {
                "hausnummer": "string",
                "ort": "string",
                "postleitzahl": "string",
                "strasse": "string"
              },
              "email": "string",
              "externePartnerId": "string",
              "externerKreditSachbearbeiterId": "string",
              "fax": "string",
              "firmenNameZusatz": "string",
              "firmierung": "string",
              "geburtsdatum": "2020-02-24",
              "id": "string",
              "kreditsachbearbeiter": true,
              "mobilTelefon": "string",
              "nachname": "string",
              "partnerId": "string",
              "produktAnbieterId": "string",
              "telefonnummer": "string",
              "vertriebsOrganisation": {
                "firma": "string",
                "name": "string",
                "vertriebsOrganisationsId": "string"
              },
              "vorname": "string",
              "webseite": "string"
            },
            "sonderZahlungen": [
              {
                "anzahl": 0,
                "betrag": 0,
                "termin": "2020-02-24",
                "zahlweise": "EINMALIG"
              }
            ],
            "sparBeitragMonatlich": 0,
            "tarif": "string",
            "typ": "string",
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "vertragsBeginn": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0,
            "zuteilungsDatum": "2020-02-24"
          }
        ],
        "ehegattenUnterhalt": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "einkuenfteAusNebentaetigkeit": [
          {
            "beginnDerNebentaetigkeit": "2020-02-24",
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "kindergeld": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "lebensUndRentenVersicherungen": [
          {
            "id": "string",
            "maximalAufzuloesenderBetrag": 0,
            "praemieMonatlich": 0,
            "rueckkaufsWertAktuell": 0,
            "tarif": "string",
            "typ": "KAPITALBILDENDE_LEBENSVERSICHERUNG",
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "versicherungsGesellschaft": "string",
            "versicherungsSumme": 0,
            "vertragsBeginn": "2020-02-24",
            "vertragsEnde": "2020-02-24",
            "vertragsNummer": "string",
            "verwaltungsgebuehrenJaehrlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "mietAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "entfallenMitFinanzierung": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "privateDarlehen": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "privateKrankenversicherung": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "ratenkredite": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeEinnahmen": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeVerbindlichkeiten": [
          {
            "glaeubiger": "string",
            "laufzeitEnde": "2020-02-24",
            "rateMonatlich": 0,
            "restschuld": 0,
            "vermoegensTyp": "VERMOEGEN",
            "wirdAbgeloest": true,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "sonstigeVermoegen": [
          {
            "aktuellerWert": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zukuenftigeEinnahmen": 0
          }
        ],
        "sparplaene": [
          {
            "aktuellerWert": 0,
            "beitragMonatlich": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0
          }
        ],
        "unbefristeteZusatzRenten": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "unterhaltsVerpflichtungen": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "variableEinkuenfte": [
          {
            "einnahmenMonatlich": 0,
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "versicherungsAusgaben": [
          {
            "ausgabenMonatlich": 0,
            "berechnungsHilfeVermoegen": {
              "betragNachFinanzierung": 0,
              "betragVorFinanzierung": 0
            },
            "zahlungsTyp": "EINNAHME"
          }
        ],
        "wertpapiere": [
          {
            "aktuellerWert": 0,
            "dividendenJaehrlich": 0,
            "ertrag": 0,
            "maximalAufzuloesenderWert": 0,
            "vermoegensEinsatz": "KEIN_EINSATZ",
            "vermoegensTyp": "VERMOEGEN",
            "zahlungsTyp": "EINNAHME",
            "zukuenftigeEinnahmen": 0
          }
        ]
      }
    }
  ],
  "vorhaben": {
    "absicherungswunsch": {
      "id": "string",
      "versicherungsWuensche": [
        {
          "finanzierungsWeise": "DURCH_HAUPTDARLEHEN",
          "id": "string",
          "praemienZahlungsweise": "EINMALIG",
          "risikoAbsicherungsWuensche": [
            {
              "abzusicherndesRisiko": "TODESFALL",
              "versicherteRate": 0,
              "versicherungsSumme": 0
            }
          ],
          "versichertePersonId": "string",
          "versicherungsArt": "RATENSCHUTZVERSICHERUNG",
          "versicherungsBeginn": "2020-02-24",
          "versicherungsDauerInMonaten": 0
        }
      ]
    },
    "eigenleistungWennNeubauOderModernisierungsmassnahmen": 0,
    "externeBausparAngebote": [
      {
        "abschlussGebuehr": 0,
        "angebotsHinweisFuerAntragsteller": "string",
        "bausparSumme": 0,
        "einmalzahlung": 0,
        "id": "string",
        "produktAnbieter": {
          "anrede": "FRAU",
          "anschrift": {
            "hausnummer": "string",
            "ort": "string",
            "postleitzahl": "string",
            "strasse": "string"
          },
          "email": "string",
          "externePartnerId": "string",
          "externerKreditSachbearbeiterId": "string",
          "fax": "string",
          "firmenNameZusatz": "string",
          "firmierung": "string",
          "geburtsdatum": "2020-02-24",
          "id": "string",
          "kreditsachbearbeiter": true,
          "mobilTelefon": "string",
          "nachname": "string",
          "partnerId": "string",
          "produktAnbieterId": "string",
          "telefonnummer": "string",
          "vertriebsOrganisation": {
            "firma": "string",
            "name": "string",
            "vertriebsOrganisationsId": "string"
          },
          "vorname": "string",
          "webseite": "string"
        },
        "sonderZahlungen": [
          {
            "anzahl": 0,
            "betrag": 0,
            "termin": "2020-02-24",
            "zahlweise": "EINMALIG"
          }
        ],
        "sparPhase": {
          "guthabenBeiZuteilung": 0,
          "sparBeitragMonatlich": 0,
          "sparPhaseInJahren": 0
        },
        "tarif": "string",
        "tilgungsPhase": {
          "bausparDarlehenSumme": 0,
          "sollZinsNachZuteilung": 0,
          "tilgungsBeitragMonatlich": 0,
          "tilgungsPhaseInJahren": 0
        },
        "typ": "string",
        "vertragsBeginn": "2020-02-24",
        "vertragsNummer": "string",
        "verwaltungsgebuehrenJaehrlich": 0,
        "zuteilungsDatum": "2020-02-24"
      }
    ],
    "finanzbedarf": {
      "anzahlTeilzahlungen": 0,
      "aussenAnlagen": 0,
      "bauNebenkosten": 0,
      "beratungsHonorar": 0,
      "bereitsBeglichen": 0,
      "erschliessung": 0,
      "grunderwerbsteuer": 0,
      "grundstueckBereitsBezahlt": true,
      "grundstuecksKaufpreis": 0,
      "herstellung": 0,
      "kapitalBeschaffung": 0,
      "kapitalWirdBeschafft": true,
      "kaufpreis": 0,
      "maklergebuehr": 0,
      "mobiliar": 0,
      "modernisieren": true,
      "modernisierung": 0,
      "notargebuehr": 0,
      "renovierung": 0,
      "sonstigeKosten": 0,
      "zusaetzlichesKapital": 0
    },
    "finanzierungswunsch": {
      "bausparWuensche": [
        {
          "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
          "bausparSummeAbsolut": 0,
          "bausparSummeRelativ": 0,
          "bausparTarif": [
            {
              "id": "string",
              "kurzName": "string",
              "langName": "string",
              "produktAnbieter": "string",
              "riesterFoerderung": true,
              "status": "AKTIV"
            }
          ],
          "bausparTarife": [
            "string"
          ],
          "id": "string",
          "sonderZahlungEinmalig": 0,
          "sonderZahlungen": [
            {
              "anzahl": 0,
              "betrag": 0,
              "termin": "2020-02-24",
              "zahlweise": "EINMALIG"
            }
          ],
          "sparBeginn": "2020-02-24",
          "sparBeitragMonatlichAbsolut": 0,
          "sparBeitragMonatlichRelativ": 0,
          "tilgungsBeitragMonatlich": 0,
          "vertragsPartnerIds": [
            "string"
          ],
          "verwendung": "ZINS_ABSICHERUNG",
          "zuteilungsDatum": "2020-02-24"
        }
      ],
      "darlehensWuensche": [
        {
          "annuitaetenDarlehen": {
            "auszahlungsDatum": "2020-02-24",
            "bereitstellungsZinsFreieZeitInMonaten": 0,
            "darlehensBetrag": 0,
            "provision": 0,
            "sondertilgungOptionalJaehrlich": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "zinsBindungInJahren": 0
          },
          "forwardDarlehen": {
            "auszahlungsDatum": "2020-02-24",
            "bereitstellungsZinsFreieZeitInMonaten": 0,
            "darlehensBetrag": 0,
            "provision": 0,
            "sondertilgungOptionalJaehrlich": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "zinsBindungInJahren": 0
          },
          "id": "string",
          "kfwDarlehen": {
            "darlehensBetrag": 0,
            "kfwEndfaellig": "NEIN",
            "kfwEnergieEffizienzStandard": "STANDARD_40_PLUS",
            "kfwProgramm": "PROGRAMM_124",
            "laufzeitInJahren": 0,
            "provision": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            },
            "tilgungsfreieAnlaufjahre": 0,
            "zinsBindungInJahren": 0
          },
          "privatDarlehen": {
            "darlehensBetrag": 0,
            "laufzeitInMonaten": 0,
            "provision": 0
          },
          "variablesDarlehen": {
            "darlehensBetrag": 0,
            "provision": 0,
            "tilgungsWunsch": {
              "anfaenglicheTilgung": 0,
              "ausgesetztBerechnet": false,
              "ausgesetztEigenesAngebot": false,
              "bausparWunsch": {
                "abschlussGebuehrenVerrechnung": "SOFORTZAHLUNG",
                "bausparSummeAbsolut": 0,
                "bausparSummeRelativ": 0,
                "bausparTarif": [
                  {
                    "id": "string",
                    "kurzName": "string",
                    "langName": "string",
                    "produktAnbieter": "string",
                    "riesterFoerderung": true,
                    "status": "AKTIV"
                  }
                ],
                "bausparTarife": [
                  "string"
                ],
                "id": "string",
                "sonderZahlungEinmalig": 0,
                "sonderZahlungen": [
                  {
                    "anzahl": 0,
                    "betrag": 0,
                    "termin": "2020-02-24",
                    "zahlweise": "EINMALIG"
                  }
                ],
                "sparBeginn": "2020-02-24",
                "sparBeitragMonatlichAbsolut": 0,
                "sparBeitragMonatlichRelativ": 0,
                "tilgungsBeitragMonatlich": 0,
                "vertragsPartnerIds": [
                  "string"
                ],
                "verwendung": "ZINS_ABSICHERUNG",
                "zuteilungsDatum": "2020-02-24"
              },
              "rate": 0,
              "tilgungsBeginn": "2020-02-24",
              "tilgungsErsatzProduktId": "string",
              "volltilgerWennAnnuitaetenOderForward": false
            }
          },
          "zwischenFinanzierung": {
            "darlehensBetrag": 0,
            "detailsZurVerwendung": "string",
            "maximaleLaufzeitInMonaten": 0,
            "provision": 0,
            "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
          }
        }
      ],
      "id": "string"
    },
    "id": "string",
    "nachfinanzierung": true,
    "nachrangigeExterneDarlehen": [
      {
        "darlehensBetrag": 0,
        "darlehensGeber": "string",
        "id": "string",
        "laufzeitEnde": "2020-02-24",
        "rateMonatlich": 0,
        "typ": "ARBEITGEBERDARLEHEN",
        "zinsBindung": {
          "endetAm": "2020-02-24",
          "jahre": 0,
          "monate": 0,
          "restschuldNachZinsBindungsEnde": 0
        }
      }
    ],
    "praeferenzen": {
      "bereitstellungsZinsFreieZeit": {
        "darlehenBenoetigtInMonaten": 0,
        "praeferenzAuswahl": "MIT_DER_ERSTEN_AUSZAHLUNG",
        "zusatzlicheKommentare": "string"
      },
      "bestandteileDerFinanzierung": {
        "praeferenzAuswahl": "UNKOMPLIZIERTE_FINANZIERUNG",
        "zusatzlicheKommentare": "string"
      },
      "hoeheDerRate": {
        "betrag": 0,
        "praeferenzAuswahl": "MEINE_MIETAUSGABEN_VON_HEUTE",
        "zusatzlicheKommentare": "string"
      },
      "laufzeit": {
        "bisZumJahr": "2016",
        "bisZurRenteImJahr": "2016",
        "inJahren": 0,
        "praeferenzAuswahl": "MOEGLICHST_SCHNELL",
        "zusatzlicheKommentare": "string"
      },
      "sondertilgung": {
        "betragEinmalig": 0,
        "betragJaehrlich": 0,
        "praeferenzAuswahl": "JAEHRLICH",
        "zusatzlicheKommentare": "string"
      },
      "tilgungsSatzWechsel": {
        "mindestensBenoetigt": 0,
        "praeferenzAuswahl": "MINDESTENS_BENOETIGT",
        "zusatzlicheKommentare": "string"
      },
      "weiterePraeferenz": "string",
      "zeitlicherRahmen": {
        "finanzierungszusageBis": "2020-02-24",
        "praeferenzAuswahl": "NUR_INFORMATION_UEBER_FINANZIERUNGSRAHMEN",
        "zusatzlicheKommentare": "string"
      },
      "zinsBindung": {
        "praeferenzAuswahl": "ZINSBINDUNG_VON_JAHREN",
        "zinsBindungBisJahren": 0,
        "zinsBindungVonJahren": 0,
        "zinsBindungZwischenJahren": 0,
        "zusatzlicheKommentare": "string"
      }
    },
    "verwendungszweck": "ANSCHLUSSFINANZIERUNG"
  }
}

```

*ZugrundeliegendeDaten*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bankverbindung|[Bankverbindung](#schemabankverbindung)|false|none|none|
|finanzierungsObjekt|[FinanzierungsObjekt](#schemafinanzierungsobjekt)|false|none|none|
|haushalte|[[Haushalt](#schemahaushalt)]|false|none|none|
|vorhaben|[Vorhaben](#schemavorhaben)|false|none|none|

<h2 id="tocSzwischenfinanzierungswunsch">ZwischenFinanzierungsWunsch</h2>

<a id="schemazwischenfinanzierungswunsch"></a>

```json
{
  "darlehensBetrag": 0,
  "detailsZurVerwendung": "string",
  "maximaleLaufzeitInMonaten": 0,
  "provision": 0,
  "verwendungszweck": "VORFINANZIERUNG_OEFFENTLICHER_MITTEL"
}

```

*ZwischenFinanzierungsWunsch*

#### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|darlehensBetrag|number|false|none|none|
|detailsZurVerwendung|string|false|none|none|
|maximaleLaufzeitInMonaten|integer(int32)|false|none|none|
|provision|number|false|none|none|
|verwendungszweck|string|false|none|none|

##### Enumerated Values

|Property|Value|
|---|---|
|verwendungszweck|VORFINANZIERUNG_OEFFENTLICHER_MITTEL|
|verwendungszweck|VERKAUF_EINES_ANDEREN_OBJEKTS|
|verwendungszweck|SONSTIGE_VERWENDUNG|

