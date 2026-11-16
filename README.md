# squarey

A cozy little drawing page on graph paper. Draw polygons along the grid lines and diagonals, color them with soft pastels, then save them as SVG or export them as PNG.

Un piccolo foglio a quadretti, accogliente, per disegnare. Disegni poligoni lungo i bordi e le diagonali dei quadretti, li colori con tinte pastello e poi li salvi in SVG o li esporti in PNG.

**[English](#english) · [Italiano](#italiano)**

---

## English

### Getting started

squarey is a single static file, `index.html`, with no build step and no dependencies. Open it in a browser, or put it on any static host.

### Drawing

| Tool | Key | How it works |
|---|---|---|
| ✏️ Pencil | `P` | Click a grid corner and move. The line snaps to the 8 allowed directions: horizontal, vertical and 45° diagonals. Each click adds a segment, and the line continues from there. **Double-click, `Esc` or right-click** stops it. You can also drag to draw a single line. |
| 💧 Fill | `B` | Click inside a closed shape to color it with the selected pastel. If the shape isn't closed, a message tells you. |
| 🧽 Eraser | `E` | Click or drag over lines to erase them. Click a colored area to remove its color. |
| ✋ Move | `H` | Drag to move around. You can also hold `Space` or drag with the middle mouse button. |

- **Zoom:** mouse wheel, two-finger pinch, the `+` / `−` keys or the buttons in the bottom-right corner. `0` fits the drawing to the screen.
- **Undo / redo:** `Ctrl+Z` / `Ctrl+Y` (or `Ctrl+Shift+Z`).
- A diagonal splits a shape into separate parts that can each be colored. A diagonal that doesn't reach the outline doesn't split anything.

### Colors

There are ten pastels: peach, apricot, butter, sage, mint, sky, periwinkle, lavender, blush and latte. The rainbow circle opens a custom color picker, and the crossed-out circle removes a fill.

### Story mode 📖

Every line remembers the day it was drawn. The **Story** button (or `S`) recolors the drawing by day:

- each closed area takes the pastel of the day it was closed, meaning the most recent day among the lines around it;
- lines take a darker shade of their own day's color;
- your own fill colors are hidden while story mode is on, and come back when you turn it off.

A **day by day** panel lists the days with their colors. Click a day: everything drawn before it appears at once, then that day's lines are redrawn one by one, in the order you drew them, and each area fills in as it closes. The drawing then stays as it was at the end of that day; click the day again to see everything. ▶ replays the whole drawing from the first line, and the panel highlights the day being replayed. The button next to ▶ sets the speed (×1, ×2, ×4, ×8); it can be changed during a replay and is remembered with the settings. Lines drawn before story mode existed have no date: they're grouped under **Before the story**, in a warm gray.

SVG and PNG exports use the story colors while story mode is on.

### Saving

- **Autosave:** the drawing in progress is saved in the browser (`localStorage`, item `squarey:current drawing`) after every change. When you reopen the page, it comes back as you left it, with the same zoom and position.
- **Drawings** (bookmark button): save the current drawing under a name, and see a list of your saved drawings with previews. Click one to load it, or use × to delete it. **New drawing** starts a blank sheet.
- **Save SVG** (`Ctrl+S`): a vector file. The drawing data is embedded in it, so **Open** can load it back for editing.
- **PNG:** a high-resolution image.
- The **grid** checkbox decides whether the grid is included in exported files.

### Settings ⚙️

- **Language:** Italiano / English. The default follows your browser's language.
- **Background:** white, four grays, paper (the default), cream, linen, blush, sage, cloud, or a custom color. The grid takes a slightly darker shade of the background.
- **Stroke:** pen, pencil (sketchy graphite), brush (tapered) or marker.
- **Grid:** solid, dashed, dotted, dash-dot, dots only, or none.
- **When the polygon closes, stop drawing:** when you return to a point the current line has already passed, drawing stops. On by default.
- **Reset settings:** restores the defaults.

Stroke and grid styles are also applied to SVG and PNG exports. Settings are stored in the `squarey_settings` cookie for one year, with a copy in `localStorage`, so they're kept even when the page is opened straight from disk.

### Keyboard shortcuts

| Key | Action |
|---|---|
| `P` / `D` | Pencil |
| `B` / `F` | Fill |
| `E` | Eraser |
| `H` | Move |
| `S` | Story mode on / off |
| `Space` (hold) | Temporary move |
| `Esc` | Stop the line / close the panel |
| `+` `−` `0` | Zoom in, zoom out, fit drawing |
| `Ctrl+Z` / `Ctrl+Y` | Undo / redo |
| `Ctrl+S` | Save SVG |

### How it works (for the curious)

- Lines are stored as **unit segments** between neighboring grid corners, including diagonals.
- Each grid cell is divided into **4 triangles** by its two diagonals. Fill is a flood fill over these triangles, and drawn lines act as walls. If the fill reaches beyond the drawing's bounds, the area isn't closed.
- Each line's day is stored with the drawing (`days`: day → list of segments), in local time.
- Drawing order needs no extra data: segments are kept and saved in the order they were drawn, so a segment's number is its position in `edges`.
- In the SVG, the drawing data is in `<metadata id="squarey-data">` as JSON.

---

## Italiano

### Per iniziare

squarey è un unico file statico, `index.html`, senza build e senza dipendenze. Aprilo nel browser o mettilo su un qualsiasi hosting statico.

### Disegnare

| Strumento | Tasto | Come funziona |
|---|---|---|
| ✏️ Matita | `P` | Clicca un incrocio e muoviti. La linea segue le 8 direzioni consentite: orizzontale, verticale e diagonali a 45°. Ogni clic aggiunge un tratto e la linea riparte da lì. **Doppio clic, `Esc` o tasto destro** per staccare. Puoi anche trascinare per tracciare una linea singola. |
| 💧 Colora | `B` | Clicca dentro una forma chiusa per colorarla con il pastello scelto. Se la forma non è chiusa, compare un avviso. |
| 🧽 Gomma | `E` | Clicca o trascina sulle linee per cancellarle. Clicca su una zona colorata per togliere il colore. |
| ✋ Sposta | `H` | Trascina per spostarti. Puoi anche tenere premuto `Spazio` o trascinare con il tasto centrale del mouse. |

- **Zoom:** rotella del mouse, pizzico con due dita, tasti `+` / `−` o i pulsanti in basso a destra. `0` inquadra il disegno.
- **Annulla / ripeti:** `Ctrl+Z` / `Ctrl+Y` (oppure `Ctrl+Shift+Z`).
- Una diagonale divide una forma in parti separate, che puoi colorare ognuna a sé. Una diagonale che non arriva al contorno non divide niente.

### Colori

Ci sono dieci pastelli: pesca, albicocca, burro, salvia, menta, cielo, pervinca, lavanda, rosa cipria e latte e caffè. Il cerchio arcobaleno apre un selettore di colore libero e il cerchio barrato toglie il colore.

### Modalità storia 📖

Ogni linea si ricorda il giorno in cui l'hai disegnata. Il pulsante **Storia** (o `S`) ricolora il disegno per giorno:

- ogni zona chiusa prende il pastello del giorno in cui si è chiusa, cioè il giorno più recente tra le linee che la circondano;
- le linee prendono una tonalità più scura del colore del loro giorno;
- i colori che hai dato tu sono nascosti finché la modalità storia è attiva, e tornano quando la spegni.

Il pannello **giorno per giorno** elenca i giorni con i loro colori. Clicca un giorno: tutto quello che c'era prima compare subito, poi le linee di quel giorno vengono ridisegnate una alla volta, nell'ordine in cui le hai tracciate, e ogni zona si colora quando si chiude. Alla fine il disegno resta com'era a fine giornata; clicca di nuovo il giorno per vedere tutto. ▶ riproduce tutto il disegno dalla prima linea, e il pannello evidenzia il giorno in riproduzione. Il pulsante accanto a ▶ sceglie la velocità (×1, ×2, ×4, ×8); si può cambiare anche durante la riproduzione e viene ricordata con le impostazioni. Le linee disegnate prima che esistesse la modalità storia non hanno una data: sono raccolte in **Prima della storia**, in un grigio caldo.

Con la modalità storia attiva, anche l'esportazione in SVG e PNG usa i colori della storia.

### Salvare

- **Salvataggio automatico:** il disegno in corso è salvato nel browser (`localStorage`, voce `squarey:current drawing`) a ogni modifica. Quando riapri la pagina lo ritrovi com'era, con lo stesso zoom e la stessa posizione.
- **Disegni** (pulsante segnalibro): salva il disegno con un nome e vedi l'elenco dei disegni salvati con un'anteprima. Clicca un disegno per caricarlo, oppure × per eliminarlo. **Nuovo disegno** apre un foglio vuoto.
- **Salva SVG** (`Ctrl+S`): un file vettoriale. Dentro ci sono i dati del disegno, così con **Apri** puoi ricaricarlo e continuare a modificarlo.
- **PNG:** un'immagine ad alta risoluzione.
- La casella **quadretti** decide se includere la griglia nei file esportati.

### Impostazioni ⚙️

- **Lingua:** Italiano / English. Quella predefinita segue la lingua del browser.
- **Sfondo:** bianco, quattro grigi, carta (predefinito), crema, lino, cipria, salvia, nuvola o un colore a scelta. I quadretti prendono una tonalità un po' più scura dello sfondo.
- **Tratto:** penna, matita (grafite un po' tremolante), pennello (assottigliato alle estremità) o pennarello.
- **Quadretti:** continua, tratteggiata, puntinata, tratto-punto, solo punti o nessuna.
- **Quando il poligono si chiude, smetti di disegnare:** quando torni su un punto già toccato dalla linea in corso, il disegno si stacca. Attiva di default.
- **Ripristina impostazioni:** torna alle impostazioni iniziali.

Tratto e quadretti valgono anche per l'esportazione in SVG e PNG. Le impostazioni sono salvate nel cookie `squarey_settings` per un anno, con una copia in `localStorage`, così restano anche quando la pagina è aperta direttamente dal disco.

### Scorciatoie da tastiera

| Tasto | Azione |
|---|---|
| `P` / `D` | Matita |
| `B` / `F` | Colora |
| `E` | Gomma |
| `H` | Sposta |
| `S` | Attiva / disattiva la modalità storia |
| `Spazio` (tenuto premuto) | Sposta temporaneo |
| `Esc` | Stacca la linea / chiude il pannello |
| `+` `−` `0` | Ingrandisci, riduci, inquadra |
| `Ctrl+Z` / `Ctrl+Y` | Annulla / ripeti |
| `Ctrl+S` | Salva SVG |

### Come funziona (per i curiosi)

- Le linee sono salvate come **segmenti unitari** tra incroci vicini, diagonali comprese.
- Ogni quadretto è diviso in **4 triangoli** dalle sue due diagonali. Colorare è un riempimento a macchia su questi triangoli, e le linee disegnate fanno da muro. Se il riempimento esce dai bordi del disegno, la zona non è chiusa.
- Il giorno di ogni linea è salvato insieme al disegno (`days`: giorno → elenco di segmenti), in ora locale.
- L'ordine di disegno non richiede dati in più: i segmenti sono tenuti e salvati nell'ordine in cui li hai disegnati, quindi il numero di un segmento è la sua posizione in `edges`.
- Nell'SVG i dati del disegno si trovano in `<metadata id="squarey-data">`, in formato JSON.
