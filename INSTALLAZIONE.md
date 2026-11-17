# Installa Video Clipper

[English](INSTALL.md) · [Estensione Firefox](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/) · [Download](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.13.38)

Installa l’estensione Firefox **1.13.38** dal catalogo Mozilla e l’helper **1.9.180** da questo repository. Aggiorna entrambi per il riarmo dei player hls.js/dash.js compatibili già avviati e la gestione corretta dei buffer nativi. Estensione e helper si aggiornano separatamente; il download selettivo è predefinito per le sorgenti qualificate.

L’helper 1.9.180 corregge il recupero delle sorgenti Beeg dopo il cambio API: normalizza l’identificativo della richiesta senza cambiare il video selezionato e recupera la playlist con la richiesta separata del sito. Per questa correzione basta aggiornare l’helper; l’estensione firmata 1.13.38 resta compatibile. Restano i limiti IN del player YouJizz già documentati.

Dopo l’aggiornamento, **Verifica collegamento** deve mostrare l’helper **1.9.180**. Il solo XPI non aggiorna l’helper installato.

La 1.13.38 conserva tutte le parti e le impostazioni dei tentativi falliti prima di attendere la risposta del player. Una risposta persa o lenta non elimina più il piano e le impostazioni cambiate dopo il clic non sostituiscono quelle originali. **Riprendi salvataggio** riusa la composizione originale senza reinserire i tempi, anche dopo una ricarica. **Impostazioni → Recupero → Recupera i salvataggi falliti** abilita un solo tentativo automatico per gli errori recuperabili sullo stesso video. Se il player non ha un’identità stabile, usa **Riprendi su questo video** sul progetto conservato. I lavori interrotti con esito incerto richiedono una ripresa esplicita. Non rimuovere l’estensione per aggiornarla: progetti e coda restano conservati.

La 1.13.38 corregge `SELECTIVE_UNAVAILABLE` sul player HLS XVideos selezionato. Se l’helper 1.9.180 è già collegato, aggiorna soltanto l’estensione. I progetti dei tentativi falliti conservano tutte le parti e le impostazioni originali; usa **Riprendi su questo video** se il vecchio piano non aveva un’identità stabile della sorgente.

La 1.13.38 amplia l’archivio da 40 a 200 progetti senza eliminare quelli esistenti. In **Clip → Progetto e scorciatoie**, usa **Salva copia dei tagli** per creare un JSON locale con tutte le parti ordinate, parte attiva e durata, anche quando Conserva progetto non è disponibile. **Carica tagli su questo video** ripristina esplicitamente gli intervalli dopo aver verificato video corrente e durata: il file non contiene impostazioni di uscita né identità della sorgente. Funziona anche in una finestra privata senza creare progetti persistenti. I progetti già conservati mantengono le impostazioni di esportazione. I vecchi progetti XVideos compatibili possono usare **Recupera su questo video** per riaprire l’editor senza avviare un download. Un salvataggio fallito mostra il suo esito senza conferme ingannevoli.

## Windows — percorso consigliato

1. Installa [Video Clipper dal catalogo Mozilla](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/). Al primo avvio si apre **Installazione guidata**, raggiungibile anche dalle impostazioni.
2. [Scarica il programma di installazione Windows x64](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.180/VideoClipper-Helper-1.9.180-Windows-Setup.exe), aprilo e premi **Installa**. Firefox è già selezionato; aggiungi Chrome/Edge solo se li usi.
3. Torna in **Impostazioni → Installazione guidata → Verifica collegamento**, scegli la cartella di destinazione e prova una breve clip.

Il programma prepara una cartella stabile nell’account Windows, sotto Programs/VideoClipper, e registra l’helper per i browser scelti. Non servono privilegi amministrativi, Python o configurazioni manuali del PATH. I file dell’helper precedente vengono conservati; se la registrazione non riesce, viene ripristinato il collegamento precedente.

Se FFmpeg, ffprobe e gli encoder necessari sono già disponibili e funzionanti, vengono riutilizzati. Altrimenti lascia selezionato **Prepara automaticamente gli strumenti video mancanti**: vengono scaricati circa 105 MB da gyan.dev, verificati per dimensione e SHA-256 e preparati accanto all’helper. L’archivio originale e la licenza restano nella cartella installata. Se rifiuti il download, gli strumenti con libx264/AAC devono essere già disponibili.

L’installer non ha una firma Authenticode separata. Scaricalo da questo repository e confronta le [impronte SHA-256](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.180/VideoClipper-Helper-1.9.180-SHA256SUMS.txt). Non aggira i controlli di Windows. Se l’installazione fallisce, conserva il codice esatto: un controllo tecnico dell’helper o un pacchetto incompleto richiedono una verifica diversa da un download degli strumenti non riuscito. Usa i dettagli mostrati per scegliere cosa riprovare. Conserva un’eventuale vecchia cartella funzionante finché la nuova è verificata.

Se il pannello era aperto, chiudilo e riaprilo. Riavvia Firefox solo se mantiene il vecchio collegamento all’helper. L’installer non chiude il browser e non modifica i profili personali.

## Lingua

In **Impostazioni → Generali → Lingua**, scegli **Automatico**, **Italiano** o **English**. Automatico segue la lingua del browser: italiano per le lingue italiane, inglese negli altri casi. Il cambio è immediato e viene conservato. Titoli dei video, nomi personalizzati, percorsi e testo del sito restano intatti.

## Linux x86_64

[Scarica l’archivio dell’helper](https://github.com/FlamingFury28/video-clipper/releases/download/helper-v1.9.180/VideoClipper-Helper-1.9.180-Linux-x86_64.tar.gz), estrailo interamente in una cartella permanente ed esegui `./installa-helper.sh firefox` come utente del browser, senza sudo. FFmpeg e ffprobe con libx264/AAC devono essere disponibili tramite il sistema. Riapri Firefox ed esegui **Verifica collegamento**.

Se sposti la cartella, registra di nuovo l’helper. Conserva insieme tutti i file estratti. Il collegamento con browser Snap/Flatpak non è verificato.

## Chrome ed Edge

Estrai lo [ZIP Chromium](https://github.com/FlamingFury28/video-clipper/releases/download/v1.13.13/VideoClipper-1.13.13-Chromium.zip) in una cartella stabile. Da `chrome://extensions` o `edge://extensions`, attiva la modalità sviluppatore e carica la cartella come estensione non pacchettizzata.

Nel programma di installazione Windows seleziona anche il browser scelto. La registrazione per Firefox da sola non basta. In alternativa, l’helper portatile accetta `VideoClipperHelper.exe --install --browser chrome` oppure `--browser edge`. Questa build Chromium separata è precedente alla release Firefox: il nuovo recupero MediaSource di Firefox non è dichiarato per questo ZIP. Non è dichiarata la pubblicazione negli store Chrome/Edge.

Per macOS, Android e iOS non è ancora disponibile un pacchetto helper verificato.

## Uso e problemi

Seleziona il player giusto, imposta IN/OUT, guarda l’anteprima e salva. In **Clip → Esportazione** puoi scegliere file unito/separati, formato, ritaglio e audio. Le regole per il nome e la lingua sono nelle impostazioni.

**Verifica collegamento** controlla helper, strumenti e cartella. **Diagnostica** verifica player e permessi e salva un rapporto senza valori dei cookie, URL delle sorgenti, titoli o percorsi locali. Se un sito richiede l’accesso, concedi la sessione facoltativa solo nel contesto del browser dove sei autenticato. La ricerca avanzata richiede un consenso separato.

Non eliminare la cartella registrata dell’helper prima di aver verificato la sostituzione. Il pacchetto portatile comprende comandi di verifica installazione e ripristino. Svuotare la cronologia elimina i riferimenti, non le clip. Leggi [Privacy](PRIVACY.md) e i limiti di compatibilità nel [README](README.md).
