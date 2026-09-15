# Harmy

Progetto personale per rimettere in funzione e pilotare via HTTP un vecchio braccio robotico da laboratorio, soprannominato "Harmy".

## Il robot

Dalle etichette presenti sull'unità, si tratta di un **QuickShot / Spectravideo SVI-2000 Robotarm**, prodotto nel 1985 da Spectravideo International (azienda cessata nel 1988) come braccio robotico didattico per computer MSX e Commodore 64/128.

Caratteristiche principali:

- 5 assi motorizzati (base, spalla, gomito, polso, pinza), azionati da **5 motori DC** tramite ingranaggi in plastica
- Nessun sensore di posizione/encoder: controllo ad anello aperto, puramente temporizzato
- Luce ("spotlight") sulla pinza
- Alimentazione a 4 batterie formato D (UM-1)
- Controllo originale tramite cartuccia MSX (linguaggio **ROGO**, simile a LOGO) oppure due joystick in stile Atari collegati a due porte DE-9

Il produttore non esiste più e non ha un sito web attivo: le risorse disponibili sono archivi storici e community di appassionati.

## Obiettivo del progetto

1. Verificare che Harmy funzioni ancora meccanicamente ed elettricamente, bypassando i controlli originali (joystick/cartuccia MSX) ormai introvabili.
2. Sviluppare un driver basato su Arduino MKR WiFi 1010 (kit Arduino Education Explore IoT Kit REV2) che piloti direttamente i 5 motori DC (via driver H-bridge TB6612FNG) ed esponga un'interfaccia HTTP per il controllo del braccio.

L'alimentazione dei motori riutilizza il vano batterie originale di Harmy (4×D, 6V): non serve un alimentatore separato, si sostituisce solo l'elettronica di comando (joystick/cartuccia MSX → H-bridge pilotati dal MKR).

## Contenuto della cartella `resources/`

I file binari (PDF, immagini) sono tracciati con **Git LFS** per evitare di appesantire il repository:

- `quickshot-svi-2000-manual.pdf` — manuale originale del QuickShot SVI-2000 Robotarm
- `schema-elettrico-driver-arduino.svg` — schema di collegamento vano batterie → driver TB6612FNG → motori, e MKR WiFi 1010 → driver
- foto di Harmy (etichette, vano batterie, dettagli meccanici) usate per l'identificazione del modello

## Documentazione del percorso

- [Presentazione "Harmy"](https://docs.google.com/presentation/d/15pbOaTJ8F_nnkq4sL5I_aqkSrkwFfh87PMP17H8uyp0/edit) — diario dell'evoluzione del progetto, per raccontare il procedimento agli studenti
- [Primo grado di libertà ripristinato (YouTube Shorts)](https://youtube.com/shorts/lzMFdCiij74)

## Link utili

- [Manuale utente su ManualsLib](https://www.manualslib.com/manual/3103077/Quickshot-Robotarm-Svi-2000.html)
- [Manuale PDF su The Old Robots](http://www.theoldrobots.com/book38/robotarm.pdf)
- [Scheda storica del modello — The Old Robots](http://www.theoldrobots.com/arms2a.html)
- [Archivio MSX/Spectravideo di Hans Otten (ROM ROGO, cartuccia)](https://hansotten.file-hunter.com/do-it-yourself/spectravideo-rogo/)
- [Spectravideo SVI-2000 — MSX Wiki](https://www.msx.org/wiki/Spectravideo_SVI-2000)
- [Tutorial H-bridge su braccio robotico OWI Edge (stessa architettura a 5 motori DC, riferimento per il driver)](https://www.whiskeytangohotel.com/2012/01/h-bridge-motor-driver-tutorial-w-owi.html)

## Stato

- [x] Identificazione del modello e reperimento del manuale
- [x] Progettazione elettronica del driver (H-bridge + Arduino MKR WiFi 1010) — vedi `resources/schema-elettrico-driver-arduino.svg`
- [~] Verifica funzionamento motori/assi — primo grado di libertà ripristinato (vedi video sopra), restano 4 assi
- [ ] Realizzazione fisica del cablaggio completo
- [ ] Interfaccia HTTP di controllo
