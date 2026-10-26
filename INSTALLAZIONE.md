# Video Clipper 1.11.0 — installazione e uso

La [release corrente](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.11.0) distribuisce **estensione 1.11.0 firmata Mozilla e helper 1.8.0**. Installa entrambi per ritaglio, formati e audio. Aggiornare l'estensione non aggiorna l'helper. L'interfaccia è in italiano.

## Scegli i pacchetti

| File | Contenuto |
|---|---|
| [VideoClipper-1.11.0-signed.xpi](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-1.11.0-signed.xpi) | Estensione Firefox con installazione permanente |
| [VideoClipper-Helper-1.8.0-Windows.zip](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-Helper-1.8.0-Windows.zip) | Solo helper Windows x64; scarica l'XPI separatamente |
| [VideoClipper-Helper-1.8.0-Linux-x86_64.tar.gz](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-Helper-1.8.0-Linux-x86_64.tar.gz) | Solo helper Linux desktop x86_64 |
| [VideoClipper-1.11.0-Chromium.zip](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-1.11.0-Chromium.zip) | Estensione da caricare decompressa in Chrome/Edge |
| [VideoClipper-1.11.0-SHA256SUMS.txt](https://github.com/FlamingFury28/video-clipper/releases/download/v1.11.0/VideoClipper-1.11.0-SHA256SUMS.txt) | Hash SHA-256 dei quattro pacchetti |

Servono **FFmpeg e ffprobe nel PATH con libx264/AAC**, da installare separatamente: [pagina ufficiale FFmpeg](https://ffmpeg.org/download.html). Python, yt-dlp, EJS e Deno sono inclusi nell'helper; non occorre installare Python, Node o Deno.

Verificato su Windows 11 x64 con Firefox 142.0/158.0.1 e Chrome 155/Edge 156; Linux x86_64 con Firefox desktop 158.0.1 su Ubuntu 24.04 tramite WSL. La versione minima Firefox è 142. Snap/Flatpak non verificati. Non sono disponibili pacchetti helper verificati per macOS o sistemi mobili. L'XPI è firmato Mozilla; i binari helper non hanno una firma separata.

## Firefox su Windows

1. Estrai **tutto** lo ZIP dell'helper in una cartella permanente, mantenendo insieme `VideoClipperHelper` e `_internal`. Conserva la vecchia cartella se stai aggiornando.
2. Esegui **Installa helper.cmd** dalla nuova cartella, con lo stesso utente di Firefox. Non servono privilegi amministrativi.
3. In Firefox apri `about:addons`, menu ingranaggio → **Installa componente aggiuntivo da file**, e scegli **VideoClipper-1.11.0-signed.xpi**. Non occorre il caricamento temporaneo.
4. Riapri Firefox per rinnovare il collegamento all'helper e ricarica le pagine video. Questo passaggio serve anche dopo modifiche al PATH.
5. Apri le impostazioni di Video Clipper, premi **Verifica configurazione**, controlla helper **1.8.0** e scegli la cartella di destinazione. **Verifica installazione.cmd** mostra la registrazione effettiva.

Se sposti la cartella, registra nuovamente l'helper dalla nuova posizione. **Ripristina helper.cmd** recupera la registrazione precedente dopo averla verificata; non cancella clip o impostazioni. Eseguire l'installer da un vecchio archivio registra il vecchio binario.

## Firefox su Linux

Estrai completamente il TAR.GZ in una cartella stabile. Apri un terminale in quella cartella ed esegui:

```sh
./installa-helper.sh firefox
./verifica-installazione.sh firefox
```

Usa lo stesso utente del browser, **senza sudo**. Installa l'XPI firmato da `about:addons`, riapri Firefox e verifica la configurazione. Conserva la cartella precedente: `./ripristina-helper.sh firefox` ripristina la registrazione verificata. Il pacchetto è per Firefox desktop; l'integrazione con browser isolati Snap/Flatpak non è verificata.

## Chrome ed Edge

1. Estrai **VideoClipper-1.11.0-Chromium.zip** in una cartella permanente.
2. Apri `chrome://extensions` o `edge://extensions`, attiva **Modalità sviluppatore**, premi **Carica estensione non pacchettizzata** e scegli la cartella estratta. Non è una pubblicazione negli store Chrome/Edge.
3. Registra anche l'helper per quel browser. Su Windows, dal terminale nella cartella dell'helper:

```powershell
& '.\Installa helper.cmd' chrome
# Per Edge:
& '.\Installa helper.cmd' edge
```

Su Linux gli script accettano `chrome`, `chromium` o `edge` al posto di `firefox`; le prove complete Chrome/Edge di questa release sono su Windows. Registrare solo Firefox non registra automaticamente gli altri browser. Riapri il browser e verifica la configurazione.

Per aggiornare il pacchetto Chromium conserva una cartella stabile, sostituisci i suoi file con quelli della nuova versione e premi **Ricarica** nella pagina delle estensioni. Le scorciatoie native si gestiscono anche da `chrome://extensions/shortcuts` o `edge://extensions/shortcuts`.

## Selezione e montaggio

Attiva Video Clipper nella pagina, avvia il video e controlla quello selezionato. Puoi cambiarlo manualmente. Imposta IN/OUT con i campi o i tasti; verifica il risultato dopo la correzione di un timestamp. **Anteprima** riproduce la parte scelta e ripristina la precedente riproduzione. **Aggiungi parte** crea altri intervalli dello stesso video, riordinabili anche se ripetuti o sovrapposti.

In **Impostazioni → Salvataggi → Quando selezioni più parti**, scegli **Un unico file** o **Un file per parte**. Puoi modificare la scelta anche in **Clip → Esportazione**, solo per quella clip o come valore predefinito. I file separati sono numerati, rispettano l'ordine delle parti e non sovrascrivono file esistenti. La sorgente viene acquisita una volta.

**Ritaglio:** in **Clip → Esportazione → Ritaglia sul video** disegna, sposta e ridimensiona un rettangolo sul player grande della pagina. Enter conferma, Esc annulla. Scegli Originale/libero, 9:16 telefono, 16:9, 1:1 o 4:5. Senza posizione manuale il formato ritaglia dal centro, mantenendo le proporzioni. Esci dal fullscreen nativo prima di modificarlo; la selezione sul player non supporta trasformazioni CSS di rotazione o riflessione.

**Audio:** nelle impostazioni regola il volume esportato da 0 a 200% oppure rimuovi la traccia. Scegli se mostrare i controlli e ricordare l'ultima impostazione. L'audio del sito resta quello della sua riproduzione. **Watermark** permette di caricare un'immagine locale e scegliere posizione, dimensione, opacità e margine; viene applicato dopo il ritaglio.

**Nomi:** personalizza origine del nome, nome di riserva, prefisso, suffisso e modello nelle impostazioni. Profili, associazioni ai siti, progetti e coda conservano le scelte di esportazione. La cronologia si apre in una sezione separata: apri file/cartella o copia tutti i percorsi dei risultati. Svuotarla non elimina i video dal disco.

**Tema e scorciatoie:** Firefox usa la palette del tema attivo; gli altri browser usano colori nativi e chiaro/scuro. Sono disponibili temi chiaro/scuro espliciti. Le scorciatoie dell'editor sono personalizzabili; i comandi globali sono soggetti ai vincoli del browser.

## Diagnosi, sessione e aggiornamenti

**Diagnosi e recupero** controlla player, permessi e helper. I dettagli sono copiabili e il rapporto non contiene valori dei cookie, URL sorgenti, titoli o percorsi locali. Il recupero di una sorgente scaduta è limitato e verifica che sia lo stesso filmato. Un cambio reale di video può richiedere la conferma degli intervalli.

**Ricerca avanzata** osserva temporaneamente le richieste multimediali solo dopo consenso per sito. Riproduci il video; se la sorgente è ambigua, scegli il candidato. **Usa la sessione del browser per questo sito** è un consenso distinto, inizialmente disattivato e revocabile: concedilo nel profilo dove sei autenticato. Non vengono usati cookie di altri profili per aggirare il consenso.

**Impostazioni → Aggiornamenti** controlla in un solo punto le versioni pubblicate di estensione e helper. La richiesta a GitHub è facoltativa e richiede un permesso separato. Non scarica né installa automaticamente. L'XPI non imposta un URL personalizzato di aggiornamento; il canale Mozilla listed resta separato.

La **1.11.0 è approvata per distribuzione diretta unlisted/Self**. Il catalogo Mozilla resta alla **1.4.7 approvata**, che non include le funzioni della 1.11.0. Per la versione corrente completa usa i pacchetti GitHub sopra.

## Verifiche e limiti

Superate 79 suite JavaScript, 474 test Python con 6 esclusioni per ambiente, 33 prove funzionali con XPI firmato, 9 controlli firma/riavvio, 16 prove binarie e 24 casi Chrome/Edge. Esportazioni controllate per durata, fotogrammi, pixel del ritaglio e audio in profili isolati. Queste prove non certificano tutti i siti autenticati: vedere il player non garantisce una sorgente scaricabile.

DRM, dirette e shadow DOM chiuso non sono supportati. L'esportazione può acquisire tutto il filmato prima di tagliarlo: considera traffico, tempo e spazio temporaneo. “Originale” non significa senza ricodifica. Una traccia audio scelta deve poter essere identificata senza ambiguità.

Segnala problemi riproducibili in [Issues](https://github.com/FlamingFury28/video-clipper/issues), evitando cookie, token, URL privati e media personali. [Privacy](PRIVACY.md) · [Novità](CHANGELOG.md) · [Verifiche](VERIFICATION.json). I sorgenti Python del progetto restano privati.
