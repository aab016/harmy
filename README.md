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
2. Sviluppare un driver basato su Arduino/ESP32 che piloti direttamente i 5 motori DC (via H-bridge) ed esponga un'interfaccia HTTP per il controllo del braccio.

## Contenuto della cartella `resources/`

Tracciata con **Git LFS** per evitare di appesantire il repository con file binari:

- `quickshot-svi-2000-manual.pdf` — manuale originale del QuickShot SVI-2000 Robotarm
- foto di Harmy (etichette, vano batterie, dettagli meccanici) usate per l'identificazione del modello

## Link utili

- [Manuale utente su ManualsLib](https://www.manualslib.com/manual/3103077/Quickshot-Robotarm-Svi-2000.html)
- [Manuale PDF su The Old Robots](http://www.theoldrobots.com/book38/robotarm.pdf)
- [Scheda storica del modello — The Old Robots](http://www.theoldrobots.com/arms2a.html)
- [Archivio MSX/Spectravideo di Hans Otten (ROM ROGO, cartuccia)](https://hansotten.file-hunter.com/do-it-yourself/spectravideo-rogo/)
- [Spectravideo SVI-2000 — MSX Wiki](https://www.msx.org/wiki/Spectravideo_SVI-2000)
- [Tutorial H-bridge su braccio robotico OWI Edge (stessa architettura a 5 motori DC, riferimento per il driver)](https://www.whiskeytangohotel.com/2012/01/h-bridge-motor-driver-tutorial-w-owi.html)

## Stato

- [x] Identificazione del modello e reperimento del manuale
- [ ] Verifica funzionamento motori/assi
- [ ] Progettazione elettronica del driver (H-bridge + Arduino/ESP32)
- [ ] Interfaccia HTTP di controllo
