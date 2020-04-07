# Dashboard COVID-19 Regione Umbria

Questo repository è dedicato alla raccolta e visualizzazione dei dati relativi all'emergenza COVID-19 in Umbria.

(BETA attualmente in costruzione)

La dashboard è stata realizzata dalla Regione Umbria allo scopo di informare i cittadini e mettere a disposizione in modo trasparente i dati raccolti, utili ai soli fini comunicativi e informativi, sotto licenza CC-BY-4.0.
I dati vengono pubblicati nella dashboard anche più volte al giorno,  in base al loro aggiornamento progressivo e dopo validazione da parte del COR. Occorre quindi fare riferimento a data ed orario indicati per ogni informazione. Inoltre, non tutte le fonti dati sono aggiornate con la stessa cadenza temporale.Per eventuali segnalazioni sui dati: [prociv@regione.umbria.it](mailto:prociv@regione.umbria.it)

I dati grezzi utilizzati dalla dashboard saranno presto resi disponibili attraverso [interfacce API](https://apistore.regione.umbria.it/store/) e tramite [dataset open data](http://dati.umbria.it/group/protezione-civile).

# Formato dati generali emergenza

_v.1.09 del 07/04/2020_

| Nome campo                  | Descrizione                       | Equivalente campo nazionale                  | Formato                       | Esempio             |
|-----------------------------|-----------------------------------|----------------------------------------|-------------------------------|---------------------|
| **data**                        | Data dell’informazione            | data                                   | YYYY-MM-DD HH:MM:SS (ISO 8601) Ora italiana | 2020-03-05 12:15:45 |
| **stato**                       | Stato di riferimento              | stato                                  | XYZ (ISO 3166-1 alpha-3)      | ITA                 |
| **codice_regione**              | Codice della Regione (ISTAT) | codice_regione                        | Numero    | 10                  |
| **denominazione_regione**              | Denominazione della Regione |denominazione_regione         | Testo                        | Umbria                  |
| **codice_geo**              | Codice area geografica (ISTAT per i comuni) o della struttura (ad es. ospedali) a cui si riferiscono i dati |         | Numero                        | 55004                  |
| **denominazione_geo**       | Denominazione dell'area o struttura a cui si riferiscono i dati       |                                                   | Testo                         | Amelia             |
| **tipo_geo**              | Tipo di area geografica o struttura a cui si riferiscono i dati |         | Testo                        | Comune                  |
| **lat_geo**                         | Latitudine (centroide)            | lat                               | WGS84                         | 42.6589177          |
| **long_geo**                        | Longitudine (centroide)           | long                              | WGS84                         | 13.70439971         |
| **residenti**                 | Totale residenti da ISTAT 2019              |                       | Numero                        | 11819                   |
| **casi_positivi**                 | Totale dei casi positivi ad oggi diagnosticati; _calcolo: attualmente_positivi + guariti + deceduti_              | totale_casi         | Numero                        | 3                   |
| **isolamento_volontario**      | Attuale numero di persone (non testate positive) che sono in isolamento fiduciario in casa o altra struttura non ospedaliera |                        | Numero                        | 3                   |
| **in_isolamento_domiciliare**      | Attuale numero di casi positivi che sono in isolamento contumaciale in casa o altra struttura non ospedaliera | isolamento_domiciliare                       | Numero                        | 3                   |
| **usciti_da_isolamento**      | Totale numero di casi positivi usciti dall'isolamento (non più positivi al tampone) |                        | Numero                        | 3                   |
| **ricoverati_totale**        | Attuale numero dei casi positivi che sono ricoverati in ospedale; _calcolo: di_cui_ricoverati_con_sintomi + di_cui_ricoverati_in_terapia_intensiva_              | totale_ospedalizzati            | Numero                        | 3                   |
| **di_cui_ricoverati_con_sintomi**      | Attuale numero di casi positivi che sono ricoverati in reparti diversi dalla terapia intensiva | ricoverati_con_sintomi    | Numero                        | 3                   |
| **di_cui_ricoverati_in_terapia_intensiva**           | Attuale numero di casi positivi ricoverati in terapia intensiva   | terapia_intensiva                         | Numero                        | 3                   |
| **attualmente_positivi** | Attuale numero di casi positivi; _calcolo: ricoverati_totale + in_isolamento_domiciliare_      | totale_positivi  | Numero                        | 3                   |
| **nuovi_positivi**  | Nuovi attualmente positivi; _calcolo: attualmente_positivi - attualmente_positivi del giorno prima_       | nuovi_positivi  | Numero                        | 3                   |
| **tasso_positivi_x1000**  | Tasso attuali casi positivi ogni 1000 abitanti residenti; _calcolo: attualmente_positivi / residenti * 1000_  |   | Numero                        | 0,85                   |
| **sign_positivi_x1000**  | Significatività degli attuali casi positivi ogni 1000 abitanti residenti rispetto al tasso medio regionale; _calcolo: 1 se tasso_positivi_x1000 superiore del 5% alla media, oppure -1 se tasso_positivi_x1000 inferiore del 5% alla media, altrimenti 0 se intorno alla media_  |   | Numero                        | 1                   |
| **guariti**             | Totale dei casi positivi che risolvono i sintomi dell’infezione da Covid-19 e che risultano negativi in due test consecutivi effettuati a distanza di 24 ore uno dall’altro           | dimessi_guariti                            | Numero                        | 3                   |
| **guariti_clinici**             | Totale dei casi positivi che risultano clinicamente guariti, anche se ancora positivi al test. Pur non essendo più necessario il ricovero, la persona non può ritornare alla vita di comunità perché ancora con una carica virale elevata.      |                             | Numero                        | 3                   |
| **deceduti**                    | Totale dei casi positivi che sono deceduti, anche con diagnosi post-mortem; La conferma che la causa del decesso è attribuibile esclusivamente al SARS-CoV-2 verrà dichiarata dall’Istituto Superiore di Sanità | deceduti                                  | Numero                        | 3                   |
| **tamponi_eseguiti**                     | Totale dei tamponi (test) effettuati, un soggetto può essere sottoposto a più tamponi quindi non è indicativo delle persone controllate       | tamponi                        | Numero                        | 3                   |
| **tamponi_positivi**                     | Totale dei tamponi (test) effettuati con esito positivo       |                         | Numero                        | 3                   |
| **tasso_tamponi_positivi**                     | Tasso percentuale di tamponi effettuati con esito positivo; _calcolo: tamponi_positivi * 100 / tamponi_eseguiti_       |                         | Numero                        | 3                   |
| **note**                     | Eventuali note sul dato raccolto. In questo campo viene indicata anche l'eventuale revisione di aggiornamento del dato.       |                         | Testo                        | XYZ                   |
| **status**                     | Se dato ufficiale confermato = "pub"       |                         | Testo                        | pub                   |
