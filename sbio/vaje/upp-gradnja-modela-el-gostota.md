# Gradnja modela strukture z uporabo elektronske gostote

## Namen

Namen delavnice je spoznati osnove ročne gradnje in piljenja modela strukture proteina z uporabo eksperimentalnih podatkov, v konkretnem primeru gre za elektronsko gostoto. V tem primeru gre za elektronsko gostoto, izračunano iz difrakcijskih podatkov (makromolekulska X-žarkovna kristalografija), podobni principi pa veljajo tudi v primeru elektronske difrakcije in krio-elektronske mikroskopije.

Pri delu bomo uporabljali program [Moorhen](https://moorhen.org/), ki predstavlja spletno različico programa [COOT](https://www2.mrc-lmb.cam.ac.uk/personal/pemsley/coot/) (Crystallographic Object-Oriented Toolkit), danes najpogosteje uporabljanega programa za gradnjo, piljenje in validacijo modelov struktur makromolekul {cite:p}`Emsley2010aaa`. Isti program se lahko uporablja tako za gradnjo modelov struktur na osnovi podatkov, pridobljenih z difrakcijo (rentgenska, elektronska difrakcija), kot tudi s krio-elektronsko mikroskopijo.

## Vaša naloga

- Z uporabo Morheen dogradite in izboljšajte model strukture $\beta$-laktamaze KPC-2 z vezanim inhibitorjem avibaktamom, pri tem pa uporabite karto elektronske gostote, izračunano na osnovi difrakcijskih podatkov.
    - 'Dogradite' pomeni, da v trenutnem modelu strukure nekateri deli (aminokislinski ostanki, ligandi, ...) manjkajo in jih morate dodati, 'izboljšajte' pa, da prilagodite koordinate dodatnih ter v modelu že prisotnih atomov/ostankov tako, da bodo kar se da skladni z eksperimentalnimi podatki (elektronska gostota) kot tudi stereokemijskimi parametri (Ramachandranov diagram, dolžine vezi, koti med vezmi, rotameri itd.) in bo končen model imel tudi kemijski smisel.
- Na koncu vaš dograjen in izboljšan model primerjajte z izpiljenim modelom strukture, deponiranim v zbirko PDB.

## Nekaj malega o KPC-2



KPC-2 (*Carbapenem-hydrolyzing beta-lactamase KPC-2*) je $\beta$-laktamaza, ki cepi vez v $\beta$-laktamskem obroču $\beta$-laktamskih antiobiotikih kot so penicilini, cefalosporini in karbapenemi, ter jih s tem inaktivira. $\beta$-laktamaze 