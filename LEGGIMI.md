# Cassa Edile Dream – versione per GitHub Pages

Gioco formativo FILCA CISL sulle Casse Edili. Regia e tavoli girano su PC diversi e si sincronizzano attraverso un database Firebase gratuito. Chi gioca apre solo un link, senza account.

## I file

| File | A cosa serve |
| --- | --- |
| `index.html` | Il gioco (tavoli e regia) |
| `config.js` | I dati del vostro progetto Firebase: è l'unico file da modificare |
| `firestore.rules` | Le regole di sicurezza da incollare in Firebase |
| `LEGGIMI.md` | Queste istruzioni |

Se `config.js` resta vuoto il gioco funziona lo stesso, ma ogni dispositivo è isolato e i dati passano con i codici da copiare e incollare.

## 1. Creare il database Firebase (una volta sola, circa 10 minuti)

> **Già fatto.** Il progetto `cassa-edile-dream` esiste sull'account formazionefilca@gmail.com (database a Milano, regole pubblicate) e `config.js` è già compilato. Questa sezione serve solo se un giorno vorrete ricreare il database.

1. Andate su https://console.firebase.google.com ed entrate con un account Google.
2. **Crea un progetto** (o "Aggiungi progetto"). Nome, per esempio, `cassa-edile-dream`. Google Analytics non serve: potete disattivarlo.
3. Nel menu a sinistra aprite **Build → Firestore Database** e premete **Crea database**.
   - Località: scegliete una località europea (per esempio `eur3` o `europe-west8`, Milano). Non si può cambiare dopo.
   - Modalità: **produzione**.
4. Sempre in Firestore, aprite la scheda **Regole**, cancellate tutto, incollate il contenuto di `firestore.rules` e premete **Pubblica**.
5. Aprite l'ingranaggio in alto a sinistra → **Impostazioni progetto**. In "Le tue app" premete l'icona **Web `</>`**, date un nome all'app (per esempio `gioco`) e **non** attivate Firebase Hosting.
6. Firebase mostra un blocco `const firebaseConfig = { apiKey: "...", ... }`. Copiate i sei valori dentro `config.js`, tra le virgolette, campo per campo.

I valori di `config.js` non sono password: servono al browser per trovare il database. La protezione sta nelle regole del punto 4.

## 2. Pubblicare su GitHub Pages

1. Su https://github.com create un nuovo repository **pubblico**, per esempio `cassa-edile-dream`.
2. **Add file → Upload files**: trascinate `index.html`, `config.js` (già compilato), `firestore.rules` e `LEGGIMI.md`. Premete **Commit changes**.
3. Aprite **Settings → Pages**. In "Build and deployment" scegliete **Deploy from a branch**, branch **main**, cartella **/ (root)**, poi **Save**.
4. Dopo uno o due minuti il gioco è online a un indirizzo come
   `https://alessandrovicini.github.io/cassa-edile-dream/`

Per aggiornare il gioco basta caricare di nuovo `index.html` nello stesso repository.

## 3. In aula

1. Sul PC del formatore aprite il gioco, scheda **Regia**, e premete **Crea una nuova partita**. Compare un codice di 6 caratteri: proiettatelo, oppure mandate il link con **Copia link** (contiene già il codice).
2. Sempre in Regia impostate il costo per dipendente e le **spese della sede** di ogni Cassa (c'è anche "Carica valori di esempio").
3. Su ogni PC dei gruppi aprite il gioco, inserite il codice partita (se non avete usato il link) e scegliete il tavolo. Con 3 gruppi: tavoli **1, 3 e 5**.
4. La Regia vede le Casse dei tavoli in tempo reale; le spese della sede arrivano ai tavoli in automatico.
5. A fine giornata potete premere **Azzera i tavoli**. Per un'altra classe create una nuova partita: ogni codice ha i suoi dati.

La partita resta salvata anche chiudendo il browser. Per riprenderla, in Regia inserite il codice in "Codice esistente" e premete **Riprendi**.

## Cose da sapere

- **Costi:** il piano gratuito di Firebase (Spark) basta ampiamente per un'aula; un tavolo salva al massimo una volta ogni secondo mentre si gioca.
- **Riservatezza:** chiunque conosca il codice di una partita può leggerla e modificarla. Il gioco non contiene dati personali, solo le scelte simulate dei gruppi.
- **Pulizia:** le vecchie partite si cancellano da Firebase → Firestore Database → Dati → raccolta `partite`.
- **Se i tavoli non risultano "collegati":** controllate che `config.js` sia compilato e caricato su GitHub, e che le regole siano state pubblicate (punto 1.4). Il gioco continua comunque a funzionare in locale, con i codici.
