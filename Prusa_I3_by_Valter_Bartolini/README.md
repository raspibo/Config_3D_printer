Optimus consigli :-)
====================

Queste impostazioni sono valide per la Prusa i3 di Valter Bartolini (http://optimusprint.org/) e sono pensate per essere usate con il software Cura (https://ultimaker.com/en/products/cura-software)


Note
----

* pare che il sensore di temperatura tenda a segnare molto più della temperatura reale. Se la vostra stampa viene male, riprovate alzando la temperatura di 20 o 30 gradi (forse anche di più, ma meglio procedere per gradi).


Cosa trovate in questo repository
---------------------------------

* nella cartella **cura\_configurazioni**: i file da importare in Cura per PLA e ABS.
* i file **start\_code.txt** e **end\_code.txt** vanno messi nel tab Start/End-GCode di Cura.
* nella cartella **vecchi\_settaggi** troverete le impostazioni che usavamo prima dell'ultimo upgrade della macchina (marzo 2016)


La spiegazione di Valter
========================

Questa macchina ha l'auto leveling, e quindi ogni slicer che si vuole usare, deve necessariamente contenere lo start code che trovate in questa cartella, pena il mal funzionamento della macchina, e il rischio di danneggiarla. Ho inserito anche le configurazioni di Cura per PLA e ABS, quando verranno importate dal menu  File/Open Profile di Cura.

Cura avrà i campi temperature a zero: le temperature vengono gestite dallo start code.


Start Code
----------

    ; For PLA
    ; Sliced at: {day} {date} {time}
    ; Basic settings: Layer height: {layer_height} Walls: {wall_thickness} Fill: {fill_density}
    ; Print time: {print_time}
    ; Filament used: {filament_amount}m {filament_weight}g
    ; Filament cost: {filament_cost}
    ; Sliced at: {day} {date} {time}
    ; Basic settings: Layer height: {layer_height} Walls: {wall_thickness} Fill: {fill_density}
    ; Print time: {print_time}
    ; Filament used: {filament_amount}m {filament_weight}g
    ; Filament cost: {filament_cost}
    ; M565 Z-4.55 Setta offset Z
    ; M220 S* Velocità
    ; M221 S* Flusso
    ; M600 X30 Y160 Z5 E0 L0  Sospensione stampa con LCD
    ; M106 S* Accende ventola
    ; M107 Spegne ventola
    ; M92 X* Y* Z* E* cambia passi ai motori
    ; G92 X* Y* Z* E* Imposta punto zero degli assi
    ; M104 S* setta la temperatura del estrusore
    ; M565 X3 Y4.5 Z-2.37 setta gli ofset
    G21                   ;Misure in Metrico decimale
    G90                   ;Absolute positioning
    M140 S61           ;faccio scaldare il lettino
    M104 S180         ;Comincio a scaldare l'estrusore
    G28                   ;Tutti gli assi a casa
    G29                   ;auto bed leveling deve assolutamente esserci
    M109 T0 S180    ;aspetta che l'estrusore sia in temperatura
    M82                   ; Extruder in absolute mode
    G92 E0              ; Reset extruder position
    G1 F200 E3        ;extrude 3mm of feed stock
    G92 E0              ;zero the extruded length again


se volete variare le temperatura perché usate un materiale che richiede temperature diverse, dovete variarle nello start code, se usate del PLA Layer che va a 210 gradi col lettino a 65, basta che cambiate i valori in:

    M140  S65
    M104 S210
    M109 T0 S210

A questo punto la macchina si comporterà come voi volete, con le temperature giuste, se mette le temperature nelle caselle di Cura, esso vi metterà quei codici in cima a tutto, e aspettera fino a che non sara tutto in temperatura, e dopo verranno ripetute quelle informazioni, perderete molto tempo inutilmente :-)

Buon divertimento :-)

