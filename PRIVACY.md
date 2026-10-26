# Privacy / Trattamento dei dati

Applies to Video Clipper catalog 1.11.1 / direct 1.11.0 and local helper 1.8.0. Updated 26 October 2026.

## English

When activated, Video Clipper reads the chosen tab's accessible HTML5 players: source addresses, title, duration, playback position and geometry. It uses active-tab access; optional access to embedded-player domains is requested through your actions. Persistent access to all websites is not granted by default.

Saving sends the selected page/frame/media addresses, title, intervals, output settings and destination to the native helper **on your own computer**. yt-dlp contacts source websites and media/CDN servers; FFmpeg/ffprobe processes media locally. Those servers receive normal network information such as your IP address and applicable request headers. The full source may be downloaded before trimming. Video Clipper has no publisher-operated video upload, cloud editing or analytics service and requires no Video Clipper account.

Browser-session access is optional, initially disabled, site-scoped and revocable in settings. Only cookies applicable to authorized addresses and the selected tab's cookie store, partition and first-party context may be sent to the local job. Another browser profile is not read. Advanced discovery has separate consent: it temporarily observes relevant requests in the selected tab/frames and keeps candidates in memory for selection. It does not collect arbitrary authorization headers or other tabs' browsing history. Revocation prevents future collection; it cannot retract session data already handed to a running local job.

Cookie values/session tokens are not stored in preferences, history or diagnostic reports. The helper may use a temporary cookie jar, scoped to authorized requests and redirects. Temporary data is cleaned after completion, error or cancellation; cleanup failures are reported. Exported videos remain in your chosen destination. This policy concerns the current extension/helper pair, not older releases' legacy protocols.

Local extension storage holds preferences, consented domains, output profiles/site associations, watermark images, projects and recent-result history. Projects retain clip names, hashed source/page identifiers, intervals and output settings so they can resume when the same video is available. History contains result names, intervals, status and local output paths, with configurable retention; clearing it removes references, not exported files. Private-window projects and jobs are not added to persistent projects/history. An exported file is still written to disk when you save from a private window.

Watermark images are converted locally to bounded PNG data, kept in local extension storage and sent only to the local export job that uses them. Diagnostic exports omit the image. Removing the current image does not remove copies retained in an existing project/profile or a settings backup you previously exported. Settings backups are user-requested JSON files and may include local paths, names, site associations and images; review them before sharing.

Diagnostic reports omit cookie values, source addresses, titles and local paths. They can contain versions, platform/browser information, configuration flags, anonymized event/error codes, durations and permission/check results. Reports remain local unless you choose to share them. Copying file paths or exporting a settings backup is a separate explicit action.

**Settings → Updates** makes an optional, user-requested HTTPS call to the GitHub releases API after host permission is granted. It sends no cookie/session credentials, video addresses, titles or local paths; GitHub receives ordinary connection information such as your IP address. It compares published versions with the installed extension/helper and offers links. It neither downloads nor installs updates automatically. Visiting GitHub/Mozilla download pages is subject to those services' privacy practices.

Firefox's theme palette, or native browser light/dark colors, is used locally. Browser vendors, Mozilla Add-ons, GitHub, dependency distributors and source websites operate independently under their own policies. The extension is not a browser-wide privacy or anonymity tool.

## Italiano

Questa informativa riguarda Video Clipper catalogo 1.11.1 / diretta 1.11.0 e helper locale 1.8.0, aggiornata il 26 ottobre 2026.

Quando lo attivi, Video Clipper legge i player HTML5 accessibili della scheda scelta: indirizzi delle sorgenti, titolo, durata, posizione di riproduzione e geometria. Usa l'accesso alla scheda attiva; gli eventuali permessi per domini dei player incorporati vengono richiesti tramite tue azioni. Non ottiene inizialmente accesso permanente a tutti i siti.

Il salvataggio invia indirizzi selezionati di pagina/frame/media, titolo, intervalli, impostazioni e destinazione all'helper nativo **sul tuo computer**. yt-dlp contatta siti e server/CDN sorgenti; FFmpeg/ffprobe elabora i media localmente. Questi server ricevono normali informazioni di rete, come IP e intestazioni applicabili. Prima del taglio può essere scaricato l'intero filmato. Video Clipper non gestisce servizi di caricamento video, montaggio cloud o analisi d'uso e non richiede un account Video Clipper.

L'accesso alla sessione del browser è facoltativo, inizialmente disattivato, limitato al sito e revocabile nelle impostazioni. Solo i cookie applicabili agli indirizzi autorizzati e al contesto della scheda — archivio, partizione e dominio di prima parte — possono essere inviati al lavoro locale. Non vengono letti altri profili. La ricerca avanzata richiede un consenso distinto: osserva temporaneamente richieste pertinenti nella scheda/frame e mantiene i candidati in memoria per la scelta. Non raccoglie intestazioni di autorizzazione arbitrarie né cronologia di altre schede. La revoca blocca la raccolta futura; non ritira dati di sessione già consegnati a un lavoro locale avviato.

Valori dei cookie e token non vengono conservati nelle preferenze, nella cronologia o nei rapporti diagnostici. L'helper può usare un file cookie temporaneo, limitato a richieste e reindirizzamenti autorizzati. I dati temporanei vengono ripuliti dopo completamento, errore o annullamento; eventuali errori di pulizia sono segnalati. I video esportati restano nella destinazione scelta. Questa informativa riguarda la coppia corrente, non i protocolli legacy delle vecchie versioni.

L'archivio locale dell'estensione conserva preferenze, domini autorizzati, profili di esportazione/associazioni ai siti, immagini watermark, progetti e cronologia dei risultati. I progetti contengono nome, identificatori hash di pagina/sorgente, intervalli e impostazioni per riprendere lo stesso video quando disponibile. La cronologia conserva nomi dei risultati, intervalli, stato e percorsi locali, con durata configurabile. Svuotarla elimina i riferimenti, non i file. Progetti e salvataggi delle finestre private non vengono aggiunti agli archivi persistenti; un video esportato da una finestra privata viene comunque scritto sul disco.

Le immagini watermark sono convertite localmente in PNG di dimensioni limitate, conservate nell'archivio locale e inviate solo al lavoro di esportazione che le usa. I rapporti diagnostici le escludono. Rimuovere l'immagine corrente non rimuove copie già conservate in progetti/profili o backup delle impostazioni esportati in precedenza. I backup JSON sono creati su richiesta e possono includere percorsi locali, nomi, associazioni ai siti e immagini: controllali prima di condividerli.

La diagnosi esclude valori dei cookie, indirizzi sorgenti, titoli e percorsi locali. Può includere versioni, sistema/browser, opzioni, codici evento/errore anonimizzati, durate ed esiti dei controlli e dei permessi. I rapporti restano locali finché non scegli di condividerli. Copiare percorsi o esportare un backup è un'azione esplicita distinta.

**Impostazioni → Aggiornamenti** esegue, su tua richiesta e dopo il permesso host, una chiamata HTTPS all'API delle release GitHub. Non invia credenziali cookie/sessione, indirizzi video, titoli o percorsi locali; GitHub riceve le normali informazioni della connessione, come l'IP. Confronta le versioni pubblicate con estensione/helper installati e propone i collegamenti. Non scarica né installa automaticamente. Le pagine di download GitHub/Mozilla applicano le rispettive informative.

La palette del tema Firefox o i colori nativi chiaro/scuro vengono utilizzati localmente. Browser, Mozilla Add-ons, GitHub, distributori delle dipendenze e siti sorgenti sono servizi indipendenti con proprie politiche. L'estensione non è uno strumento di anonimato o protezione generale della navigazione.
