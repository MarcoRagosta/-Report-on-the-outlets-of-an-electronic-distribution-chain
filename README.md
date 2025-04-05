# -TechMarket S.p.A. - Report Vendite
#### Descrizione del Progetto

Questo progetto riguarda la creazione di un report Power BI per TechMarket S.p.A., una catena di distribuzione al dettaglio di prodotti elettronici. Il report è stato progettato per analizzare le vendite dei prodotti nei negozi in Italia durante l'anno 2014.

#### Obiettivo:
Visualizzare le vendite per ogni mese, considerando lo sconto, le unità e il prezzo.

Visualizzare le unità vendute per ogni città.

Visualizzare tutte le informazioni relative a ciascun prodotto.

Visualizzare le informazioni per ciascun negozio, combinando dati di vendite e informazioni sui negozi.

Creare una navigazione tra le diverse pagine tramite pulsanti.

Implementare un segnalibro per salvare una vista importante.

Punto Bonus: Creare una pagina che calcola le vendite escluse i resi per i mesi di Gennaio e Febbraio.

Struttura dei Dati
I dati utilizzati nel progetto sono contenuti in diversi file CSV:

Cartella "DATI": Contiene i dati delle vendite per i vari punti vendita.

I file sono separati per mese (ad esempio Gennaio.csv, Febbraio.csv, ecc.).

Ogni file contiene informazioni su Prodotti, Quantità Vendute, Prezzo, Sconto e Data di vendita.

Cartella "DATI NEGOZI": Contiene i dati relativi ai negozi, ai prodotti e alle province italiane.

Include informazioni sui negozi (ID, nome, città, provincia).

Include informazioni sui prodotti (ID prodotto, descrizione prodotto, prezzo unitario).

File "RESI" (punto bonus): Contiene i dati relativi ai resi effettuati per i prodotti nei mesi di Gennaio e Febbraio.

Include l'ID prodotto, ID negozio, quantità resa e data di reso.

Passaggi di Pulizia e Trasformazione dei Dati
Caricamento Dati:

I dati sono stati caricati in Power BI utilizzando il File > Carica Dati.

I file CSV sono stati importati nelle rispettive tabelle: Vendite, Negozi, Prodotti, Province, Resi.

Pulizia dei Dati:

Gestione dei valori nulli: In alcuni file, alcune righe presentavano valori nulli (ad esempio, nelle colonne Sconto o Quantità). Questi sono stati gestiti eliminando le righe incomplete o sostituendo i valori nulli con 0.

Formattazione delle date: Le date nei file di vendite sono state formattate correttamente per poter essere utilizzate in visualizzazioni temporali (ad esempio, mese e anno).

Rimozione di duplicati: I duplicati sono stati rimossi dove presente una duplicazione nelle righe delle vendite.

Transformazione dei Dati:

Unione delle tabelle:

Utilizzando la funzione Merge di Power Query, sono state unite le tabelle Vendite e Prodotti tramite il campo Prodotto_ID, così da includere la descrizione del prodotto e il prezzo unitario nelle vendite.

È stato anche unito il file Negozi con la tabella Vendite tramite l'ID del negozio, così da includere tutte le informazioni relative al negozio (nome, città, provincia).

Creazione delle colonne calcolate:

È stata creata una colonna calcolata per calcolare il Totale Vendite come il prodotto di Quantità e Prezzo (tenendo conto anche degli sconti applicati).

Creazione delle relazioni:

Sono state create le relazioni tra le tabelle, utilizzando gli ID dei prodotti, degli negozi e delle vendite. Le relazioni chiave sono:

Vendite[Prodotto_ID] → Prodotti[Prodotto_ID]

Vendite[Negozi_ID] → Negozi[Negozi_ID]

Negozi[Provincia_ID] → Province[Provincia_ID]

Creazione del Report:

Pagina 1 (Vendite per mese):

Una visualizzazione temporale è stata creata per mostrare le vendite totali per mese. Vengono considerati anche gli sconti e il numero di unità vendute.

Pagina 2 (Unità Vendute per città):

Una visualizzazione a mappa è stata creata per visualizzare le unità vendute per ogni città, in base alla relazione con le province.

Pagina 3 (Informazioni prodotto):

Una tabella è stata creata per visualizzare tutte le informazioni sui prodotti, con descrizione, prezzo unitario e quantità venduta.

Pagina 4 (Informazioni negozio e vendite):

Una tabella unificata mostra le informazioni dei negozi insieme alle vendite, inclusi sconto, quantità e totale per ogni negozio.

Funzionalità Bonus:

È stata creata una pagina che visualizza le vendite escluse i resi per i mesi di Gennaio e Febbraio, utilizzando il file Resi per sottrarre i resi dal totale vendite.

Interattività e Navigazione:

Sono stati creati Segnalibri per permettere all'utente di salvare e navigare tra le visualizzazioni più rilevanti.

È stata configurata una navigazione tramite pulsanti che consente di spostarsi tra le diverse pagine del report.

Istruzioni per l'Uso del Report
Pagina 1 (Vendite per mese): Visualizza le vendite totali per mese, tenendo conto dello sconto e delle unità vendute.

Pagina 2 (Unità Vendute per città): Mostra le unità vendute per ciascuna città.

Pagina 3 (Informazioni prodotto): Dettagli per ciascun prodotto, inclusi descrizione, prezzo e quantità venduta.

Pagina 4 (Informazioni negozio): Mostra le informazioni per ciascun negozio, combinando i dati di vendita e le informazioni sui negozi.

File ZIP e Consegna
Se si verifica un errore durante il caricamento del file .pbi, è stato compresso il progetto in un file ZIP. Assicurati di caricare il file ZIP sulla piattaforma per la consegna.

Contatti
Se hai domande o necessiti di chiarimenti, non esitare a contattarmi.
