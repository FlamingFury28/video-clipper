# Video Clipper 1.4.6 — installazione e aggiornamento

La [release GitHub v1.4.6](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.4.6) contiene **estensione Firefox 1.4.6 firmata Mozilla e helper Windows 1.4.3 verificato**. Aggiorna entrambi i componenti: l'aggiornamento dell'estensione non aggiorna l'helper.

## Download e requisiti

- [VideoClipper-1.4.6-Windows.zip](https://github.com/FlamingFury28/video-clipper/releases/download/v1.4.6/VideoClipper-1.4.6-Windows.zip): pacchetto completo con helper 1.4.3, runtime, XPI firmato, istruzioni e licenze.
- [VideoClipper-1.4.6-signed.xpi](https://github.com/FlamingFury28/video-clipper/releases/download/v1.4.6/VideoClipper-1.4.6-signed.xpi): lo stesso XPI incluso nello ZIP, disponibile separatamente.
- [VideoClipper-1.4.6-SHA256SUMS.txt](https://github.com/FlamingFury28/video-clipper/releases/download/v1.4.6/VideoClipper-1.4.6-SHA256SUMS.txt): hash SHA-256 di ZIP e XPI.

Servono **Windows 11 x64, Firefox 142+ e FFmpeg/ffprobe con libx264/AAC nel PATH**. Python, yt-dlp, EJS e Deno sono inclusi; non richiedono installazioni separate. FFmpeg/ffprobe non sono inclusi: parti dalla [pagina ufficiale](https://ffmpeg.org/download.html#build-windows) e riapri Firefox dopo modifiche al PATH.

## Installazione permanente

1. Estrai **tutto** lo ZIP in una cartella stabile.
2. Avvia **Installa helper.cmd** con lo stesso utente Windows di Firefox. Non servono privilegi amministrativi. Mantieni `VideoClipperHelper.exe` e `_internal` insieme; se sposti la cartella, ripeti la registrazione dalla nuova posizione.
3. In Firefox apri `about:addons`, menu ingranaggio → **Installa componente aggiuntivo da file**, e scegli **VideoClipper-1.4.6-signed.xpi**. È un'installazione permanente con firma Mozilla.
4. Controlla versione estensione **1.4.6**. Nelle preferenze premi **Verifica configurazione**, controlla il collegamento e la versione helper **1.4.3**, poi scegli la destinazione.
5. Ricarica le pagine video aperte prima dell'aggiornamento.

L'helper non ha una firma Authenticode separata. L'XPI è firmato da Mozilla. L'helper Windows non è supportato su macOS, Linux o Android.

## Se stai aggiornando

| Situazione | Azione |
|---|---|
| Estensione e helper 1.4.1 | Installa l'XPI 1.4.6 e registra l'helper 1.4.3 dal nuovo ZIP |
| Estensione già 1.4.6, helper precedente | Estrai il nuovo ZIP e avvia il suo Installa helper.cmd; verifica helper 1.4.3 |
| Estensione 1.4.5 | Aggiorna entrambi alla coppia distribuita 1.4.6 / 1.4.3 |
| Helper assente o versione ancora vecchia | Controlla la cartella da cui esegui l'installer; quello del vecchio ZIP registra il vecchio binario |

La 1.4.5 richiede helper 1.4.2 per il protocollo v3 e rifiuta helper 1.4.1 su quel percorso. La nuova release distribuisce la coppia 1.4.6/1.4.3 verificata insieme. Non occorre ricorrere al caricamento temporaneo né disattivare i controlli di firma.

## Uso e consenso

Scegli il video, imposta IN/OUT, prova **Anteprima** e salva una clip. Per più intervalli dello stesso video usa **Aggiungi parte** e **Salva video unito**. L'ordine dell'elenco determina il risultato; il riordino è facoltativo e l'anteprima riproduce solo la parte selezionata. Controlla i timestamp dopo una correzione automatica.

**Ricerca avanzata** richiede consenso per sito: riproduci il video e scegli il candidato quando la sorgente è ambigua. **Usa la sessione Firefox per questo sito** è un consenso separato, inizialmente disattivato e revocabile. Per contenuti autenticati concedilo nel profilo/contesto dove sei autenticato. Non usare cookie di altri profili per aggirare il consenso.

L'esportazione autenticata può scaricare tutto il filmato prima del taglio: considera tempo, spazio temporaneo e traffico. Una traccia audio identificata deve essere risolvibile univocamente; altrimenti l'operazione termina con errore.

## Stato Mozilla, verifiche e limiti

La 1.4.6 è approvata come **Self / unlisted**, per distribuzione diretta. L'installazione passa dall'XPI firmato della release GitHub. La distinta submission **listed 1.4.2** risulta ancora **Awaiting Review** nel gestore Mozilla consultato il 22 ottobre 2026; la pagina avvisa che non è un'inserzione pubblica. Firma diretta e pubblicazione nel catalogo restano separate.

Il pacchetto non configura un URL personalizzato per aggiornamenti automatici. Per le prossime versioni consulta le [release GitHub](https://github.com/FlamingFury28/video-clipper/releases) e aggiorna XPI e helper compatibile.

I file pubblicati coincidono con gli hash delle ricevute. Sono già verificati installazione permanente e riavvio con firma obbligatoria, ed esportazioni con XPI firmato/helper 1.4.3 su Firefox 142.0 (3 casi) e 158.0.1 (6 casi), con media MP4/HLS/DASH locali. Le prove sintetiche non certificano ogni sito reale. DRM, dirette e shadow DOM chiuso sono esclusi; un player visibile non garantisce il download.

Per problemi controlla versione helper, configurazione, PATH, accesso alla sorgente e scadenza degli URL. Usa [Issues](https://github.com/FlamingFury28/video-clipper/issues) senza inviare cookie, token, URL privati o media personali. [Privacy](PRIVACY.md) · [Novità](CHANGELOG.md). I sorgenti Python del progetto restano privati.
