# Changes / Novità

## 1.12.9 / helper 1.8.2 — protect existing output files, 26 October 2026

- Helper 1.8.2 fixes a race where another application's file replacing the output reservation could be overwritten, or deleted after a failed final move. A verified file now commits atomically without replacing an occupied name.
- Keeps collision suffixes, separate-part ordering/rollback and cancellation after successful publication. The fault was reproduced in helper 1.8.1 source on a real temporary Windows filesystem before the fix.
- Real Windows/Linux binaries pass concurrent exports, foreign-file and empty-reservation preservation, Unicode titles and separate parts. The full Windows Python run passes 489 tests with six environment skips; eight targeted publication cases pass on each OS.
- Extension 1.12.9 changes only the two Guided setup download URLs and manifest version. No new permissions, source/player changes or session access. The already signed 1.12.8 also works with the new helper.
- The exact 1.12.9 XPI and helper pass MP4/HLS exports after permanent restart on Windows Firefox 142/158 and Ubuntu Firefox 158. Installer payload verification and isolated setup with verified portable tools pass. Upstream dependencies/notices are unchanged.
- Italiano: il nuovo helper evita sovrascritture o eliminazioni di file estranei durante la pubblicazione della clip. Aggiornare il programma desktop per ricevere la correzione; la nuova estensione aggiorna i download della guida, senza nuovi permessi.

## 1.12.8 — durable queue cancellation, 26 October 2026

- Fixes a cancelled queued clip resuming after a browser restart when its cancellation record encountered a temporary storage failure.
- Recovers cancellation metadata automatically through bounded retries. Pending cancellation blocks the queue; a message explains when to wait before closing the browser. No cancelled export is restarted.
- Preserves known completed results and the real terminal acknowledgement of active native jobs, including completion winning a cancellation race.
- Reproduced in signed 1.12.7 before the fix. Eight targeted Firefox/Chromium cases, 87 JavaScript suites and signed native MP4/restart checks on Windows and Linux pass. No new permissions; helper 1.8.1 is unchanged.
- Italiano: l'annullamento della coda recupera da solo un errore temporaneo di registrazione e resta valido dopo riavvio. Gli esiti nativi restano autorevoli; nessuna reinstallazione helper necessaria.

## 1.12.7 — explicit queue resume without draft autosave, 26 October 2026

- Fixes explicitly queued clips left idle after the selected player/audio returns or the browser restarts when automatic draft saving is off.
- Separates queue context discovery from draft persistence/restoration. Captured ranges and output remain attached to the queued intent; no automatic drafts are written or restored while the option is off.
- Keeps selected media/audio, duration, private-tab, source and session-consent guards. A finished or uncertain interrupted intent is not automatically replayed.
- Verified before the fix in signed 1.12.6, ten targeted Firefox/Chromium cases, 86 JavaScript suites and real MP4 exports after permanent restart on Windows and Linux. Helper 1.8.1 is unchanged.
- Italiano: la coda esplicita riparte anche con Conserva automaticamente il lavoro disattivato, senza salvare o ripristinare bozze. Intervalli e impostazioni catturati restano validi; media/audio diversi, finestre private e durate incompatibili rimangono esclusi.

## 1.12.6 — queue outcome recovery, 26 October 2026

- Fixes a queue item stuck Running after a completed native export when its completion record could not be written. The visible status reflects the real result.
- Retries terminal metadata at 1, 5 and 30 seconds, without replaying the native export. New queue claims wait for a durable outcome. A later successful project operation also commits pending results and resumes the queue.
- Preserves interrupted/no-auto-replay behavior after a worker/browser restart. English and Italian explain pending records. No new permissions or helper update; helper 1.8.1 is unchanged.
- Verified in the older signed XPI before the fix, 12 Firefox/Chromium durability/concurrency/restart cases, 84 JavaScript suites and real signed Firefox MP4/restart checks on Windows and Linux.
- Italiano: recupera automaticamente gli errori temporanei di registrazione della coda senza esportare di nuovo le clip concluse. Stato reale visibile, tentativi limitati e recupero anche da una successiva operazione sul progetto. Dopo riavvio i lavori incerti restano interrotti; helper 1.8.1 invariato.

## 1.12.5 — Firefox update guidance, 26 October 2026

- Replaces the blocked XPI update link with a local two-step guide to Firefox’s add-on manager. The Mozilla catalog is a separate link; the guide also works without a successful optional GitHub check.
- Chrome and Edge receive their own ZIP instead of a Firefox XPI. English and Italian messages distinguish GitHub releases from Mozilla catalog availability.
- Verified signed permanent upgrade from 1.12.2 and restart with settings retained. No new permissions or helper reinstall; helper 1.8.1 is unchanged.
- Italiano: aggiornamento guidato dal gestore Firefox, nessun XPI aperto dal contesto dell’estensione. Catalogo separato, ZIP corretto per Chrome/Edge, guida disponibile anche senza esito GitHub. Impostazioni conservate e helper 1.8.1 invariato.

## 1.12.3 — embedded player reconnects, 26 October 2026

- Fixes a reproduced editor lock after an iframe player reconnects during a native export. The player stays pinned, the active job reclaims its token on the new port, and completed/orphaned locks are released safely after success, cancellation or error.
- Handles a retry made while disconnected and a video removed during saving. Source renewal follows the verified same-document connection; document/player/job guards and audio/range checks remain enforced. Another document cannot receive the old job’s token.
- Verification: 82 JavaScript suites, including 11 added lifecycle scenarios and the existing Save ownership cases; five failures reproduced with the old signed 1.12.2 in Firefox, then five corrected real-port/native MP4 cases with subsequent saves. Firefox 142 checks and signed installation/restart evidence are recorded in the verification metadata. Test-only DevTools listeners target the selected iframe port without changing the extension payload.
- No helper rebuild, new permissions, external requests or session-consent changes. Helper 1.8.1, installers and upstream notices are reused unchanged.

## 1.12.2 — selected media identity, 26 October 2026

- Fixes a reproduced X identity error when one post reuses the same player, blob URL and duration for another video. The previous media’s cached/manual sources are discarded and the interval remains pending confirmation for a different video.
- URL tokens and cover changes for the same media item still renew normally. No extra requests, permissions, session access or helper update. Helper 1.8.1 and its verified Windows/Linux packages are reused unchanged.
- The old signed 1.12.1 package reproduces the error with controlled X/CDN replies and actual Firefox/native exports. The corrected payload passes 82 JavaScript suites, including 87 existing X cases and six new identity/cache/manual/renewal cases. Real Firefox 142/158 checks cover replacement with and without a poster; signature-enforced installation/restart evidence is recorded with the delivered XPI. Fixtures do not establish universal or authenticated live-X compatibility.

## 1.12.1 + helper 1.8.1 — reliable Unicode filenames, 26 October 2026

- Fixes a final-publication failure reproduced on the old Linux helper: emoji, accented and non-Latin titles exceeded the filesystem’s UTF-8 filename limit after range/part metadata was added. Complete names now fit UTF-8 and UTF-16 limits, including collision suffixes. Existing clips are preserved; normal filenames retain their form.
- The extension previews the naming contract advertised by the helper. Read-only capability checks are shared, cached and bounded; an absent or slow helper keeps the editor usable, and stale player requests are rejected.
- Helper 1.8.1 binaries and guided Windows installer verified; no extraction, session-consent, permission or encoding changes. Upstream dependencies/notices are reused because their versions are unchanged.
- Verification: 480 Python tests (6 environment skips), 81 JavaScript suites, 7 exact-binary cases on each OS, signed Firefox MP4/HLS exports after restart on Windows 142/158 and Linux 158, a Unicode-named clip with preview/file equality from the signed 1.12.1 editor, 3 signature/install/restart checks and 4 Chromium MV3 language cases.
- Developer diagnostics now recognize nested localization catalogs and report changed/extra files correctly. Release and installer builds retain version/hash guards.

## 1.12.0 — English and guided helper setup, 26 October 2026

- Full English and Italian interface with automatic browser-language selection and a persistent manual choice. Includes editor, settings, history, projects, diagnostics, consents and crop controls; original user/video data remains unchanged.
- First install opens guided setup. New Windows x64 installer embeds the unchanged helper 1.8.0, prepares a stable per-user folder and browser connection, reuses healthy video tools or verifies a pinned vendor FFmpeg download. No administrator access, Python installation or manual PATH edits. Existing helper 1.8.0 users can keep it.
- Local translation only, no translation service, no new extension permissions. Installer updates are separate from Mozilla extension updates. Linux retains its verified binary archive and system FFmpeg requirement.
- Verification: 80 JavaScript suites, release-package integrity checks, real Firefox language/setup/crop/export checks, clean portable-tool setup with PATH isolated, corrupt archive/payload rejection and actual per-user Firefox registration. Signature/restart verification is recorded with the signed package.

## 1.11.1 — public Mozilla catalog, 26 October 2026

- Approved and publicly downloadable from [Mozilla Add-ons](https://addons.mozilla.org/firefox/addon/video-clipper-in-out-mp4/). Replaces catalog 1.4.7 with the current trim/crop/audio/separate-file features.
- Only `manifest.version` changes from verified direct release 1.11.0. All ten functional files match byte for byte; helper 1.8.0 is unchanged. Existing functional evidence is reused by payload equality. The new signed XPI also passes permanent installation, signature enforcement and restart checks in isolated Firefox 158.0.1.
- Store listing: clearer English/Italian name and summary, benefits-first description, original icon and three actual-extension screenshots with localized captions. Helper requirements and supported platforms are visible before installation.
- The approved 1.11.0 direct/GitHub distribution remains available. Current catalog status supersedes the historical 1.4.7 statements below. Installation guide and privacy version scope are updated.

## 1.11.0 + helper 1.8.0 — current direct distribution (26 October 2026)

The [signed GitHub release](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.11.0) replaces 1.4.6 as the latest public direct download. It includes the verified 1.11.0 extension and separate helper 1.8.0 binaries for Windows and Linux x86_64. Intermediate direct releases developed since 1.4.6 are included in this cumulative update.

- Rectangular crop over the original page player; Original/free, phone 9:16, 16:9, 1:1 and 4:5 without stretching. Export volume 0–200% or remove audio; optional controls and remembered settings. Watermark applied after cropping.
- Multiple parts can become one MP4 or separate numbered files; one source acquisition, ordered intervals, no overwriting existing results.
- Firefox browser-theme palette, native light/dark fallback in other browsers, customizable editor shortcuts and browser commands, one settings page for checking published extension/helper updates.
- Cumulative improvements: local watermark, filename sources/templates/defaults, separate history, output profiles, projects/queue, privacy-preserving diagnostics and bounded recovery of expired sources.
- Fixes cover X post/media identity, direct-source matching, visible/embedded player selection, same-video URL renewal, selection locking during save, queue/cancellation races and private-history persistence. Matching and range validation remain enforced.
- Verified packages: Firefox permanent signed XPI, Chromium unpacked ZIP, Windows helper ZIP, Linux x86_64 helper TAR.GZ and SHA-256 list. No project Python source archive is published.
- Verification: 79 JavaScript suites; 474 Python tests (6 environment skips); 33 signed Firefox functional cases; 9 signature/restart checks; 16 binary checks; 24 Chrome/Edge cases. Controlled media and isolated profiles; not a guarantee for all live sites.

La 1.11.0 è firmata e approvata per distribuzione diretta unlisted/Self. Il catalogo listed resta alla **1.4.7, approvata**, separata e priva delle nuove funzioni. Le vecchie voci sotto descrivono gli stati storici al momento dell'invio, non lo stato corrente. Aggiornare l'XPI non aggiorna l'helper: per tutte le funzioni usa 1.11.0 / 1.8.0. [Installazione](INSTALLAZIONE.md) · [Privacy aggiornata](PRIVACY.md).

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



