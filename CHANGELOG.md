# Changes / Novità

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
