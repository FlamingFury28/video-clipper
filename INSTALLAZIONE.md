# Video Clipper 1.2.0 — installazione Windows

Video Clipper permette di scegliere un player HTML5, segnare IN e OUT, regolare i marcatori di 0,1 o 1 secondo, provare l'intervallo e salvarlo come MP4 locale. Al termine dell'anteprima ripristina posizione e stato precedenti. Il pannello si può spostare e ridimensionare ai lati della pagina, sul video oppure usare nella sidebar Firefox. Rileva anche video dinamici e componenti con shadow DOM aperto.

**Requisiti:** Windows 11 x64, Firefox 142+, FFmpeg e ffprobe nel PATH con encoder libx264/AAC. Interfaccia attuale in italiano. Python e le dipendenze dell'helper sono già inclusi; non occorre installare Python separatamente.

1. Installa FFmpeg e ffprobe partendo dalla [pagina ufficiale FFmpeg](https://ffmpeg.org/download.html#build-windows) e aggiungi la cartella che contiene entrambi al PATH. FFmpeg non è incluso. Riapri Firefox dopo aver modificato il PATH.
2. Scarica [VideoClipper-1.2.0-Windows.zip](https://github.com/FlamingFury28/video-clipper/releases/tag/v1.2.0) ed estrai **tutto** in una cartella stabile sotto il tuo utente. Non eseguire dall'archivio ZIP.
3. Avvia **Installa helper.cmd**. Verifica l'helper e registra il collegamento nativo per l'utente Windows corrente, conservando una copia del manifest precedente se presente. Non serve avviarlo come amministratore.
4. In Firefox apri **about:addons**, menu ingranaggio → **Installa componente aggiuntivo da file**, e scegli **VideoClipper-1.2.0-signed.xpi**. Nei dettagli deve comparire **Versione 1.2.0**.
5. Apri **Preferenze** dell'estensione e premi **Verifica collegamento**. Scegli la cartella di destinazione e ricarica le pagine video già aperte.

Conserva la cartella dopo l'installazione, compresa `_internal` accanto all'eseguibile. Se la sposti, riesegui `Installa helper.cmd` dal nuovo percorso. L'XPI è firmato da Mozilla; l'eseguibile helper non ha una firma Authenticode separata e Windows può mostrare un produttore sconosciuto. Non disattivare le protezioni di Windows per installarlo.

## Uso

Apri un video e attiva Video Clipper dalla barra Firefox. **Cambia video** sceglie il player. Imposta IN e OUT, premi **Anteprima**, poi **Salva clip**. **Posizione pannello** cambia la disposizione; le maniglie regolano le dimensioni. Puoi annullare il salvataggio o aprire file/cartella e copiare il percorso al termine. La cronologia conserva al massimo 30 esiti per 30 giorni: svuotarla non elimina i video.

## Limiti e aggiornamenti

La sola estensione non esporta MP4: serve l'helper. I siti devono rendere accessibili i media ed essere compatibili con yt-dlp. Sono supportate sorgenti MP4 dirette e HLS quando scaricabili; DRM e shadow root chiuse non sono supportati. Le trasformazioni CSS/SVG degli iframe possono alterare l'allineamento. L'helper non è supportato su macOS, Linux o Android. Le regolazioni di 0,1 secondi non garantiscono un risultato identico al fotogramma su tutte le sorgenti; Originale indica il limite di risoluzione, non un'esportazione senza perdita.

Per aggiornare una vecchia copia installa il nuovo XPI firmato e registra l'helper dal nuovo pacchetto. La distribuzione autonoma 1.2.0 non configura un URL di aggiornamento automatico: il selettore di Firefox non legge la cartella del progetto.

Se compare **No such native application**, riesegui `Installa helper.cmd` con lo stesso utente di Firefox e riapri il browser. Per dipendenze mancanti verifica il PATH e ripeti **Verifica collegamento**. Per segnalare un errore usa [Issues](https://github.com/FlamingFury28/video-clipper/issues), senza inviare cookie, token o URL privati.

Consulta [privacy](PRIVACY.md), [novità](CHANGELOG.md) e [licenze delle dipendenze](THIRD-PARTY-NOTICES.md). I sorgenti del progetto restano privati; gli archivi sorgente inclusi riguardano esclusivamente componenti di terze parti.
