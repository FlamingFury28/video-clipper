# Video Clipper 1.3.1 — installazione Windows

**L'estensione 1.3.1 è in invio al catalogo AMO. Disponibilità e aggiornamento dipendono dalla revisione Mozilla. L'esportazione richiede l'helper 1.3.0 separato.**

1. Installa FFmpeg e ffprobe con libx264/AAC nel PATH, dalla [pagina ufficiale](https://ffmpeg.org/download.html#build-windows), e riapri Firefox dopo modifiche al PATH.
2. Scarica **VideoClipper-1.3.0-Windows.zip** dalla [release aggiornata](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.3.1). Estrai **tutto** in una cartella stabile sul PC.
3. Avvia **Installa helper.cmd** con lo stesso utente Windows di Firefox. Conserva eseguibile e cartella `_internal` nella posizione registrata. Se li sposti, registra nuovamente l'helper. Python e le dipendenze sono inclusi; FFmpeg/ffprobe restano separati.
4. Installa o aggiorna l'[estensione dal catalogo Mozilla](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/) quando la 1.3.1 è approvata. Questo ZIP contiene solo il companion Windows, non un XPI unsigned.
5. Apri le preferenze, usa **Verifica configurazione**, scegli la destinazione e ricarica le pagine video già aperte.

Non serve avviare come amministratore. L'helper non ha firma Authenticode separata: non disattivare le protezioni di Windows. Requisiti: Firefox 142+ e Windows 11 x64.

## Uso e sessione

Attiva Video Clipper, scegli il video con **Cambia**, imposta IN/OUT, prova **Anteprima** e salva. Invio o uscita dal campo correggono i timestamp in base all'errore: durata massima, valori negativi, unità da riportare e limiti IN/OUT. Il testo ambiguo ripristina l'ultimo valore valido; Annulla recupera le modifiche effettive.

In **Pannello e sessione** puoi autorizzare la sessione Firefox per il sito. È disattivata inizialmente: la finestra mostra i domini e richiede i permessi. Il background specifica archivio della scheda e partizione; solo il consenso viene conservato. I cookie selezionati vanno al job locale e al suo temporaneo, ripulito dopo successo, errore o annullamento. Puoi revocare il consenso nelle impostazioni.

## Aggiornamento e limiti

Aggiornare l'estensione non aggiorna automaticamente l'helper: per la 1.3.1 registra quello 1.3.0 dal nuovo ZIP. Un XPI distribuito autonomamente in precedenza deve essere sostituito dalla versione AMO quando disponibile.

MP4, HLS e DASH dipendono dall'accessibilità del media e da yt-dlp. Le prove con media sintetici e Firefox isolato non garantiscono ulteriori siti reali. DRM, dirette e shadow DOM chiuso sono esclusi. L'helper non è supportato su macOS, Linux o Android.

Per errori controlla configurazione, PATH, accesso alla sorgente e scadenza degli URL. Usa [Issues](https://github.com/FlamingFury28/video-clipper/issues) senza inviare cookie, token, URL privati o media personali. Consulta [privacy](PRIVACY.md), [novità](CHANGELOG.md) e le licenze incluse nel pacchetto; i sorgenti Python del progetto restano privati.
