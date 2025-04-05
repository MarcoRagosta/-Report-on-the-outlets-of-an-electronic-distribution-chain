# TechMarket S.p.A. - Report Vendite

## Descrizione del Progetto

Questo progetto riguarda la creazione di un report Power BI per TechMarket S.p.A., una catena di distribuzione al dettaglio di prodotti elettronici. Il report è stato progettato per analizzare le vendite dei prodotti nei negozi in Italia durante l'anno 2014.

### Obiettivo:

- Visualizzare le vendite per ogni mese, considerando lo sconto, le unità e il prezzo.
- Visualizzare le unità vendute per ogni città.
- Visualizzare tutte le informazioni relative a ciascun prodotto.
- Visualizzare le informazioni per ciascun negozio, combinando dati di vendite e informazioni sui negozi.
- Creare una navigazione tra le diverse pagine tramite pulsanti.
- Implementare un segnalibro per salvare una vista importante.

**Punto Bonus**: Creare una pagina che calcola le vendite escluse i resi per i mesi di Gennaio e Febbraio.

---

## Struttura dei Dati

I dati utilizzati nel progetto sono contenuti in diversi file CSV:

1. **Cartella "DATI"**: Contiene i dati delle vendite per i vari punti vendita.
   - I file sono separati per mese (ad esempio `Gennaio.csv`, `Febbraio.csv`, ecc.).
   - Ogni file contiene informazioni su Prodotti, Quantità Vendute, Prezzo, Sconto e Data di vendita.

2. **Cartella "DATI NEGOZI"**: Contiene i dati relativi ai negozi, ai prodotti e alle province italiane.
   - Include informazioni sui negozi (ID, nome, città, provincia).
   - Include informazioni sui prodotti (ID prodotto, descrizione prodotto, prezzo unitario).

3. **File "RESI" (punto bonus)**: Contiene i dati relativi ai resi effettuati per i prodotti nei mesi di Gennaio e Febbraio.
   - Include l'ID prodotto, ID negozio, quantità resa e data di reso.

---

## Passaggi di Pulizia e Trasformazione dei Dati

### 1. Caricamento Dati:

- I dati sono stati caricati in Power BI utilizzando il menu **File** > **Carica Dati**.
- I file CSV sono stati importati nelle rispettive tabelle: `Vendite`, `Negozi`, `Prodotti`, `Province`, `Resi`.

### 2. Pulizia dei Dati:

- **Gestione dei valori nulli**:  
  In alcuni file, alcune righe presentavano valori nulli (ad esempio, nelle colonne Sconto o Quantità). Questi sono stati gestiti eliminando le righe incomplete o sostituendo i valori nulli con `0`.

  ```m
  #"Removed Null Values" = Table.SelectRows(#"Previous Step", each ([Sconto] <> null and [Quantita] <> null))

- **Formattazione delle date**:
  Le date nei file di vendite sono state formattate correttamente per poter essere utilizzate in visualizzazioni temporali (ad esempio, mese e anno).

  ```m
  #"Changed Type" = Table.TransformColumnTypes(#"Previous Step",{{"Data", type date}})

- **Rimozione dei duplicati**:
  I duplicati sono stati rimossi dove presente una duplicazione nelle righe delle vendite.

  ```m
  #"Removed Duplicates" = Table.Distinct(#"Previous Step")

  
