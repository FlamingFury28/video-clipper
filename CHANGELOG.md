# Changes / Novità

## Helper 1.9.3 — bounded source recovery and Windows setup, 27 October 2026

- When page extraction finds no formats and every observed HLS/DASH manifest returns HTTP 410, retry the same page at most twice. Identity, session scope and DRM checks remain active. If the site keeps the manifests unavailable, the save can still fail and reports HTTP 410.
- The Windows installer retries transient staging-directory move errors for a few seconds; it never overwrites a destination and remains cancellable. The installer is not Authenticode signed.
- Tests include Windows/Linux native compatibility, collection and page recovery, signed Firefox local exports and Chromium integration. Three clean installer preparations and transient, persistent and collision failure tests pass. A short sample from the reported page was saved using helper 1.9.2 with the same logic; the real-page Firefox test was blocked by the site's cookie overlay.
- Italiano: recupero automatico limitato quando i manifest risultano indisponibili con HTTP 410; migliorata l'affidabilita dell'installer Windows. Il successo dipende comunque dal sito.

## Helper 1.9.1 — valid source containers and reliable first Save, 27 October 2026

- Fixes automatic page recovery incorrectly applying encoded-MP4 frame-count requirements to downloaded sources. Valid WebM, Matroska and fragmented MP4 can omit nb_frames. Source video coverage is checked separately; the final encoded MP4 still requires positive frames, valid duration and full video coverage.
- Gives complete MPEG-TS downloads a local MP4 seek index through packet copying. A real fixture reproduced input seeking producing only audio; the indexed path matches decoded-seek pixels and retains strict output checks. No re-encoding is used for indexing, and source/indexed timelines must agree.
- The reported public-page failure and exact interval reproduce VIDEO_OUTPUT_MISSING with helper 1.9.0. Helper 1.9.1 saves that interval on one normal Save with the actual signed/permanent extension 1.13.3 after restart. Output video, audio and duration pass; the user URL, HTML and media are private.
- Nine real-container tests, native compatibility (4), Collection (8) and page-recovery (3) cases per platform pass. MP4/HLS exports pass on Firefox 142/158 Windows and 158 Linux. Three signed first-click container cases pass per platform. Twelve Chromium/native checks pass. Python coverage: 516 cases with six environment skips, including an affected-suite rerun after correcting a fake-media test fixture; unchanged product payload.
- New Windows guided installer and Linux archive contain binary helper 1.9.1 and upstream notices. Installer payload and clean preparation are verified without changing personal registrations. Extension 1.13.3 remains unchanged and Mozilla signed. No new permissions or session access.
- Italiano: corretto il rifiuto di sorgenti valide senza conteggio fotogrammi e il taglio MPEG-TS senza indice. Verificato il caso reale al primo clic. Per questo errore serve aggiornare l’helper alla1.9.1, oltre all’estensione1.13.3 per le correzioni dei player pubblicitari.

## 1.13.3 — explicit advertising markers and embedded players, 27 October 2026

- Fixes three additional failures reproduced with signed 1.13.2: a larger data-ad=true player winning selection, an ad-only child frame blocking main-page recovery, and an advertising marker placed around the frame in its parent document.
- Uses explicit markers and accessible same-origin frame ancestry. Nested frames are bounded to 16 ancestors; inaccessible, cross-origin, opaque and unmarked contexts retain their guards. No size, title or duration guesses.
- Returning from manual to automatic selection applies the same advertisement filter. Adding/removing the parent marker updates eligibility, so a recovered embedded video is not lost permanently. Main-player advertisements remain blocked.
- Ten targeted local DOM/media cases and four native first-click export cases per platform pass. Actual signed/permanent Firefox 158 after restart on Windows and Linux produces the correct film, frames, audio and 1.2-second selection with one normal Save per case. Firefox 142 source exports also pass all four cases. These fixtures are local, not new live-site claims.
- All 102 JavaScript suites, 12 Chromium/native checks, 15 release-tool tests (2 environment skips) and 3 permanent signature/restart checks pass. Only content.js and the manifest version change; helper 1.9.0 and collection evidence are reused after matching unchanged hashes. No new permissions.
- Italiano: corretti altri blocchi del primo salvataggio con player pubblicitari grandi o incorporati e il ritorno alla selezione automatica. Verificati file, fotogrammi e audio; helper invariato.

## 1.13.2 — first-save recovery beside video advertisements, 27 October 2026

- Fixes a reproduced public XVideos case where two sidebar video advertisements made a blob-backed main player appear ambiguous. The first normal Save previously failed before page extraction.
- Recognizes explicit advertising placements and excludes them from automatic selection and page-video uniqueness checks. The fix uses structural advertising markers, not video size, title, duration or media URL guesses. Main-player advertisements remain blocked, including blob-backed players; ordinary multiple-video pages and unmarked neighbors keep their guards.
- Signed permanent 1.13.1 reproduces the failure. The new signed XPI saves the reported public page on one normal Save click; the created MP4 is independently checked for audio and the selected duration. No browser-session sharing or consent changes. The user URL, HTML and clip metadata remain private.
- Six targeted local DOM/media cases, 101 JavaScript suites, 12 Chromium/native cases, 15 release-tool tests (2 environment skips), Firefox 142 native exports and signed/restarted Firefox 158 Windows/Linux collection exports pass. Only content.js and the manifest version change; helper 1.9.0 and its hash-bound tests are reused.
- Italiano: corretto il primo salvataggio bloccato dai player pubblicitari laterali. Il caso reale ora produce la clip con un solo clic; helper invariato, nessun nuovo permesso.

## 1.13.1 — Collection loading and readable file errors, 27 October 2026

- Saved Collection entries now refresh an already-open panel as soon as startup storage loading completes. A paused player no longer leaves restored clips apparently missing. Invalid/unavailable storage is reported without replacing saved data.
- Opening a moved/missing MP4 or an unavailable helper now reports the actual error in Collection. Playback updates preserve the message; a new action or changed collection clears it, and old replies cannot replace the current action.
- Previous signed permanent 1.13.0 reproduces the missing-file feedback failure. Fixed source and signed Firefox Windows/Linux exports verify opaque-player collection, navigation, ordered joined output, identical separate copies, restart persistence and stable missing-file feedback during playback.
- 100 JavaScript suites, 12 Chromium/native cases, 15 release-tool tests (2 environment skips) and bilingual narrow layouts pass. Helper 1.9.0 and content.js are byte-identical; prior 507 Python tests (6 environment skips) and binary evidence are reused by hash. Update only the extension if helper 1.9.0 is installed.
- Italiano: Raccolta visibile dopo un caricamento lento ed errori Apri file leggibili anche durante la riproduzione. Helper invariato, nessun nuovo permesso.

## 1.13.0 — verified page recovery and clips from multiple videos, 27 October 2026

- Fixes the repeated first-click block for a unique visible opaque player. Page recovery starts automatically when appropriate, with a new helper capability gate, unique extraction, known provider/video identity checks and full-duration verification before output publication.
- Missing extractor duration is verified against the downloaded media. Multiple results, incompatible durations, ads, live/DRM media, ambiguous matched configurations and previews remain excluded. Existing X/YouTube identity paths and scoped session choices are retained.
- New Collection saves verified individual MP4s, supports clips from different videos in one tab, ordering, one joined export or separate copies. Hash checks detect changed local files; originals are kept and output names are never overwritten. Storage failure can retry metadata registration without downloading again.
- YouTube page/player IDs must agree before selecting a new video. Full same-site navigation resumes with existing or explicitly granted optional site access; temporary activeTab access expires in Firefox.
- Joined output preserves order, fits the first clip frame without stretching, handles missing audio and avoids cumulative frame-rounding drift. Collection is excluded from private windows.
- Real Firefox 142/158 Windows/Linux exports, signed restart persistence, frame/audio checks, exact separate hashes, 97 JavaScript suites, 507 Python tests (6 environment skips), 12 Chromium/native checks and 12 bilingual narrow-panel layouts verified. Local synthetic media; no universal or authenticated-site success claim.
- Requires extension 1.13.0 and helper 1.9.0. Installer engine and third-party dependencies are unchanged; the helper remains compatible with signed 1.12.13. One isolated installer preparation initially failed with a staging access error; a clean second run of the identical package passed. Cause is not established.
- Italiano: salvataggio diretto dal pulsante con recupero verificato della pagina e nuova Raccolta da video diversi, unita o separata. Aggiornare entrambi i componenti; file originali e consensi conservati.

## 1.12.13 — keep clip parts when the player moves, 26 October 2026

- Fixes a reproduced case where a site moves the same video element into newly created open Shadow DOM components. Candidate cleanup previously ran before discovery, reset the selected parts and could export a default segment instead.
- Follow only already-observed connected videos through reachable open ancestors before cleanup. No whole-document scan, closed-root access or extra permission. Manual selection, busy players and nested open roots keep their identity and ranges; genuinely changed sources still require confirmation.
- Thirteen focused actual-DOM cases pass, including delayed sources, replacement, known/new/nested roots, manual/busy selection, changed sources, closed roots, detached nodes and adoption into another document.
- Old signed 1.12.12 reproduces the wrong export after restart. Firefox 142 source checks and signed permanent/restarted 1.12.13 on Windows/Ubuntu Firefox 158 verify two retained parts and independently check frames, audio, order and duration. Local synthetic media; no authenticated-site claim.
- All 93 JavaScript suites, twelve Chromium/native checks and three signature/install/restart checks pass. Helper 1.8.3 and its Windows/Linux packages are unchanged; existing hash-matched helper/Python evidence is reused.
- Italiano: i siti che riorganizzano il player non azzerano più le parti scelte spostando lo stesso video. Correzione provata con salvataggi reali; nessun nuovo permesso, helper 1.8.3 invariato.

## 1.12.12 + helper 1.8.3 — native Firefox MP4 timing, 26 October 2026

- Fixes a reproduced native Firefox MP4 case where the video track starts after audio. Saving the full range shown by the player could fail with SOURCE_RANGE_INVALID; shorter exports could show earlier frames while audio remained correct.
- A narrowly verified native MP4 timeline is aligned by copying video packets with corrected timestamps. Audio, chosen markers and the existing range tolerance stay unchanged. Manual sources, MSE, other browsers, page extraction, selected audio and ambiguous tracks do not qualify; truly shorter video remains rejected.
- Actual native Firefox duration/decoded frames/audio and independent output checks cover full, partial, joined and separate clips. Windows Firefox 142 and signed permanent/restarted Windows and Ubuntu Firefox 158 pass. No duration getter is overridden and no authenticated-site coverage is claimed.
- Both extension 1.12.12 and helper 1.8.3 are required. The new Windows/Linux binaries retain MP4/HLS compatibility with signed extension 1.12.11. Guided downloads point to the new helper; clean Windows setup and portable video tools are verified.
- All 92 JavaScript suites, 496 Python tests (six environment skips), twelve Chromium/native checks and signature/install/restart checks pass. The private test runner now terminates timed-out owned Windows process trees immediately; this was a test-infrastructure issue, separate from the product correction.
- Italiano: corregge un falso errore di durata e i fotogrammi anticipati negli MP4 nativi Firefox con video e audio che iniziano in momenti diversi. Audio e marcatori restano invariati. Aggiornare sia estensione sia helper; nessun nuovo permesso.

## 1.12.11 — queued clips across multiple tabs, 26 October 2026

- Fixes a queue that could stay waiting when the same video was open in several tabs and the first tab reported an incompatible duration. The old signed 1.12.10 reproduces this in isolated Firefox with real MediaSource duration changes.
- Candidate selection now includes the existing duration and interval checks, so another compatible document can consume the queued intent. Video/audio identity, normal-profile requirements, post-claim checks, captured parts/settings and one export per intent remain enforced.
- Twenty-four focused Firefox/Chromium API cases cover compatible alternatives and rejection of other video/audio, private tabs, invalid players and wrong durations, with automatic draft saving on and off. Twenty audio snapshot/renewal boundary cases also pass.
- All 92 JavaScript suites pass. Native Firefox exports verify frames, audio and joined intervals on Windows 142 and the signed package after restart on Windows/Linux 158. Permanent signature/restart and four Chromium MV3 checks pass. Existing helper evidence is reused unchanged.
- Italiano: una scheda con durata incompatibile non blocca più una clip in coda se un’altra scheda dello stesso video è pronta. Nessun nuovo permesso o aggiornamento helper; resta compatibile la 1.8.2.

## 1.12.10 — preserve ranges during duration recovery, 26 October 2026

- Fixes silent marker truncation when a player temporarily reports a shorter duration. Active and inactive parts retain their original intervals; the old signed XPI reproduces the loss with real MediaSource duration changes in Firefox.
- Saving waits while any part is outside the duration, then recovers automatically when compatible metadata returns. Source revisions invalidate pending snapshots. A real video replacement still requires its existing confirmation.
- Explicit confirmation can adapt intervals to a source that remains shorter. Reset is not offered for an initial interval outside the current duration.
- Eight focused native/Video.js DOM cases and three actual Firefox MediaSource/native MP4 cases per tested browser cover active ranges, inactive parts, recovery and explicit confirmation. Exact signed 1.12.10 passes after restart on Windows and Ubuntu Firefox 158; Firefox 142 passes on the same functional source bytes. Exported frames, audio and intervals are verified.
- All 89 JavaScript suites have passing evidence: 88 in the full run and one successful repeat after a local browser navigation buffer error. Four Chromium MV3 checks and three signature/permanent/restart checks pass. Existing helper evidence is reused by hash; helper 1.8.2 needs no reinstall.
- Italiano: i marcatori non vengono più accorciati silenziosamente se il player cambia durata. Sono protette anche le parti non selezionate; al ritorno della durata corretta il recupero è automatico. Nessun nuovo permesso.

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
