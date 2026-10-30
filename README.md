# Crispy Tileset Studio

Strumento web per preparare **tileset, palette e blocchi di Pokémon FireRed** (GBA) partendo da immagini PNG a colori pieni.

**Apri lo strumento:** https://crispymcangels.github.io/Tileset-Studio/

Gira tutto nel browser: le immagini e i file che carichi non vengono inviati da nessuna parte.

## Cosa fa

- Converte i PNG nei colori del GBA, divide in tile 8×8 ed elimina i doppioni (anche specchiati).
- Distribuisce i tile nelle palette (primario 0–6, secondario 7–12, 15 colori + trasparenza) usandone il meno possibile.
- **Non decide da solo**: quando c'è un compromesso te lo propone con il costo reale e un'anteprima prima/dopo. Per esempio:
  - adattare pochi colori per risparmiare una palette;
  - ridurre un tile con più di 15 colori, oppure dividerlo in due layer;
  - unire colori quasi identici.
- Costruisce i **blocchi 16×16**: per ogni blocco scegli "sopra" o "sotto il giocatore", e puoi riempire le parti trasparenti con un blocco di sfondo.
- Genera uno **script `.hma` per HexManiacAdvance** che scrive tileset, palette, blocchi e attributi nella ROM (in spazio libero, annullabile con Ctrl+Z).

## Due modalità

**Nuovo tileset**: crea un tileset da zero.

**Aggiungi a esistente**: carichi i file esportati da HMA (tileset `.bin`, blocchi `.bin`, palette `.pal`) e la nuova grafica entra nel tileset che hai già:
- usa i colori liberi delle palette esistenti senza toccare quelli usati;
- riusa i tile già presenti;
- riempie il tileset dall'alto: i tile nuovi prendono prima il posto dei tile che nessun blocco usa, poi vanno in coda (se preferisci, li metti tutti in coda);
- piazzi i blocchi nelle caselle libere del blockset.

Lo script controlla che la ROM corrisponda agli export prima di scrivere.

## Note per HexManiacAdvance

- Lo script `.hma` va trascinato sulla **vista esadecimale**. Sulla vista mappa, HMA lo aprirebbe come una ROM.
- I file `.pal` esportati da HMA hanno rosso e blu scambiati. Crispy Tileset Studio li legge correttamente; le `.pal` esportate da Crispy Tileset Studio sono RGB standard (per AdvanceMap e programmi di grafica).
- Il pulsante "Import Blocks" di HMA usa un formato diverso (18 byte per blocco): per HMA usa lo script `.hma`.
- I blocchi nuovi hanno comportamento 0: erba alta, acqua ecc. si impostano in HMA.

Testato con HexManiacAdvance 0.5.6 e Complete Fire Red Upgrade.
