# Privacy / Trattamento dei dati

Video Clipper 1.2.0 — data handling

When you activate Video Clipper in a tab, the extension reads information about that page's HTML5 video players, including media source, title, duration, playback position and geometry, to let you select and preview an interval. Activation grants access to the current tab and accessible frames; the extension does not request persistent access to all websites.

When you request an export, page/media URLs, the selected timestamps, title and export preferences are sent to the separately installed native helper on your own computer. The helper uses yt-dlp to contact the original page/video hosts and related media delivery servers, and FFmpeg/ffprobe to process media locally. Those servers receive the normal network-request information, including your IP address and applicable HTTP headers such as the source-page referrer. Video Clipper does not upload the media to an online editing service. This release does not implement a publisher-operated analytics or clip-processing service.

For its FapFolder authenticated-download integration, the helper may read existing cookies for fapfolder.club and its subdomains from the uniquely identifiable Firefox profile containing the extension. Cookie records marked as private browsing or belonging to a non-default container are excluded. The helper uses the selected cookies only for matching-domain download requests and writes a temporary per-job cookie file. Cleanup is attempted after success, failure or cancellation; cleanup failures are reported. This integration is not needed for other accessible, unauthenticated sources.

Preferences and panel geometry are stored locally in Firefox. Recent clip results include title, IN/OUT times, completion information and local output paths. History is limited to 30 results and 30 days; source URLs and cookies are not stored in that history. Clear history removes those references but does not delete saved video files. Output videos remain in the folder you choose.

The companion helper creates temporary download/conversion files on the destination volume and attempts to remove job files after completion, failure or cancellation. The extension and helper do not ask you to create a Video Clipper account. The source websites and the services used to install dependencies have their own data practices.

This statement describes version 1.2.0 and its companion helper. It does not describe data collection performed independently by Firefox, Mozilla Add-ons or the source websites.

---

Video Clipper 1.2.0 — trattamento dei dati

Quando attivi Video Clipper in una scheda, l’estensione legge le informazioni dei player HTML5 della pagina, tra cui sorgente, titolo, durata, posizione di riproduzione e geometria, per selezionare e provare un intervallo. L’attivazione concede accesso alla scheda corrente e ai frame accessibili; l’estensione non richiede accesso permanente a tutti i siti.

Quando richiedi un’esportazione, URL della pagina e del media, timestamp selezionati, titolo e preferenze vengono inviati all’helper nativo separato sul tuo computer. L’helper usa yt-dlp per contattare il sito originale e i relativi server di distribuzione dei media, e FFmpeg/ffprobe per l’elaborazione locale. Questi server ricevono i normali dati delle richieste di rete, compresi indirizzo IP e intestazioni HTTP applicabili, come il riferimento alla pagina sorgente. Video Clipper non carica i media su un servizio di montaggio online. Questa release non implementa servizi del produttore per analisi dell’utilizzo o elaborazione delle clip.

Per l’integrazione dei download autenticati FapFolder, l’helper può leggere i cookie esistenti di fapfolder.club e dei suoi sottodomini dal solo profilo Firefox individuabile univocamente che contiene l’estensione. I record dei cookie contrassegnati come navigazione anonima o appartenenti a contenitori diversi da quello predefinito vengono esclusi. L’helper usa i cookie selezionati soltanto per le richieste ai domini corrispondenti e crea un file cookie temporaneo per il singolo lavoro. La rimozione viene tentata dopo successo, errore o annullamento; gli errori di pulizia vengono segnalati. Questa integrazione non serve per altre sorgenti accessibili senza autenticazione.

Preferenze e geometria del pannello restano nell’archivio locale di Firefox. Gli esiti recenti comprendono titolo, tempi IN/OUT, informazioni sul completamento e percorsi locali. La cronologia è limitata a 30 esiti e 30 giorni; non vi vengono conservati URL sorgente o cookie. Svuotarla elimina i riferimenti, non i video salvati. I file esportati restano nella cartella scelta.

L’helper crea file temporanei di download e conversione sul volume di destinazione e ne tenta la rimozione dopo completamento, errore o annullamento. Estensione e helper non richiedono un account Video Clipper. I siti sorgente e i servizi usati per installare le dipendenze applicano le proprie pratiche sui dati.

Questa descrizione riguarda la versione 1.2.0 e il relativo helper. Non descrive le raccolte di dati svolte autonomamente da Firefox, Mozilla Add-ons o dai siti sorgente.
