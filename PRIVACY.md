# Privacy / Trattamento dei dati

Video Clipper 1.3.1 and Windows helper 1.3.0 — data handling

When you activate the extension, it reads the selected tab's accessible HTML5 players: source URLs, title, duration, current time and geometry. It uses activeTab access and, only when you request it, optional host access for displayed embedded-player domains. It does not request persistent access to every website by default.

When you save a clip, the selected page/frame/media URLs, title, timestamps and export preferences are sent to the separately installed native helper on your own computer. yt-dlp contacts the source page, video hosts and related media-delivery servers; FFmpeg/ffprobe processes media locally. Those hosts receive normal request information including your IP address and applicable headers such as the referrer. Video Clipper does not upload video to a publisher-operated editing service and has no analytics or telemetry service.

Use Firefox session for this site is optional and off by default. Its separate consent window identifies the authorized site/media domains and requests cookies plus the relevant host permissions. The background reads only cookies applicable to authorized URLs, explicitly limiting the query to this tab's cookie store and to unpartitioned cookies or the top-level site's partition. Cookies from other stores, unrelated partitions or nonempty legacy firstPartyDomain isolation are not used. The scope can be revoked in extension settings; removing browser permissions also invalidates the related consent. Revocation prevents future jobs and collection still in progress; it does not retroactively remove a session already passed to a running job.

Only the consent/domain list is saved in extension preferences. Cookie values are sent only to the local export job, written to its temporary yt-dlp cookie jar and used for matching-domain media requests. They are not stored in clip history, UI views or diagnostic records. Cleanup is attempted after success, failure and cancellation; a cleanup failure is reported. The 1.3.x extension's new protocol does not read Firefox profile files. For compatibility, the helper's legacy protocol used by older extensions retains the previously documented limited X/FapFolder profile-cookie behavior.

Destination, quality, layout and panel geometry stay in local Firefox storage. Clip history stores up to 30 recent results for up to 30 days, including title, interval, completion status and local output path. Source URLs and cookies are not stored in history. Clearing history removes references, not saved videos. Exported files remain in your chosen folder. Temporary media is created on the destination volume and cleaned after the job, with cleanup failures reported.

No Video Clipper account is required. Firefox, Mozilla Add-ons, GitHub, dependency distributors and source websites apply their own privacy practices. This policy describes the extension and local helper, not those independent services.

---

Video Clipper 1.3.1 e helper Windows 1.3.0 — trattamento dei dati

Quando attivi l'estensione, legge i player HTML5 accessibili della scheda scelta: URL sorgenti, titolo, durata, posizione corrente e geometria. Usa activeTab e, solo su tua richiesta, l'accesso facoltativo ai domini mostrati dei player incorporati. Non richiede inizialmente accesso permanente a tutti i siti.

Quando salvi una clip, URL selezionati di pagina/frame/media, titolo, timestamp e preferenze vengono inviati all'helper nativo separato sul tuo computer. yt-dlp contatta pagina e server sorgenti e i relativi CDN; FFmpeg/ffprobe elabora i media localmente. I server ricevono i normali dati di rete, compresi indirizzo IP e intestazioni applicabili come il Referer. Video Clipper non carica video su un servizio di montaggio del produttore e non implementa analisi dell'utilizzo o telemetria.

Usa la sessione Firefox per questo sito è facoltativo e disattivato inizialmente. La finestra di consenso separata mostra i domini autorizzati di sito e media e richiede i cookie e i relativi permessi host. Il background legge solo i cookie applicabili agli URL autorizzati, specificando archivio della scheda e cookie non partizionati o partizione del sito principale. Non usa altri archivi, partizioni estranee o cookie dell'isolamento legacy con firstPartyDomain non vuoto. Puoi revocare il consenso nelle impostazioni; la rimozione dei permessi Firefox invalida il consenso associato. La revoca blocca i lavori successivi e la raccolta ancora in corso; non ritira retroattivamente la sessione già passata a un job avviato.

Nelle preferenze resta solo il consenso con i domini. I valori dei cookie vengono inviati al job locale, scritti nel suo file temporaneo per yt-dlp e usati per richieste ai domini corrispondenti. Non vengono conservati nella cronologia, nelle viste dell'interfaccia o nei dati diagnostici. La pulizia è tentata dopo successo, errore o annullamento e gli errori di pulizia vengono segnalati. Il nuovo protocollo dell'estensione 1.3.x non legge i file dei profili Firefox. Per compatibilità, il protocollo legacy usato dalle vecchie estensioni mantiene il precedente comportamento limitato ai cookie X/FapFolder già documentato.

Destinazione, qualità, posizione e geometria restano nell'archivio locale Firefox. La cronologia conserva al massimo 30 esiti per 30 giorni: titolo, intervallo, stato e percorso locale. Non conserva URL sorgenti o cookie. Svuotarla elimina i riferimenti, non i video salvati. I file esportati restano nella cartella scelta. I temporanei dei media vengono creati sul volume della destinazione e ripuliti al termine del job; gli errori di pulizia vengono segnalati.

Non serve un account Video Clipper. Firefox, Mozilla Add-ons, GitHub, distributori delle dipendenze e siti sorgente applicano le proprie pratiche sulla privacy. Questa informativa descrive estensione e helper locale, non quei servizi indipendenti.
