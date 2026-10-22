# Changes / Novità

## 1.4.7 — catalog submission; manifest version only

- Inviata al solo catalogo Mozilla (listed); stato verificato **Awaiting Review**, validazione con **0 errori e 0 avvisi**. [Submission AMO](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/6610420), accessibile all'autore.
- Cambia esclusivamente `manifest.version` da 1.4.6 a 1.4.7. I dieci file funzionali coincidono byte per byte con la 1.4.6; nessuna modifica a funzionalità, permessi o helper.
- L'helper resta **1.4.3**, nella [release GitHub 1.4.6](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.4.6). Le prove della coppia 1.4.6/1.4.3 sono riutilizzate dopo il confronto dei payload.
- La **1.4.6 unlisted resta Self / Approved**, con distribuzione diretta GitHub attiva. Non è stata creata una nuova release GitHub né sostituito l'XPI firmato.
- Il numero 1.4.7 è stato autorizzato per il catalogo dopo il rifiuto AMO del numero 1.4.6 già esistente. L'invio non attesta la pubblicazione o l'approvazione del catalogo.

## 1.4.6 — published signed extension + verified helper 1.4.3

La [release GitHub v1.4.6](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.4.6) distribuisce l'estensione firmata Mozilla **1.4.6**, l'helper Windows **1.4.3**, il pacchetto completo e gli hash SHA-256. Le istruzioni di installazione correnti sono in [INSTALLAZIONE](INSTALLAZIONE.md). La firma è per distribuzione diretta unlisted; il catalogo listed rimane un flusso separato.

- Migliora il riconoscimento Vidstack e i cambi di stato del player, compresi pubblicità, dirette e contenuti cifrati.
- Migliora trasporto HLS/DASH, mantenimento della traccia audio identificata, gestione degli header e degli errori transitori.
- Verifica la copertura temporale della traccia video MP4 prima di pubblicare il risultato; migliora le anteprime e i montaggi quando l'audio termina prima del video.
- Conserva taglio singolo e unione ordinata di più intervalli dello stesso video, con riordino facoltativo e anteprima della sola parte selezionata.
- Verificati gli hash di tutti i file del pacchetto, XPI firmato e helper. Riutilizzate le prove già registrate di installazione permanente/riavvio, esportazioni con XPI firmato su Firefox 142.0 (3 casi) e 158.0.1 (6 casi), 4 controlli nativi e 34 test v3/refresh del binario. Ricontrollata la risposta nativa del binario 1.4.3 estratto dallo ZIP.
- Aggiornare entrambi i componenti. Python, yt-dlp, EJS e Deno sono inclusi; FFmpeg/ffprobe con libx264/AAC restano separati.
- Le prove locali non attestano ogni sito reale. DRM, dirette e shadow DOM chiuso restano esclusi.

## Cronologia delle verifiche prima della pubblicazione GitHub 1.4.6

Le indicazioni seguenti su asset mancanti e descrizione Mozilla obsoleta descrivono le verifiche precedenti a questa pubblicazione. Per download e installazione valgono i collegamenti correnti sopra.

Stato verificato il 22 ottobre 2026. Le voci storiche descrivono il loro contesto; per installare valgono [README](README.md) e [INSTALLAZIONE](INSTALLAZIONE.md).

## Verifica aggiuntiva degli artefatti — 2026-10-22

- Conservati gli stati AMO e i requisiti helper documentati nella [verifica precedente](https://github.com/FlamingFury28/video-clipper/commit/fcd7230891952809081efd801569a2da1e2e1a38). La successiva lettura pubblica del link XPI 1.4.5 ha restituito HTTP 404; il codice di tale versione e le pagine AMO autenticate non sono stati riesaminati in questa verifica aggiuntiva.
- Scaricati direttamente ZIP Windows e XPI GitHub 1.4.1: hash conformi ai checksum pubblicati, hash dell'eseguibile helper conforme a `PRODUCT.json` incluso, XPI nello ZIP identico all'asset separato.
- Verificati nel manifest GitHub 1.4.1 versione, ID estensione e Firefox minimo 142.0; nelle preferenze il pulsante è **Verifica configurazione**. Corretta l'etichetta nelle istruzioni.
- Il codice 1.4.1 controlla `multi-part-export-v1` per l'unione; alcuni altri messaggi di aggiornamento citano ancora helper 1.4.0. La distribuzione documentata resta la coppia 1.4.1/1.4.1.
- Nessuna nuova prova completa di esportazione in Firefox. L'assenza di un download pubblico della 1.4.5 in questa lettura non dimostra un ritiro da Mozilla.

## 1.4.6 — Mozilla direct distribution approved; helper 1.4.3 required

- Il [gestore AMO](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/) mostra **Self / Approved**; è la versione diretta approvata più recente osservata.
- Le [note AMO](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/6609239) richiedono helper **1.4.3**.
- Nessuna release GitHub 1.4.6 o asset helper 1.4.3 è stato trovato nella verifica. L'approvazione non prova la pubblicazione nel catalogo né la disponibilità del pacchetto Windows su GitHub.

## 1.4.5 — Mozilla direct distribution approved; helper 1.4.2 required

- Approvazione automatica comunicata il 22 ottobre 2026 alle 18:21 circa, ora italiana. AMO registra la versione come **Self / Approved**, non come versione pubblicata nel catalogo.
- Le [note AMO](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/6609010) documentano identità del contenuto selezionato, ulteriori adattatori dei player, ricerca facoltativa delle sorgenti, contesti di sessione Firefox isolati e verifica della sorgente. Queste indicazioni non certificano tutti i siti.
- Le note richiedono helper **1.4.2**. Nel relativo [XPI approvato](https://addons.mozilla.org/firefox/downloads/file/5153129/video_clipper_in_out_mp4-1.4.5.xpi) il controllo del percorso v3 rifiuta helper 1.4.1 con `HELPER_UPDATE_REQUIRED`.
- L'helper binario della release GitHub 1.4.1 dichiara capacità v3 ma fallisce tale controllo. Il confronto di artefatti e capacità non è una nuova prova completa di esportazione in Firefox con la coppia mista. Nessun helper 1.4.2 è stato trovato nelle release GitHub.
- I percorsi pubblici legacy presenti nel codice non consentono di dichiarare la coppia estensione 1.4.5 / helper 1.4.1 pienamente compatibile.

## 1.4.2 — catalog submission awaiting review

- Il [gestore AMO](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/) mostra **AMO / Awaiting Review**, con validazione senza errori né avvisi. La revisione non risulta conclusa.
- La pagina del prodotto, vista dall'account dell'autore, avvisa che l'inserzione non è pubblica. Non interpretare l'email della 1.4.5 come approvazione della 1.4.2 listed.

## 1.4.1 — multiple intervals in one MP4; published GitHub distribution

- [Release pubblicata il 22 ottobre 2026](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.4.1), con **VideoClipper-1.4.1-signed.xpi**, **VideoClipper-1.4.1-Windows.zip** e **VideoClipper-1.4.1-SHA256SUMS.txt**.
- Unione di più intervalli dello stesso video in un MP4 nell'ordine dell'elenco, anche sovrapposti o ripetuti; riordino facoltativo, annullamento e cronologia della composizione.
- Anteprima della sola parte selezionata e salvataggio singolo conservati.
- La distribuzione richiede entrambi i componenti **estensione 1.4.1 / helper 1.4.1**. Python, yt-dlp, EJS e Deno sono inclusi; FFmpeg/ffprobe con libx264/AAC restano nel PATH.
- La release documenta installazione permanente e riavvio con firma Firefox attiva, esportazione singola e unione con il binario, ordine video/audio, durata e riproduzione fino alla fine. Prove su media sintetici locali, non certificazione di ulteriori siti.

I dettagli delle versioni intermedie non sono ricostruiti per supposizione.

## 1.3.1 — historical public AMO submission

Video Clipper 1.3.1

- Saves from the selected player's media sources first, avoiding another video from a page with several players. Page extraction is used only when the video can be identified unambiguously.
- Adds Video.js public-API source discovery alongside JW Player and X/Twitter support; improves linked players, dynamically loaded/nested frames, about:blank and srcdoc documents.
- Keeps Search for other videos available while a player is selected, preserving the selected range during the search.
- Adds optional Firefox session use per site. It is off by default, asks for the displayed domains and cookie permission, uses the tab's cookie store and the top-level site's partition, and can be revoked in settings. Only consent is saved; the scoped cookies are sent to the local export job and its temporary cookie file is cleaned up after success, failure or cancellation.
- Introduces a compact editor with readable timestamps, reachable preview/save/cancel actions, collapsible settings/history and visible completed-file actions.
- Automatically repairs timestamps on Enter or leaving the field: clamps to the video duration and IN/OUT bounds, carries excess seconds/minutes, rounds milliseconds and restores the last valid value for ambiguous text. Corrections are explained and range changes can be undone.

IMPORTANT: MP4 export now requires Windows helper 1.3.0 or later and FFmpeg/ffprobe with libx264/AAC. Updating the extension does not update the helper. Updated helper and instructions: https://github.com/FlamingFury28/video-clipper/releases/tag/v1.3.1

Firefox 142+; interface in Italian. Compatibility was checked with synthetic MP4/HLS/DASH media and the actual extension in isolated Firefox. Additional live sites remain unverified. DRM, live streams and closed shadow roots are unsupported.

---

Video Clipper 1.3.1

- Il salvataggio prova prima le sorgenti del player selezionato, evitando di scegliere un altro filmato nelle pagine con più video. L'estrazione della pagina è usata solo quando identifica il video senza ambiguità.
- Aggiunge il recupero delle sorgenti tramite le API pubbliche di Video.js, accanto a JW Player e X/Twitter; migliora i video dentro link, i frame dinamici e annidati e i documenti about:blank/srcdoc.
- Cerca altri video resta disponibile con un player selezionato e conserva l'intervallo durante la ricerca.
- Aggiunge la sessione Firefox facoltativa per sito, disattivata inizialmente. Richiede il consenso ai domini mostrati e ai cookie, specifica archivio della scheda e partizione del sito principale ed è revocabile nelle impostazioni. Nelle preferenze resta solo il consenso: i cookie selezionati vanno al job locale e al suo file temporaneo, ripulito dopo successo, errore o annullamento.
- Ridisegna il pannello come editor compatto: timestamp leggibili, anteprima/salvataggio/annullamento raggiungibili, impostazioni e cronologia richiudibili e azioni del file salvato direttamente disponibili.
- Corregge automaticamente i timestamp con Invio o all'uscita dal campo: limita durata e confini IN/OUT, riporta secondi/minuti in eccesso, arrotonda i millisecondi e ripristina l'ultimo valore valido quando il testo è ambiguo. Spiega la correzione e permette di annullare le modifiche all'intervallo.

IMPORTANTE: per esportare MP4 serve ora l'helper Windows 1.3.0 o successivo, oltre a FFmpeg/ffprobe con libx264/AAC. Aggiornare l'estensione non aggiorna l'helper. Helper aggiornato e istruzioni: https://github.com/FlamingFury28/video-clipper/releases/tag/v1.3.1

Firefox 142+; interfaccia in italiano. Verificati media sintetici MP4/HLS/DASH e l'estensione reale in Firefox isolato. Gli ulteriori siti reali restano da verificare. DRM, dirette e shadow DOM chiuso non sono supportati.

## Historical release notes


## 1.2.2 — signature pending

- Shows visible cross-origin embedded domains when no video is accessible.
- Adds a direct user-click request for one chosen player host, followed by another detection attempt.
- Handles denial/retry and rejects stale work after tab, activation or player changes.
- Keeps existing required permissions; host grants are optional and remain revocable in Firefox.
- Validated with 250 Python tests (248 passed, 2 Windows privilege skips), 31 JavaScript suites and a synthetic JW-style iframe fixture on two origins. The live video of a particular website has not been exported by these tests.

Historical status recorded for 1.2.2: signature was pending and 1.2.0 was then the latest downloadable signed release. These statements do not describe current availability or compatibility with later extensions.

Video Clipper 1.2.0

- Detects HTML5 videos inside open shadow DOM components, including nested components and roots created after activation.
- Fixes preview completion when OUT is the end of a looping video; restores the previous playback position and state.
- Makes player selection, command feedback and activation more reliable when videos, frames or tabs change during pending operations.
- Improves movable/resizable dock gestures, fullscreen transitions and iframe alignment for borders, padding and internal navigation.
- Preserves preference drafts, confirms successful writes and supports retries after failures. Improves local history, clipboard feedback and keyboard focus.
- Improves local export validation, Windows filenames, resolution limits, cancellation, progress reporting and temporary-file handling.

The Windows distribution now includes a compiled helper with Python and dependencies. FFmpeg/ffprobe remain a separate requirement.

---

Video Clipper 1.2.0

- Rileva video HTML5 nei componenti con shadow DOM aperto, anche annidati o creati dopo l’attivazione.
- Corregge la fine dell’anteprima quando OUT coincide con la fine di un video in ripetizione; ripristina posizione e stato precedenti.
- Migliora selezione del player, esiti dei comandi e attivazione quando video, frame o scheda cambiano durante operazioni in attesa.
- Migliora trascinamento e ridimensionamento del pannello, passaggi a schermo intero e allineamento degli iframe con bordi, padding o navigazione interna.
- Conserva le bozze delle preferenze, conferma la scrittura riuscita e permette di riprovare dopo un errore. Migliora cronologia locale, copia dei percorsi e focus da tastiera.
- Migliora verifica dell’esportazione locale, nomi Windows, limiti di risoluzione, annullamento, avanzamento e gestione dei temporanei.

La distribuzione Windows include ora un helper eseguibile con Python e dipendenze. FFmpeg/ffprobe restano necessari separatamente.
