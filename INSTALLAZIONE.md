# Video Clipper — installazione Windows

Verifica del 22 ottobre 2026: la [release GitHub v1.4.1](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.4.1) distribuisce **estensione firmata 1.4.1 e helper 1.4.1**. È la coppia pubblicata cui si riferiscono i passaggi seguenti. L'aggiornamento dell'estensione non aggiorna automaticamente l'helper.

1. Installa FFmpeg e ffprobe con libx264/AAC nel PATH, dalla [pagina ufficiale](https://ffmpeg.org/download.html#build-windows), e riapri Firefox dopo modifiche al PATH.
2. Scarica **VideoClipper-1.4.1-Windows.zip** dalla release indicata. Estrai **tutto** in una cartella stabile sul PC.
3. Avvia **Installa helper.cmd** con lo stesso utente Windows di Firefox. Conserva eseguibile e cartella `_internal` nella posizione registrata. Se li sposti, registra nuovamente l'helper. Python, yt-dlp, EJS e Deno sono inclusi; FFmpeg/ffprobe restano separati.
4. In Firefox apri `about:addons`, menu ingranaggio → **Installa componente aggiuntivo da file**, e scegli **VideoClipper-1.4.1-signed.xpi**, incluso nel pacchetto e disponibile anche come asset separato. È un'installazione permanente con XPI firmato da Mozilla. Controlla che la versione installata sia 1.4.1.
5. Apri le preferenze, usa **Verifica collegamento**, scegli la destinazione e ricarica le pagine video già aperte.

Non serve avviare come amministratore. L'helper non ha firma Authenticode separata. Requisiti della distribuzione: Firefox 142+, Windows 11 x64 e FFmpeg/ffprobe. Gli hash dei download sono in **VideoClipper-1.4.1-SHA256SUMS.txt** nella stessa release.

## Se hai già l'estensione 1.4.5 o 1.4.6

| Estensione | Requisito verificato | Disponibilità dell'helper su GitHub |
|---|---|---|
| 1.4.1 | Helper 1.4.1 della stessa release | Pubblicato nella v1.4.1 |
| 1.4.5 | Le note AMO richiedono helper 1.4.2; il codice rifiuta 1.4.1 per il protocollo v3 | Nessun asset 1.4.2 trovato nella verifica |
| 1.4.6 | Le note AMO richiedono helper 1.4.3 | Nessun asset 1.4.3 trovato nella verifica |

Per la 1.4.5 il requisito è confermato dalle [note AMO](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/6609010), dalla ricevuta locale di firma e dal codice dell'[XPI Mozilla approvato](https://addons.mozilla.org/firefox/downloads/file/5153129/video_clipper_in_out_mp4-1.4.5.xpi). Il binario estratto dallo ZIP GitHub 1.4.1 dichiara capacità v3 ma non supera il controllo di versione della 1.4.5: il percorso v3 produce `HELPER_UPDATE_REQUIRED`. Alcuni percorsi pubblici legacy restano nel codice; non costituiscono una garanzia di compatibilità della coppia mista.

Le [note AMO 1.4.6](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/6609239) richiedono l'helper 1.4.3. Non installare un XPI più recente da solo aspettandoti che aggiorni il companion. Se hai già una di queste versioni, procurati il pacchetto completo con l'helper richiesto e registra quello; rieseguire **Installa helper.cmd** sullo ZIP 1.4.1 non aggiorna il binario. L'eventuale disponibilità di un nuovo pacchetto completo va controllata nelle [release](https://github.com/FlamingFury28/video-clipper/releases). Non viene prescritto un downgrade dell'estensione.

## Stato Mozilla e istruzioni precedenti

Il [gestore versioni AMO](https://addons.mozilla.org/en-US/developers/addon/video-clipper-in-out-mp4/versions/), consultato con l'account dell'autore, mostra **1.4.5 e 1.4.6: Self / Approved** (distribuzione diretta, unlisted) e **1.4.2: AMO / Awaiting Review** (catalogo, listed). La pagina del prodotto avvisa che non è un'inserzione pubblica e viene mostrata per i privilegi dell'account. La visibilità configurata su **Visible** non equivale alla conclusione della revisione.

L'email di approvazione automatica della 1.4.5 del 22 ottobre alle 18:21, ora italiana, non prova la pubblicazione nel catalogo. Firma diretta, pubblicazione listed e aggiornamenti automatici sono aspetti distinti. Non occorre attendere il catalogo per installare l'XPI già firmato della release GitHub 1.4.1.

La descrizione AMO contiene ancora estensione 1.3.1, helper 1.3.0 e il collegamento alla v1.3.1: sono riferimenti precedenti e non soddisfano i requisiti della 1.4.5/1.4.6. Le modifiche a questi quattro documenti non aggiornano la scheda AMO né cambiano i canali di pubblicazione.

## Uso, sessione e limiti

Attiva Video Clipper, scegli il video, imposta IN/OUT, prova **Anteprima** e salva una clip. Per più intervalli dello stesso video usa **Aggiungi parte** e **Salva video unito**; l'ordine dell'elenco determina il risultato e il riordino è facoltativo. L'anteprima riproduce solo la parte selezionata.

**Usa la sessione Firefox per questo sito** è facoltativo e disattivato inizialmente. Per video autenticati concedilo nel profilo in cui sei autenticato, per i domini mostrati. L'estensione usa il contesto della scheda e della partizione; il consenso è revocabile nelle impostazioni. Non usare cookie di un altro profilo per aggirare il consenso.

MP4, HLS e DASH dipendono dall'accessibilità del media. Le prove su media sintetici e Firefox isolato non garantiscono il funzionamento su ulteriori siti reali. DRM, dirette e shadow DOM chiuso sono esclusi. L'helper non è supportato su macOS, Linux o Android.

Per errori controlla versione dell'helper, collegamento, PATH, accesso alla sorgente e scadenza degli URL. Usa [Issues](https://github.com/FlamingFury28/video-clipper/issues) senza inviare cookie, token, URL privati o media personali. Consulta [privacy](PRIVACY.md), [novità](CHANGELOG.md) e le licenze incluse nel pacchetto; i sorgenti Python del progetto restano privati.
