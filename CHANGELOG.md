# Changes / Novità

## 1.3.1 — public AMO submission

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

The update is awaiting Mozilla signature. The latest downloadable signed release remains 1.2.0; the Windows helper 1.2.0 remains compatible.

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
